package code

import cats.data.Kleisli
import cats.implicits._

case class Person(name: String, age: Int) //, address: Address)

case class Address(house: Int, street: String)

object Main extends App {
  type Error      = String
  type Result[A]  = Either[Error, A]
  type Request    = Map[String, String]

  def readName(req: Request): Either[Error, String] =
    req.get("name")
      .toRight("Name not found")

  def readAge(req: Request): Either[Error, Int] =
    req.get("age")
      .toRight("Age not found")
      .flatMap { str =>
        try {
          Right(str.toInt)
        } catch {
          case exn: NumberFormatException =>
            Left("Age is not a number")
        }
      }
      .flatMap { num =>
        if(num > 0) {
          Right(num)
        } else {
          Left("Age is negative")
        }
      }

  def readPerson(req: Request): Either[Error, Person] =
    for {
      name <- readName(req)
      age  <- readAge(req)
    } yield Person(name, age)

  type Rule[A, B] = Kleisli[Result, A, B]

  def getField(name: String): Rule[Request, String] =
    Kleisli(_.get(name).toRight("Field not found: " + name))

  def parseInt: Rule[String, Int] =
    Kleisli(str => Either.catchNonFatal(str.toInt).leftMap(_ => "Not an integer"))

  def gte(min: Int): Rule

  val readName2 = Kleisli(readName)
  val readAge2 = Kleisli(readAge)

  val readPerson2 =
    (readName2, readAge2).mapN(Person.apply)
}