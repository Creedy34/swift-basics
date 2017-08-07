# swift-basics
just my practices in Xcode playground

The following is what I put in a playground but I could not push to github



//: Playground - noun: a place where people can play

import UIKit

//variables video

var message = "Hello, playground"   //type inference


//operators
//unary, binary, and ternary
    //those are the number of targets

var amICool = true  //binary

amICool = !amICool  //unary

//only one ternary in swift
var feelGoodAboutMyself = true
feelGoodAboutMyself = amICool ?true : false         //is a binary and ternary operator
//if amICool is true then it feelGoodAboutMyself is true, else false

var bankAccountBalance = 100
var cashRegisterMessage = (bankAccountBalance >= 150) ? "You just bought the item" : "You are broke af"

//strings video

var str: String = "practice"        //explicitly declared type
var first = "Jim"
var last = "Office"
var full = first + " " + last           //string concatenation
var fullName = "\(first) \(last) is not his real name"  //string interpolation
fullName.append(" III")
var bookTitle = "revenge of the crab cakes"
bookTitle = bookTitle.capitalized
var chatroomAnnoyingCapsGuy = "PLEASE HELP ME NOW"
chatroomAnnoyingCapsGuy.lowercased()

var sentence = "What the fetch?"
if sentence.contains("fetch") || sentence.contains("heck"){
    sentence.replacingOccurrences(of: "fetch", with: "tuna")
    sentence.replacingOccurrences(of: "heck", with: "playa")
}

//numbers video

var age = 30    //Int - inferred
var weight: Int = 200 //int - explicit
//you typically want to do an inferred type
var milesRan = 56.45 //double is default
//floating point is another type of decimal possibility but it auto chooses double always

//arithmatic operators
// + - / * %

//functions video

//shape #1
var length = 5
var width = 10
var area = length * width
var length2 = 6
var width2 = 12
var area2 = length2 * width2
//alternative
func Area(length: Int, width: Int) -> Int {
    let area = length * width   //constant
    return area
}
let newarea = Area(length: 5, width: 4)
func Area2(length: Int, width: Int, area: inout Int) {        // the inout changes that value so you dont have to return it --- kinda a pointer
    area = length * width   //constant
    return
}
var testarea = 0
Area2(length: 2, width: 2, area: &testarea)
print(testarea)

//boolean and conditional logic video

//bool is the new version of boolean
//just dont use boolean

/*
if 1 == 2 {
    print("Should not see this")
}
*/
 
//==
//!=
//<
//>
//<=
//<=

/*
 if(){
 } else if{
 } else{
 }
 */

//constants and logicl operators video

let allowedEntry = false    //constant
if !allowedEntry{
    print("ACCESS DENIED")
}

//array data sructure video

var employeeSalaries: [Any] = [4500, "1500"]   //allowed
//following not allowed if declared
//var employeeSalaries: [Int] = [4500, "1500"]
print(employeeSalaries.count)
employeeSalaries.append(3900)
print(employeeSalaries.count)
employeeSalaries.remove(at: 1)  //gets rid of #2 since it starts at 0
print(employeeSalaries.count)

var students = [String]()       //innitializes an empty array
students.append("Jon")
students.append("Jose")
students.remove(at: 1)

//swift loops video
var empolyee1Salary = 100.0
var empolyee2Salary = 100
var empolyee3Salary = 100
var empolyee4Salary = 100

var salaries = [100.0, 200.0, 300.0, 400.0]

var x = 0
//wont use this a lot
repeat {
    salaries[x] += (salaries[x] * 0.10)
    print (salaries[x])
    x+=1
} while (x < salaries.count)            //this will always run at least once

//will use this more
for i in 0..<salaries.count {           //for in loop
    salaries[i] += (salaries[i] * 0.10)     //includes 0     excludes salaries.count
    print(salaries[i])
}

for x in 1...5 {            //inclusive       ..< is exclusive
    print(x)
}

//another type of loop
//called a for each loop even though syntax is still for in
for salary in salaries {                //auto grabs item at the index and gets every item in salaries
    print("Salary: \(salary)")
}

//data dictionary structure video
//hash tables
/*
 hash tables are data tables used to store information
 they have a key and then a value with a record
 the key can be your name and the value can be your phone number
 hash functions look at a certain key then evalueate it to get the index number for where the value is stored
    should always get the exact same value when you enter the same key
 a collision occurs if a hash function gets the same index value for different keys
 to avoid this you can create a linked list off of these indexes 
 has functions basically tell you where to look at so you dont have to go through the entire list to find it
 if you do it right you shouldnt have too many things in each index
 there are other options to do this but this is just one way to take care of collisions
 */

