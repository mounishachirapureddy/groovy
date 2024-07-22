**Loops**
for 
for in
while
**keywords**
upto
times
step
=======================
**Exception Handling**
try-catch
try-catch-finally
try-finally
{---all blocks should be written continously ---}
========================
**STRING**
single quoted '....'--->variables are printed as it is even it is defined (variables are not disaplaced with the original value){dont have multiline}
double quoted "...." --->{dont have multiline}       
triple single quoted '''....'''-->{have multiline}              
triple double quoted """....""" -->-->{have multiline}
slashy  /..../ -->{have multiline}              
dollar slashy $/..../$-->{have multiline}               
**REFERENCE**-https://groovy-lang.org/syntax.html#all-strings
FUNCTIONS-----
length()
concat(name)
name[1]-->index position(if negative last position is -1)
name.indexOf('g')
name[0..2]-->0 and 2 both are considered
name[0,2,4]
name.substring(2)--> from 2nd index tpo last index
name.subSequence(0,2)
name.split(" ")
name- ("groovy")--->it will deduct the word groovy from name string 
name.replace("one","two")
name.toLowerCase
name.toUpperCase
name.toList--->every character is a seperated including space by comma
name *3 -->print threee times
name.equals("ki")
name.equalsIgnoreCase("ki")-->to ignore case sensitive issues
to print the word inside string with double quotes--->"my name is \"hi\"" or /my name is "hi"/
=====================================
**METHODS**
to call methods--- direct call or creating an object to call method
 eg: class method2{
          method2 myfunc= new method2();
          myfunc.method1();
          }
      def method1(){
       println 'hi'
       }
       ------------------
       method1()--->we can call this
==================================================
**closures**
def myclosure={ println "hi"}
myclosure.call()
--------
def myclosure={ name -> println "hi $name"}
myclosure.call(raghav)----------->{to pass name as parameter we give ->}
o/p---->hi raghav
------
string my="hi"
def myclosure={ name -> println "$my $name"}[------this calling variable froom outsidee cannot be done in functions---------]
myclosure.call(raghav)
o/p---->hi raghav
----------
string my="hi"
def myclosure={ name -> println "$my $name"}
def myfunc(clos){
clos.call(raghav)
}
myfunc(myclosure)
o/p---->hi raghav
---------------
def myclosure={ a,b -> return (a+b)}
def b =myclosure.call(10,20)----------->{to pass name as parameter we give ->}
println b
o/p=30
---------
def list1=["ad","ab"]
println list1.each{it}
o/p--> [ad,ab]
-----
def mymap1=["ad":"1","ab":"2"]
println list1.each{it}
o/p--> [ad:1,ab:2]
-----
def list1=[1,2,3,4,5]
list1.find{item->item==3}-->to check the elements present in the list
list1.findAll{item->item>3}-->to print all the elements present in the list
list1.any{item->item>3}-->prints true/false(whether any element is greater than 3 or not)
list1.every{item->item>3}-->prints true/false(whether every element present is greater than 3)
==========================================
**LISTS**
LIST
structure to store collection of data items
syntax :  [obj1, obj2, obj3, ...]
[1,2,3,4]
["Groovy", "Raghav"]
[1,2,3,['A','B'],4]
[1,2,"Groovy", 2.2]
[] - empty list
def list1=["addd","add",["ck","ak"],"adc"]
lsit1[1]
list1.get(1)
list1[2][1]---->o/p--ak
list1.get(2).get(1)---->o/p--ak
lsit1[0..2]
lsit1[2..0]-->to reverse the list
list1.contains(2)-->true/false
list1.size()
list1.add(10) or list1<<10 or list1=list1+[30,40]
list1.add(2,10)--->add num 10 at index 2
list1.remove(2)--->to remove num at index 2
list1=list1-[30,40]
list1=list1.minus([30,40])
list1.pop()
list1.removeLast()
list1.intersect([1,2])
list1=list1.reverse()
list1.isEmpty()
list1.clear()
========================================
**MAPS**
key-value pair
unordered collection
[key : value]
['name' : 'Raghav']
[:] = empty map
eg: def employee=['name' : 'Raghav','age' : 40]
    println employee.name or 
    println employee['name']  or
    println employee.get('name') or
    println employee.getAt('name')
    
     println employee.size()
     employee.put('city','paris')
     employee.containsKey('city')
     employee.containsValue('paris')
     def employee2=employee.clone() 

     employee.each {key,value ->
        println "$key:$value"
        }
============================================
RANGES
creates a list of sequential values
denoted by first and last value of the sequence

1..10
'a'..'z'
10..1
2 types -  inclusive --->eg 1..10 & exclusive---->1..<10

print range
print range.size()
print range.getFrom()---->starting value
print range.getTo()----->ending value
assert range.from==1
assert range.to--10
range.get(3) or range[3]
range.contains(6)--->prints true or false
def range2=range.subList(first index,last index)
range.each{i ->println  "value=$i"}
=================================================================
**INPUT AND OUTPUT**
INPUT-
def name = System.console().readLine()
println "hello $name"
println "hello" +name

def num = System.console().readLine().toInteger()
printf"%s |%d \n", ["raghav",10]
%-10s===>space after the word
%10s===>space before the word
=============================================================
**HOW TO READ FILES IN GROOVY**
String filepath ="";
File myFile= new File(filepath)
println myFile.text


def list=myFile.collect{it}
println"list:$list"---> to print content in the list form
o/p-->list:[line1 ,line 2]

def array=myFile as String[]
println"array:$array"---> to print content in the array form
o/p-->array:[line1 ,line 2]

def lines=myFile.readLines()
println"lines:$lines"--->read file in to list of strings
o/p-->lines:[line1 ,line 2]

myFile.eachLine{ line ->
println"line:$line"
}
o/p---> line:line1
        line:line2


myFile.eachLine{ line, lineNo ->
println"$lineNo:$line"
}
o/p---> 1:line1
        2:line2

def lineList=[]
def lineNoRange = 2..4
myFile.eachLine{ line, lineNo ->
if (lineNoRange.contains(lineNo))
{
lineList.add(line)
}
}
println"lineList:$lineList"
o/p---> 1:line1
        2:line2


def line
myFile.withReader { reader ->
   while(line = reader.readLine()!=null){
   println ("line:$line")
   }
   }

// reading with new reader
def outputFile = "data2.txt"
def reader=myFile.newReader()
new File(outputFile).append(reader)
reader.close()

//when working with binary files and read content as bytes
byte[] contents=myFile.bytes
println contents