//hash tables are called dictionaries in swift
/*
 three different value storage systems
 1. Arrays - linear and can have multiple indexes with the smae value. ordered
 2. Sets - has items that should only have one type of value. not ordered but unique
 3. Dictionaries - has keys and values where the key is of a certain type and the values are related to those keys
                 - keys must always be unique
                 - values dont have to be
 */

var namesOfIntegers = [Int: String]()       //int is the type of the key and string is the value
namesOfIntegers[3] = "three"        //3 is the name of the key and "three" is the value
namesOfIntegers[44] = "forty four"

//the following clears out all of the keys and values in a dictionary
namesOfIntegers = [:]

var airports: [String: String] = ["YYZ": "Toronto Pearso", "LAX": "Los Angeles International"]      //can also do type inference like shown below
var airports2 = ["YYZ": "Toronto Pearso", "LAX": "Los Angeles International"]

print("The airports dictionary has \(airports.count) items")
if airports.isEmpty {
    print("The airports dictionary is empty!")
}
airports["LHR"] = "London"
airports["LHR"] = "London Heathrow"     //this is how you replace the old one
airports["DEV"] = "Devslopes International"
airports["DEV"] = nil       //removes the item
//this is good for keys

for (airportCode, airportName) in airports {        //the (airportCode, airportName) is a tuple (data construct that has one or more elements in it)
    print("\(airportCode): \(airportName)")     //airportCode is key, airportName is value
}

for key in airports.keys {
    print("Key: \(key)")
}

for val in airports.values {
    print("Value: \(val)")
}

//object oriented programming video

//classes are like structs in C
class Vehicle {
    var tires = 4
    var headlights = 2
    var horsepower = 468
    var model = ""
    func drive() {
        //accelerate the vehicle
    }
    func brake() {
        //brakes the vehicle
    }
}

let bmw = Vehicle()     //instantiating an instance of the Vehicle class    - called an object after it is instantiated
bmw.model = "328i"
bmw.brake()
//objects are passed by reference not value
//cannot copy an object
//Ex of pass by reference
func passByReference(vehicle: Vehicle) {
    vehicle.model = "Cheese"        //changes whatever model is put in the location of Vehicle
}

passByReference(vehicle: bmw)      //this changed the vehicle model of bmw to Cheese
print(bmw.model)


func passByValue(age: Int) {
    let newAge = age                //this is pass by value, the input age is a constant so you can never change that but you can do what is shown below by making another constant or variable equal to it
}

//pass by reference allows you to manipulate the actual information passed in
//  this always occurs when you pass in an object

//pass by value just sends a copy of the variable which in turn becomes a constant in the new function
//  it will not manipulate the original variable or constant


//video on inheritance and OOP

//kinda similar to a struct in C
class newVehicle {
    var tires = 4
    var make: String?
    var model: String?
    var currentSpeed: Double = 0
    init() {
        print("I am the parent")
    }
    func drive(speedIncrease: Double) {
        currentSpeed += (speedIncrease * 2)
    }
    func brake() {
        
    }
}

class SportsCar: newVehicle {              //this inherits from the Vehicle type/class
    override init() {
        super.init()
        print("I am the child")
        model = "3 series"
        make = "BMW"
    }
    override func drive(speedIncrease: Double) {
        currentSpeed += speedIncrease * 3
    }
}

let car = SportsCar()

//polymorphism and OOP video

//polymorphism - the condition of occuring in several different forms
//             - common question on interviews
//             - allows the expression of some sort of contract, with potentiallly many types implementing that contract (whether through class inheritance or not) in different ways, each according to their own purpose. code not using that contract should not have to care about which implementation is involved, only that the contract will be obeyed

class Shape {
    var area: Double?       //makes the area optional with the ?
    func calculateArea(valA: Double, valB: Double) {
        
    }
}

class Triangle: Shape {
    override func calculateArea(valA: Double, valB: Double) {
        area =  (valA * valB) / 2
    }
}

class Rectangle: Shape {
    override func calculateArea(valA: Double, valB: Double) {
        area = valA * valB
    }
}

//this is polymorphism since they both follow the "contract" (function) but the logic inside is actually different
//still uses the same parent class









