
# Appendix-12
# Secton-12 Introduction to functional programming.

# 258 step=0 Intro to functional programming.
![Alt text](image-131.png)
==
# 259 Step-1 Let's start
![Alt text](image-132.png)
![Alt text](image-133.png)
![Alt text](image-134.png)
![Alt text](image-135.png)

![Alt text](image-136.png)
```java
package programming;

import java.util.List;

public class FP01Structured {
	
	public static void main(String args[]) {
		
		List<Integer> numbers = List.of(12,9,13,4,6,2,4,12,15);
		printAllNumbersInListStructured(numbers);
	}

	private static void printAllNumbersInListStructured(List<Integer> numbers) {
		
		//In Traditional approach.
		//need to think about how to loop the numbers 
		
		for(int number : numbers) {
			System.out.println(number);
		}
	}
}
```
![Alt text](image-137.png)
==
# 260 step-2 via Functional programming appraoach.
![Alt text](image-138.png)
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		printAllNumbersInListFunctional(numbers);
	}

	//2
	//custom method which print the number.
	private static void print(int number) {

		System.out.println(number);
	}

	private static void printAllNumbersInListFunctional(List<Integer> numbers) {

		// In functional approach
		// focus on what to do?
		// Convert this list of number into stream of numbers.
		// [12,9,13,4,6,2,4,12,15] - this is the list of number
		// i need to convert it into sequence so that
		// first i get 12
		// then 9
		// then 13 so on so forth
		// So how to convert list into Stream.
		// via stream() method == Returns a sequential Stream with this collection as
		// its source.
		// once have stream of number what to do with each one of them.

		// go to 2nd step
		// for each sequence of number we need to print it.
		// We need to define the behaviour that what needs to be done. when we get
		// number
		// To define behaviour we use method refrence.
		// method refrence = class name ::(double colon) method name
		numbers.stream()
			.forEach(FP01Functional::print);
		
		//print is a static method. 
		// we use it's class name to call this 
		
		//Here what we do?
		//will take the numbers - convert it to stream - and for each element - do a print.
		

	}
}
```
![Alt text](image-139.png)
### Syntax  of Method refrence
 Class name :: method name (provide method should be static)
==
# 261 step-3 Improving Java function via filter.
### Simplify the previous implementation.
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		printAllNumbersInListFunctional(numbers);
	}
	

	private static void printAllNumbersInListFunctional(List<Integer> numbers) {

		//System.out contain static method println		 
		numbers.stream()
			.forEach(System.out::println);		
	}
}
```
### Output is same as previous.
In Structured approach - we have to focus on  
1. how to loop the numbers
2. print them

IN functional apprach= we get list of element and we define what to do with element.

### Print only even numbers from list
#### Traditional approach
```java
package programming;

import java.util.List;

public class FP01Structured {

	public static void main(String args[]) {

		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		printEvenNumbersInListStructured(numbers);
	}

	private static void printEvenNumbersInListStructured(List<Integer> numbers) {
		for (int number : numbers) {
			
			if(number%2 == 0)
				System.out.println(number);
		}
	}
}
```
![Alt text](image-140.png)

#### Functional approach
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		printEvenNumbersInListFunctional(numbers);
	}
	
	//2nd
	private static boolean isEven(int number) {
		
		return number%2 == 0;
	}
	
	private static void printEvenNumbersInListFunctional(List<Integer> numbers) {
	 
		//apply filter() - only allow even numbers
		//2nd
		// if filter passes number then print.
		
		numbers.stream()
			.filter(FP01Functional::isEven)
			.forEach(System.out::println);	
		
		//Here we are not calling the method
		// we are declaring the method.
		//that stated that this method need to be called on each of the numbers whatever stream
		// gives
	}
}
```
![Alt text](image-141.png)
==
# 262 step=4 using lambda experession
![Alt text](image-142.png)
 ```java
 package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		printEvenNumbersInListFunctional(numbers);
	}

	private static void printEvenNumbersInListFunctional(List<Integer> numbers) {

		// Lambda expression - is a simpler way of defining method.
		// Take the number and check it's even things and return back.

		numbers.stream()
			.filter(number -> number % 2 == 0)
			.forEach(System.out::println);
	}
}
 ```
 ![Alt text](image-143.png)  
 In filter method if this lambda expression condition is true then go ahead.  
 Here we focus on.
 1. When you got number via stream what to check via filter
 2. After filtering what to do with that.
==
# 263 Step=05 Exercise
![Alt text](image-144.png)
### Print odd number
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		printOddNumbersInListFunctional(numbers);
	}

	private static void printOddNumbersInListFunctional(List<Integer> numbers) {
  
		numbers.stream()
			.filter(number -> number % 2 != 0)
			.forEach(System.out::println);
	}
}
```
![Alt text](image-145.png)
### Print all courses individually.
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<String> courses = 
				List.of("Spring","Spring Boot","API", "Microservices",
						"AWS","PCF","Azure","Docker","Kubernates");
	
		courses.stream()
				.forEach(System.out::println);		
	}
	
}
```
![Alt text](image-146.png)

### Print only those whose contain the word spring.
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<String> courses = 
				List.of("Spring","Spring Boot","API", "Microservices",
						"AWS","PCF","Azure","Docker","Kubernates");
	
		courses.stream()
				.filter(course -> course.contains("Spring"))
				.forEach(System.out::println);		
	}
	
}
```
![Alt text](image-147.png)
### Print courses whose name has atleast 4 charcter.
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {

		List<String> courses = 
				List.of("Spring","Spring Boot","API", "Microservices",
						"AWS","PCF","Azure","Docker","Kubernates");
	
		courses.stream()
				.filter(course -> course.length()>= 4)
				.forEach(System.out::println);		
	}
	
}
```
![Alt text](image-148.png)
==
# 264 step-6 via map
### We want to print Square of numbers.
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {
		
		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		
		printSquareOfNumbersInList(numbers);
	}

	private static void printSquareOfNumbersInList(List<Integer> numbers) {
		
		numbers.stream()
				.map(number -> number * number)
				.forEach(System.out::println);		
	}
	
}
```
![Alt text](image-149.png)
### Print Squar of even number
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {
		
		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		
		printSquareOfEvenNumbersInList(numbers);
	}

	private static void printSquareOfEvenNumbersInList(List<Integer> numbers) {
		
		numbers.stream()
				.filter(number -> number%2 == 0)
				.map(number -> number * number)
				.forEach(System.out::println);		
	}
	
}
```
![Alt text](image-150.png)
![Alt text](image-151.png)
### Find the cubes of odd numbers
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {
		
		List<Integer> numbers = List.of(12, 9, 13, 4, 6, 2, 4, 12, 15);
		
		printSquareOfOddNumbersInList(numbers);
	}

	private static void printSquareOfOddNumbersInList(List<Integer> numbers) {
		
		numbers.stream()
				.filter(number -> number%2 != 0)
				.map(number -> number * number * number)
				.forEach(System.out::println);		
	}
	
}
```
![Alt text](image-152.png)
### Print length of this courses
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {
		
		List<String> courses = 
				List.of("Spring","Spring Boot","API", "Microservices",
						"AWS","PCF","Azure","Docker","Kubernates");
		
		courses.stream()
				.forEach(course -> System.out.println(course + " : " + course.length()));
	}

}
```
![Alt text](image-153.png)
### other way
```java
package programming;

import java.util.List;

public class FP01Functional {

	public static void main(String args[]) {
		
		List<String> courses = 
				List.of("Spring","Spring Boot","API", "Microservices",
						"AWS","PCF","Azure","Docker","Kubernates");
		
		courses.stream()
				.map(course -> course +  " = " + course.length())
				.forEach(System.out::println);
	}

}
```
![Alt text](image-154.png)
==
# 265 Step-7 Optional
![Alt text](image-155.png)
### Find first fruit that start with b
```java
package programming;

import java.util.List;

public class PlayingWithOptinal {

	public static void main(String[] args) {
		List<String> fruits = List.of("apple","banana","mango");
		
		fruits.stream()
				.filter(fruit -> fruit.startsWith("b"))
				.forEach(System.out::println);		
	}
}
```
![Alt text](image-156.png)
### Other way
```java
package programming;

import java.util.List;
import java.util.Optional;
import java.util.function.Predicate;

public class PlayingWithOptinal {

	public static void main(String[] args) {
		List<String> fruits = List.of("apple","banana","mango");
		
		Predicate<? super String> predicate = fruit -> fruit.startsWith("b");
		
		//We need to findFirst() 
		
		Optional<String> optional = fruits.stream()
											.filter(predicate)
											.findFirst();	
		
		//Why we get optional here 
		//since whatever variable you pass might or might not here
		// and optional is a container object
		//A container object which may or may not contain a non-null value.
		
		
		System.out.println("optional := "+optional);
		System.out.println("optional.isEmpty() := "+optional.isEmpty());
		System.out.println("optional.isPresent() := "+optional.isPresent());
		System.out.println("optional.get() := "+optional.get());//return the specific value
		
	}

}
```
![Alt text](image-157.png)

### What happen if we insert value which are not present in list.
![Alt text](image-158.png)
If there are no value then you have Optiona.empty instead of null.

If there you think that you would encounter with null go with  Optonal .

## if you want to create a value in optional
 ```java
 package programming;

import java.util.List;
import java.util.Optional;
import java.util.function.Predicate;

public class PlayingWithOptinal {

	public static void main(String[] args) {
		
		Optional<String> fruit = Optional.of("banana");
		System.out.println(fruit.get());
	}

}
 ```
 ![Alt text](image-159.png)
### Instead of representing null value use optional
```java
package programming;

import java.util.Optional;

public class PlayingWithOptinal {

	public static void main(String[] args) {
		
	//If you want to represent empty value you can do that also
	 Optional<String> empty = Optional.empty();
		
	}

}

```







# Appendix-10
# Section-10 (232-245) Introduction to spring boot in 12 steps

# 232 Step-1 Getting Started with Spring Boot -Goals
![Alt text](image-44.png)

![Alt text](image-45.png)

# 233 Step-2 Understand the world before Spring Boot- 10000 feet overview
![Alt text](image-46.png)
![  ](image-47.png)  
If you need to create Rest API then you require spring framework, spring mvc framwork, etc also you need to manage their dependency in pom.xml.

![Alt text](image-48.png) 
U also need to configure dispatcher servlet in web.xml

![Alt text](image-49.png)
apart from it you need to define other configuration's also



![Alt text](image-51.png)
Also woried about Non Functional requirements like logging,monitoring and error handling..
U need to properly handle the error.etc
![Alt text](image-52.png)

![Alt text](image-53.png)
==
# 234 Step-3 Setting up new spring boot project with Spring initializer.

![Alt text](image-54.png)

Snapshot version(don't use it, this are verison under developement)  
milestone version  
released version
![Alt text](image-55.png)

![Alt text](image-56.png)
![Alt text](image-57.png)  
And select the folder structure where you unzip the code.  

### Run the application
![Alt text](image-58.png)
==
# 235 Step-4 Build a Hello World! API with Spring boot
/*
 * What you want to do in CourseController
 * 
 * http://localhost:8080/courses - we need to create this api
 * [
 * 	{
 * 		"id" : 1,
 * 		 "name" : "Learn AWS",
 * 		"author" : "Aditya"
 * 	}
 * ]
 * 
 * So we need to create  
 *    url  of   /courses 
 *   
 * when somebody hits this url it will get data back
 *   ,=i.e  Course : id, name, author
 * */

 Ctr + shift + O ==> It will take imports automatically.

![Alt text](image-59.png)

### Course.java
```java
package com.adi.springboot;

public class Course {
	
	private long id;
	private String name;
	private String author;	
	
	public Course(long id, String name, String author) {
		super();
		this.id = id;
		this.name = name;
		this.author = author;
	}
	
	public long getId() {
		return id;
	}
	public String getName() {
		return name;
	}
	public String getAuthor() {
		return author;
	}
	@Override
	public String toString() {
		return "Course [id=" + id + ", name=" + name + ", author=" + author + "]";
	}
}
```
### CourseController.java
```java
package com.adi.springboot;

import java.util.Arrays;
import java.util.List;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

//Need to create a rest api that's why @RestController
@RestController
public class CourseController {

	//  /course
	//  Course : id, name ,author
	//We require set of courses
	
	@RequestMapping("/courses")
	public List<Course> retriveAllCourses(){ 
		
		return Arrays.asList(
				//here we create our new Courses
				new Course(1, "Learn Aws","ASR "),
				new Course(2, "Learn DevOps","ASR ")
				);
	}

}
```
![Alt text](image-60.png)
==
# 236 step-5 Understand the goal of Spring boot
![Alt text](image-61.png)
==
# 237 Step-6 Understanding Spring Boot magic 

### It provide set of predefined dependencies which help to create rest api.
![Alt text](image-62.png)

Spring boot starters is convinient dependancy descriptors for diff feature.  
To build an application you require dependancy all that dependencies are predefined in starter project.   

जब  भी  project बनाना  है  तब  हमको  कई  साडी  dependancy लगती . Starter project उन  सबको  group करके  हमको  provide करता .
==

# 238.Step-7 Understand Spring boot magic Autoconfiguration
 ![Alt text](image-63.png)

```
जब   भी  आप   spring की  web app बनाते  हो  आपको  lot of configuration करनी  पड़ती . 
Eg – component scan, dispatcher servlet, data source  etc.

Autoconfiguration is generated based on which type of framework is present on your class path. 
हम  pom.xml में  starter project की  dependency  जैसे ही लगते  वो  कई  सारी framework add करता है .

वैसे  spring boot default configuration provide करता है पर  आप  उसको  अपने  configuration लिख  कर  override भी  कर  सकते  
Combination of your and default config = auto configuration
```
### Web application /Restful app बनाने  में  जो  भी  configuration लग  रहे है  वो  यहाँ  defined है 
![Alt text](image-64.png)

Change in defualt configuration. 
Go to application.proeperties file.

### application.properties file
```properties
logging.level.org.springframework=debug
```
here we change logging level property.

B4 this
![Alt text](image-65.png)
After changing logging level in app.pro
![Alt text](image-66.png)
![Alt text](image-67.png)
![Alt text](image-68.png)

In conditional Evaluation report  
 positive matches : successfully autoconfigured for you.  
 negative matches : not autoconfigured for you.

 ### Now analyse positive mathes
  Go to DisptacherServletAutoconfiguration
  ![Alt text](image-69.png)

#### When it will autoconfigure 
 1. this is enable when we build web app or rest api 
or 
2.  dispacther servlet  present in class path(since we add starter project already dispatcher servlet is present in class path.)

Similarly
![Alt text](image-70.png)
This is also auto configuring default error page.
![Alt text](image-71.png)
![Alt text](image-72.png)
![Alt text](image-73.png)
==
# 239. step-8 build faster with spring boot dev tool

![Alt text](image-76.png)

### Add dependency in pom.xml
![Alt text](image-74.png)

```java
package com.adi.springboot;

import java.util.Arrays;
import java.util.List;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class CourseController {

	@RequestMapping("/courses")
	public List<Course> retriveAllCourses(){ 
		
		return Arrays.asList(
				//here we create our new Courses
				new Course(1, "Learn Aws","ASR "),
				new Course(2, "Learn DevOps","ASR "),
				new Course(3, "Learn Azure","ASR "),
				new Course(4, "Learn GCP","ASR ")
				);
	}

}
```
![Alt text](image-75.png)
==
# 240. step-9 Get Production ready with spring boot-1-Profiles
![Alt text](image-77.png)
![Alt text](image-78.png)

![Alt text](image-80.png)

We have diffrent configuration for different environment for same app.  
Here profiles comes in picture.

For diff environment configuration we need to create diff profile.

![Alt text](image-81.png)

### How can you create profile?


#### application.properties 
```properties
logging.level.org.springframework=debug
```
#### application-dev.properties 
```properties
logging.level.org.springframework=trace
```

#### application-prod.properties 
```properties
logging.level.org.springframework=info
```
Currently application doesn't use any profile so defualt application.properties is running

Currently debug log and all level bellow debug log is executes.
![Alt text](image-82.png)
![Alt text](image-83.png)

### Configure a profile of production

application.properties file
```properties
logging.level.org.springframework=debug
spring.profiles.active=prod
```
![Alt text](image-84.png)

because you mention you want to configure via prod it will get more priority than normal application property.

### Now configure profile to dev environment

application.properties file
```properties
logging.level.org.springframework=debug
spring.profiles.active=dev
```
Every log trace is generated. very big log.

![Alt text](image-85.png)
==
# 241. Step-10 Get prod ready with Spring boot 2 - configuration property

### How would you setup complex configuration for your app.
हम  अभी  currency-service से  talk कर  रहे  है .   
and we have lot of value for it like.  
//currency-service.url=  
//currency-service.username=  
//currency-service.key=

यदि  आपको  configuration देनी  है .so let's create a class of it.

### CurrencyServiceConfiguration.java
```java
package com.adi.springboot;

import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.stereotype.Component;

//currency-service.url=
//currency-service.username=
//currency-service.key=

//we have to provide configuration for the above properties so use
//@ConfigurationProperties annotation.
//there are many other properties value present in application.properties file 
//how should spring identify use prefix. 
//the property which started with this. Is the value for this property.

//We need to create object  of this- so give this task to spring.
//use @Component


@ConfigurationProperties(prefix = "currency-service")
@Component
public class CurrencyServiceConfiguration {

	private String url;
	private String username;
	private String key;

	public String getUrl() {
		return url;
	}

	public void setUrl(String url) {
		this.url = url;
	}

	public String getUsername() {
		return username;
	}

	public void setUsername(String username) {
		this.username = username;
	}

	public String getKey() {
		return key;
	}

	public void setKey(String key) {
		this.key = key;
	}

}
```

### Set it value in application.properties file
```properties
logging.level.org.springframework=debug
spring.profiles.active=dev


currency-service.url=http://default.aditya.com
currency-service.username=default_username
currency-service.key=default_key

```

### To view everything is working let's create a controller. It will help us to view value of configuration.
```java
package com.adi.springboot;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class CurrencyConfigurationController {

	@Autowired
	private CurrencyServiceConfiguration configuration;
	
	@RequestMapping("/currency-configuration")
	public CurrencyServiceConfiguration retrive() {
		
		return configuration;
	}
}
```
![Alt text](image-86.png)

अभी  profile active है  dev configuration की . But वह  हमने  ये  currency-configuration की  property set नहीं  किये  है ... 

निति  ऐसी  है .. की  profile अभी  dev की  set है   
 पर  वो  combinatiaon  में  property लेता .   
 मने   application.properties और  application-dev.properties में  जितनी  properties है  वो  लेंगे .  
यदि  कोई  property common है  applicaton और  application-dev में  तो  application-dev ये  override मारेंगा.   
so result would be combining and overriding properties. 

ये  currency-service वह  configure नहीं  है .. इसीलिए  यहाँ  से  चल  रही  है .. हम  यदि  इसको  dev में  set करे  तो .

### application-dev.properties
```properties
 logging.level.org.springframework=info

 
 currency-service.url=http://dev.aditya.com
currency-service.username=dev_username
currency-service.key=dev_key

```
![Alt text](image-87.png)

### 1 exception i encounter
if you add constructor in configuration you will get bellow exception


### CurrencyServiceConfiguration
```java
@ConfigurationProperties(prefix = "currency-service")
@Component
public class CurrencyServiceConfiguration {

	private String url;
	private String username;
	private String key;



	public CurrencyServiceConfiguration(String url, String username, String key) {
		super();
		this.url = url;
		this.username = username;
		this.key = key;
	}

	public String getUrl() {
		return url;
	}

	public void setUrl(String url) {
		this.url = url;
	}

	public String getUsername() {
		return username;
	}

	public void setUsername(String username) {
		this.username = username;
	}

	public String getKey() {
		return key;
	}

	public void setKey(String key) {
		this.key = key;
	}

}
```
![Alt text](image-88.png)

Always be aware..
==
# 242 Step-11 Embeded Server
हमारे  multiple environments होते  है .  
सो  हमको  deployement process बड़ी  simple होना .  

### Old Approach
![Alt text](image-89.png)  
पहले  java install करो .  
फिर  install web/applicaton server.  
फिर  deploy the application  war file.

![Alt text](image-90.png)

### new Approach
![Alt text](image-91.png)  
पहले  install java  
ready to run jar file.
![Alt text](image-92.png)

![Alt text](image-93.png)

![Alt text](image-94.png)
This will run commoand mvn clean and install
![Alt text](image-95.png)

Take jar out of it.  
\Users\Asus\.m2\repository\com\adi\springboot\learn-spring-boot\0.0.1-SNAPSHOT\learn-spring-boot-0.0.1-SNAPSHOT.jar  

I will open command prompt and cd into sepcific folder

require java 17 or more
![Alt text](image-96.png)

Now run jar file  
java -jar your_jar_fileName

![Alt text](image-97.png)

Now आप  अब  सारी  url check कर  सकते .App आपकी  launch हो  चुकी  है 

![Alt text](image-98.png)

सो  हमको  webserver install करने  की  जरुरत  नहीं  it's part of our jar file.  
Terminate via ctr + c
![Alt text](image-99.png)

![Alt text](image-100.png)
==
# 243 Step-12 Actuator
U can monitor your entire application की  background में  हो  क्या  रहा  है .

To make visible actuator. Add their dependancy in pom.xml
![Alt text](image-101.png)

Now type /actuator in web
![Alt text](image-102.png)  
Abhi current url aur health url hi dikha raha hai.

click on heath url
![Alt text](image-103.png)  
Health i.e status of your application is up and running

आप  जब  भी  actuator launch करेंगे  तो  by default केवल  health ही  show होता  है .  
if you require all actuator features are enabled then 
go to 

### application.properties 
```properties
logging.level.org.springframework=debug
spring.profiles.active=dev


currency-service.url=http://default.aditya.com
currency-service.username=defaultusername
currency-service.key=defaultkey

# It will include all endpoints provided by actuator.
management.endpoints.web.exposure.include=*
```

![Alt text](image-104.png)

यदि  आप  bean open karo   
![Alt text](image-106.png)  
हमको  dispatcher servlet, CourseControoler, ErrorMvc सब  bean देखने  को  मिल  रही  है .

![Alt text](image-105.png)

Next endpoint is configprop
![Alt text](image-107.png)

जो  हमने  configure किया  वो  दिख  रहा  है 
![Alt text](image-108.png)

go to env endpoint

![Alt text](image-109.png)

go to metric.. 

![Alt text](image-111.png)

अब  यदि  server request metric open करना  है 
![Alt text](image-112.png)

It will tracking the number of request comming to your actuator.


अगर  आपको  explicit endpoint configure करना  है  सारी  नहीं .
तब  
```properties
logging.level.org.springframework=debug
spring.profiles.active=dev


currency-service.url=http://default.aditya.com
currency-service.username=defaultusername
currency-service.key=defaultkey

# configure specific endpoints
management.endpoints.web.exposure.include=health,metrics
```
![Alt text](image-113.png)

![Alt text](image-114.png)
==

# 244 step13 Understanding spring boot vs spring mvc

### Spring framework 

All about dependecny
1. Define dependency via @Component,@Service etc
2. Identify dependancy via @Component scan
3.  You can autowire them together. 

database से  integrate करना  है  we have spring-jpa  
unit test - spring-mokito

### Spring mvc
fully focus on web app and rest api  
tightcoupling in strut

### Spring boot
lot of configuration problem ख़तम  करता .
![Alt text](image-115.png)
==
# 245 step 14 review
![Alt text](image-116.png)
==

# Section-11 Appendix Introduction to JPA
==
# 246 Step-1 Getting  started with JPA and hibernates
![Alt text](image-357.png)
![Alt text](image-358.png)
==
# 247 Step-2 Setting up Spring Boot project for JPA and hibernate.
![Alt text](image-359.png)
![Alt text](image-360.png)
==
# 248 Step-3 Launching up H2 console and creating course table in h2
h2 is in-memory database

### How to connect with h2 db.
This is h2 url printed in log start with jdbc:h2:mem
![Alt text](image-361.png)
So now we want to connect to h2 db which is running in this url.

### Enable h2 console or access the h2 db
Go to application.properties file  
![Alt text](image-363.png)
![Alt text](image-362.png)

This will give access to h2 console.
![Alt text](image-364.png)

![Alt text](image-365.png)

![Alt text](image-366.png)

This is dynamic url changing each time when you restarted application.

### let's create static url
![Alt text](image-367.png)  
restart app and check log
![Alt text](image-368.png)

![Alt text](image-369.png)
![Alt text](image-370.png)
Currrently nothing in h2 console.

### Create a table in h2
Configure schema.file   
Go to resources -rgt clk - sql file
![Alt text](image-371.png)
![Alt text](image-372.png)  
u can also create normal file but save that with sql extension

id store long type then in h2 it will become bigInt  
name  
author  
want to define a primary key   

![Alt text](image-373.png)  
save this.. automatically pick up this file and create the table in h2.
stop and restart the app
![Alt text](image-374.png)

![Alt text](image-375.png)

![Alt text](image-376.png)
also check it's syntax

# 249. Step-4 Getting started with spring Jdbc

insert some data into table.
![Alt text](image-377.png)

![Alt text](image-380.png)

![Alt text](image-378.png)

![Alt text](image-381.png)

![Alt text](image-379.png)  
data in h2 lost after restart.
### Application.properties file
```properties
spring.h2.console.enabled=true
spring.datasource.url=jdbc:h2:mem:testdb
```
### Schema.sql
```sql
create table course
(
	id bigint not null,
	name varchar(255) not null,
	author varchar(255) not null,
	primary key (id)
);
```
 
==
# 250 Step-5 Inserting hardcoded data using spring Jdbc
Target : Execute above query(Simple query) via Spring Jdbc

Create a repository which can talk with course table.
1. use JdbcTemplate since you are using spring jdbc and autowoire them.
2. Create a method which can fire query.Then via jdbctemplate use update() method to fire query.
3. Create hardcoded query

### CourseRepository.java
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Repository;

//This is a repository which talk with course table
@Repository
public class CourseRepository {

	//1.
	// Fire query to db via Spring jdbc
	@Autowired
	private JdbcTemplate jdbcTemplate;

	//3.
	private static String INSERT_QUERY =
			// This is text block 3 double codes
			// you can type whatever you want.
			// u can retain the formatting of query.
			"""
					insert into course(id,name,author)
					values(1,'Learn Aws','in28minutes');

			""";

	//2.
	public void insert() {
		// let's hardcode the query
		jdbcTemplate.update(INSERT_QUERY);
	}
}
```
When application start up you want to fire insert query via spring boot command line runner.

### CourseJdbcCommandLineRunner.java
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Repository;

//app के  startup पर  चालना  है  सो  implements CommandLineRunner
//Interface used to indicate that a bean should run when it is contained within a SpringApplication
//When you have some logic to run at the start of application use CommandLineRunner

//@Component so that spring framework find it in auto scan.

@Component
public class CourseJdbcCommandLineRunner implements CommandLineRunner{ 

	@Autowired
	private CourseRepository courseRepository;
	
	@Override
	public void run(String... args) throws Exception {
		
		//fire up the insert query
		//This is calling query
		courseRepository.insert();
		
	}

}
```
![Alt text](image-382.png)
==
# 251 Step-6 Inserting and deleting the data using SpringJdbc.


अगर  यही  code हम  jdbc से  लिखते  तो  बहुत  java code लिखना  पड़ता . But via SpringJdbc we write very less java code.


Insert the details of specific course at runtime
### CourseRepository.java
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Repository;

import com.aditya.springboot.course.Course;

@Repository
public class CourseRepository {

	@Autowired
	private JdbcTemplate jdbcTemplate;

	//2.
	//Now our insert query become
	private static String INSERT_QUERY =

			"""
				insert into course(id,name,author)
				values(?,?,?);
				
			""";

	//Insert the details for Specific course
	//Course लेंगे .. उससे  details लेंगे  and execute the query.
	public void insert(Course course){

		//value should be in same order as ? here..
		jdbcTemplate.update(INSERT_QUERY,
				course.getId(),course.getName(),course.getAuthor());
	}
}
```
### Course.java
```java
package com.aditya.springboot.course;

public class Course {
	private long id;
	private String name;
	private String author;	
	
	public Course() {
		
	}
	public Course(long id, String name, String author) {
		super();
		this.id = id;
		this.name = name;
		this.author = author;
	}
	
	public long getId() {
		return id;
	}
	public String getName() {
		return name;
	}
	public String getAuthor() {
		return author;
	}
	
	@Override
	public String toString() {
		return "Course [id=" + id + ", name=" + name + ", author=" + author + "]";
	}	
}
```
### CourseJdbcCommandLineRunner
YOU can pass single or multiple statements in run method.
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Repository;

import com.aditya.springboot.course.Course;

@Component
public class CourseJdbcCommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseRepository courseRepository;

	@Override
	public void run(String... args) throws Exception {

		//In sql always use '' single quotes
		// in java always use "" double quotes
		courseRepository.insert(new Course(1,"Learn Phython","in28min"));
		courseRepository.insert(new Course(2,"Learn Aws","in28min"));
		courseRepository.insert(new Course(3,"Learn DevOps","in28min"));
	}
}
```
![Alt text](image-383.png)

### Delete query

### CourseRepository.java
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Repository;

import com.aditya.springboot.course.Course;

@Repository
public class CourseRepository {

	


	@Autowired
	private JdbcTemplate jdbcTemplate;

	
	private static String INSERT_QUERY =

			"""
				insert into course(id,name,author)
				values(?,?,?);
				
			""";
	
	private static String DELETE_QUERY =

			"""
				delete from course
				where id=?;
				
			""";

	public void insert(Course course){

		jdbcTemplate.update(INSERT_QUERY,
				course.getId(),course.getName(),course.getAuthor());
	}
	
	//Delete query
	public void deleteById(long id) {
		
		jdbcTemplate.update(DELETE_QUERY,id);
	}
}
```

### CourseJdbcCommandLineRunner.java
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Repository;

import com.aditya.springboot.course.Course;

@Component
public class CourseJdbcCommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseRepository courseRepository;

	@Override
	public void run(String... args) throws Exception {

	
		courseRepository.insert(new Course(1,"Learn Phython","in28min"));
		courseRepository.insert(new Course(2,"Learn Aws","in28min"));
		courseRepository.insert(new Course(3,"Learn DevOps","in28min"));
		
		courseRepository.deleteById(1);
	}
}
```
![Alt text](image-384.png)
===
# 252 Step-7 Quering data using SpringJdbc

Retreive some data from db.
### CourseRepository.java
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.BeanPropertyRowMapper;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.stereotype.Repository;

import com.aditya.springboot.course.Course;

@Repository
public class CourseRepository {

	@Autowired
	private JdbcTemplate jdbcTemplate;

	private static String INSERT_QUERY =

			"""
				insert into course(id,name,author)
				values(?,?,?);
				
			""";
	
	private static String DELETE_QUERY =

			"""
				delete from course
				where id=?;
				
			""";
	
	//Get the details for specific course
	private static String SELECT_QUERY =

			"""
				select * from course
				where id=?;
				
			""";

	public void insert(Course course){

		jdbcTemplate.update(INSERT_QUERY,
				course.getId(),course.getName(),course.getAuthor());
	}
	
	public void deleteById(long id) {
		
		jdbcTemplate.update(DELETE_QUERY,id);
	}
	
	//When you execute a query you get the course back
	
	public Course findById(long id) {
		
		//humko query execute karke return karna hai sth
		
		// so hum jdbcTemplate.update() to use nhi kar sakte.
		
		//So we use query - for returning  Course 
		//use queryForObject for returning specific Course
		
		//Now 1. we have select query which we want to fire
		
		//2. jab bhi aap query execute karonge to course ka object nahi milne wala.. fhir kayka object milenga ResultSet ka.
		//jab bhi query execute hongi wo Result set ka object return karenga hamesha
		//humko Result set ke object ko apne bean se map karna honga.
		// ResultSet -> to bean mapping
		
		//3rd. id as input.
		
		//The thing which help us to bind ResultSet to bean are rowMapper
		//They map each row of rs to specific bean
		//so ResultSet ko konse class ke sath map karna hai course class ke sath
		
		
		return	jdbcTemplate.queryForObject(SELECT_QUERY, new BeanPropertyRowMapper<>(Course.class),id);
		
		//hum fire kar rahe hai select query for particular id aur jo bhi result set ka object aavenga usko hum 
		//map karenge apne (Course)bean ke sath via BeanPropertyRowMapper() 
	}
}
```
### Course.java 
we add setter other wise null value come in object
```java
package com.aditya.springboot.course;

public class Course {
	private long id;
	private String name;
	private String author;	
	
	public Course() {
		
	}
	public Course(long id, String name, String author) {
		super();
		this.id = id;
		this.name = name;
		this.author = author;
	}
	
	public long getId() {
		return id;
	}
	public String getName() {
		return name;
	}
	public String getAuthor() {
		return author;
	}
	
	public void setId(long id) {
		this.id = id;
	}
	public void setName(String name) {
		this.name = name;
	}
	public void setAuthor(String author) {
		this.author = author;
	}	
	@Override
	public String toString() {
		return "Course [id=" + id + ", name=" + name + ", author=" + author + "]";
	}
}
```
### CourseJdbcCommandLineRunner.java
```java
package com.aditya.springboot.course.jdbc;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Repository;

import com.aditya.springboot.course.Course;

@Component
public class CourseJdbcCommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseRepository courseRepository;

	@Override
	public void run(String... args) throws Exception {

	
		courseRepository.insert(new Course(1,"Learn Phython","in28min"));
		courseRepository.insert(new Course(2,"Learn Aws","in28min"));
		courseRepository.insert(new Course(3,"Learn DevOps","in28min"));
		
		courseRepository.deleteById(1);
		
		System.out.println(courseRepository.findById(2));
		System.out.println(courseRepository.findById(3));
	}
}
```
### Output at console
![Alt text](image-385.png)
==
# 253 Step-8 Getting Started with JPA and entity Manager

SpringJdbc mein aap java ka code to kam likh rahe ho but query likhne ke liye magajmari karna pad raha hai.

Abhi to ek table hai course karke query likhna utna bhari nahi jaa raha hai. But jaise jaise table badhte javenge.It's became headache. 

To resolve this JPA comes in picture.

With this we can directly map our Course bean to Course table present in db.

1. Map your java bean to table.
```java
package com.aditya.springboot.course;

import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.Id;

//Created a mapping between our java bean and table
@Entity
public class Course {
	
	@Id
	private long id;
	
	private String name;	
	private String author;	
	
	public Course() {
		
	}
	public Course(long id, String name, String author) {
		super();
		this.id = id;
		this.name = name;
		this.author = author;
	}
	
	public long getId() {
		return id;
	}
	public String getName() {
		return name;
	}
	public String getAuthor() {
		return author;
	}
	
	public void setId(long id) {
		this.id = id;
	}
	public void setName(String name) {
		this.name = name;
	}
	public void setAuthor(String author) {
		this.author = author;
	}	
	@Override
	public String toString() {
		return "Course [id=" + id + ", name=" + name + ", author=" + author + "]";
	}
}
```
2. to play with this Create a JPA repo
```java
package com.aditya.springboot.course.jpa;

import org.springframework.stereotype.Repository;

import com.aditya.springboot.course.Course;

import jakarta.persistence.EntityManager;
import jakarta.persistence.PersistenceContext;
import jakarta.transaction.Transactional;

//jab bhi JPA ke sath query execute karna hai require @Transaction

@Repository
@Transactional
public class CourseJpaRepository {

	//For JPA to talk with Db require EntityManager
	//use entity manager to manage our entity
	//@Autowired also works but use 
	//Expresses a dependency on a container-managed EntityManager and itsassociated persistence context.
	
	@PersistenceContext
	private EntityManager entityManager;
	
	//Insert a row
	//in merge() everything is already map.
	public void insert(Course course) {
		
		entityManager.merge(course);
	}
	
	
	public Course findById(long id) {
		
		//What to find - Course.class
		//what is primary key
		return entityManager.find(Course.class, id);
	}
	
	public void deleteById(long id) {
		
		//For delete 
		// 1. find the entity
		//2. then delete
		
		Course course = entityManager.find(Course.class, id);
		entityManager.remove(course);
	}
}
```
3. show_sql
```properties
spring.h2.console.enabled=true
spring.datasource.url=jdbc:h2:mem:testdb
spring.jpa.show-sql=true
```

4. for execution
```java
package com.aditya.springboot.course.jpa;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

import com.aditya.springboot.course.Course;

@Component
public class CourseJPACommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseJpaRepository repository;

	@Override
	public void run(String... args) throws Exception {

		repository.insert(new Course(1, "Learn Phython1 JPA", "in28min"));
		repository.insert(new Course(2, "Learn Aws1 JPA", "in28min"));
		repository.insert(new Course(3, "Learn DevOps1 JPA", "in28min"));

		repository.deleteById(1);

		System.out.println(repository.findById(2));
		System.out.println(repository.findById(3));
	}
}

```
if you not write this annotation then
![ ](image-386.png)


![Alt text](image-387.png)
![Alt text](image-388.png)
![Alt text](image-390.png)
# 254 Step-9 Exploring magic of JPA
![Alt text](image-391.png)
# 255  step-10 Getting started with SpringData JPA
jab JPA mein apko query par focus nhi karna tha to ab aap SpringDataJPA par kyu shift ho rahe hai.

JPA mein Entity Manager hota tha..jo entity ko manage karta  tha.   
SpringDataJPA entity manager ko bhi khud hi handle karta.

![Alt text](image-392.png)
```java
package com.aditya.springboot.course;

import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.Id;

//Created a mapping between our java bean and table
@Entity
public class Course {
	
	@Id
	private long id;
	
	private String name;	
	private String author;	
	
	public Course() {
		
	}
	public Course(long id, String name, String author) {
		super();
		this.id = id;
		this.name = name;
		this.author = author;
	}
	
	public long getId() {
		return id;
	}
	public String getName() {
		return name;
	}
	public String getAuthor() {
		return author;
	}
	
	public void setId(long id) {
		this.id = id;
	}
	public void setName(String name) {
		this.name = name;
	}
	public void setAuthor(String author) {
		this.author = author;
	}	
	@Override
	public String toString() {
		return "Course [id=" + id + ", name=" + name + ", author=" + author + "]";
	}
}
```
```java
package com.aditya.springboot.course.springdatajpa;

import org.springframework.data.jpa.repository.JpaRepository;

import com.aditya.springboot.course.Course;

public interface CourseSpringDataJPARepository  extends JpaRepository<Course, Long>{
	
	

}

```
```java
package com.aditya.springboot.course.springdatajpa;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

import com.aditya.springboot.course.Course;

@Component
public class CourseSpringDataJPACommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseSpringDataJPARepository repository;

	@Override
	public void run(String... args) throws Exception {

		//for insert we have save method 
		repository.save(new Course(1, "Learn Phython1 SpringDataJPA", "in28min"));
		repository.save(new Course(2, "Learn Aws1 SpringDataJPA", "in28min"));
		repository.save(new Course(3, "Learn DevOps1 SpringDataJPA", "in28min"));

		//We are passsing integer and the methods expect long
		repository.deleteById(1L);

		System.out.println(repository.findById(2L));
		System.out.println(repository.findById(3l));
	}
}

```
![Alt text](image-393.png)
![Alt text](image-394.png)
==
# 256 step-11 Exploring feature of SpringDataJPA
```java
package com.aditya.springboot.course.springdatajpa;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

import com.aditya.springboot.course.Course;

@Component
public class CourseSpringDataJPACommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseSpringDataJPARepository repository;

	@Override
	public void run(String... args) throws Exception {

		
		repository.save(new Course(1, "Learn Phython1 SpringDataJPA", "in28min"));
		repository.save(new Course(2, "Learn Aws1 SpringDataJPA", "in28min"));
		repository.save(new Course(3, "Learn DevOps1 SpringDataJPA", "in28min"));

		//findAll the courses
		System.out.println(repository.findAll());
		
	
		
		//How many entity are present
		System.out.println(repository.count()); //3 select count(*) from course
	}
}
```
Output  
1. 

	
	 [Course [id=1, name=Learn Phython1 SpringDataJPA, author=in28min],  Course [id=2, name=Learn Aws1 SpringDataJPA, author=in28min], Course [id=3, name=Learn DevOps1 SpringDataJPA, author=in28min]]
		
### We can also add custom method to SpringDataJPA

i want to search by author
```java
package com.aditya.springboot.course.springdatajpa;

import java.util.List;

import org.springframework.data.jpa.repository.JpaRepository;

import com.aditya.springboot.course.Course;

public interface CourseSpringDataJPARepository  extends JpaRepository<Course, Long>{
	
	//custom method
	// i want to search via author
	//follow Naming convention
	//finBy attribute name
	// What the method take name of author
	// what it will return list of courses
	
	List<Course> findByAuthor(String author);

}
```
```java
package com.aditya.springboot.course.springdatajpa;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

import com.aditya.springboot.course.Course;

@Component
public class CourseSpringDataJPACommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseSpringDataJPARepository repository;

	@Override
	public void run(String... args) throws Exception {

		
		repository.save(new Course(1, "Learn Phython1 SpringDataJPA", "in28min"));
		repository.save(new Course(2, "Learn Aws1 SpringDataJPA", "in28min"));
		repository.save(new Course(3, "Learn DevOps1 SpringDataJPA", "in28min"));

		
		
		//Find course by author
		System.out.println(repository.findByAuthor("in28min"));
		/*
		 * [Course [id=1, name=Learn Phython1 SpringDataJPA, author=in28min], 
		 * Course [id=2, name=Learn Aws1 SpringDataJPA, author=in28min], 
		 * Course [id=3, name=Learn DevOps1 SpringDataJPA, author=in28min]]
		 * */
		System.out.println("======================================");
		System.out.println(repository.findByAuthor(""));//[]
		
	}
}
```
### Find by courseName
```java
package com.aditya.springboot.course.springdatajpa;

import java.util.List;

import org.springframework.data.jpa.repository.JpaRepository;

import com.aditya.springboot.course.Course;

public interface CourseSpringDataJPARepository  extends JpaRepository<Course, Long>{
	
	List<Course> findByAuthor(String author);

	List<Course>  findByName(String name);
}

```
```java
package com.aditya.springboot.course.springdatajpa;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

import com.aditya.springboot.course.Course;

@Component
public class CourseSpringDataJPACommandLineRunner implements CommandLineRunner {

	@Autowired
	private CourseSpringDataJPARepository repository;

	@Override
	public void run(String... args) throws Exception {

		
		repository.save(new Course(1, "Learn Phython1 SpringDataJPA", "in28min"));
		repository.save(new Course(2, "Learn Aws1 SpringDataJPA", "in28min"));
		repository.save(new Course(3, "Learn DevOps1 SpringDataJPA", "in28min"));

		
		
		System.out.println(repository.findByName("Learn Aws1 SpringDataJPA"));
		
		//Course [id=2, name=Learn Aws1 SpringDataJPA, author=in28min]
	}
}

```
==
# 257 step-12 Understanding the diff between hibernate and JPA
JPA makes talking to db very very easy.


![Alt text](image-395.png)
also cross check in maven dependancy jar

![Alt text](image-396.png)


![Alt text](image-397.png)






# Section-2 Introduction to web services:
# 5. What is web service?
![Alt text](image.png)
--
![Alt text](image-1.png)
No  this is not the defination of web service.
--
![Alt text](image-2.png)
This is to-do app with login logout and you add delete todo info.  
हमारे दोस्त  एक   social app बना  रहा  है . और  वह  वो  ये  todo app लेना  चाह रहा  है .   
ये   todoApp  हमने  spring boot के  help से  बनाया  है  जिसमे  html use  किया है   as front end .. हमारे  dost को  logic चाइये  उसे  html से  लेना  देना  नहीं  है .
Basically the html is not consumable by his social app.  
So solution is:
![Alt text](image-3.png)  
दोस्त  बोलै  मुझको  सिर्फ  तेरा  business और  data layer से  मतलब  है  मुझको  उसकी  jar बनके  देदे .. मई  अपने  app में  add कर  दूंगा .
![Alt text](image-4.png)  
data layer को  db लगेंगे . यदि  सारी dependacy मेरे  mitra satisfy कर  लेवे . तब  वो  ये  to-do app use कर  सकता  है  apni social website पर .  
Problem:  
कल  हमने  to-do app को  upgrade किया . तो  उसे  हमें  upgraded version की  jar बनाकर  देना  होंगे . Which is again complicated task.

the solution for all above problem are resolved by web service.
![Alt text](image-5.png)

![Alt text](image-6.png)

todo aap सिर्फ  human interaction कर  सकता  है अभी , पर  application to application interaction नहीं . So it's not web service.

![Alt text](image-7.png)  
Interoperable किसी  भी  language के  app में  चल  जावे .Java/phython/.net etc

हम  jar देंगे  और  वो  jar store होंगी  locally. This is not available over n/w.
--
# 6. How question related to web-service.
![Alt text](image-16.png)
![Alt text](image-8.png)  
हमने  todo app बनाया  है  for time being assume it's webservice. जिसमे  list of todo है . यदि  किसी  और  app को  ये  todoApp   use करना  है ..
तब  वो  request करेंगा/input देंगे  की  मुझको  ranga के  todos होना .   
और  jo output आवेगा   वो  response होंगे  हमारी  webservice से .
![Alt text](image-9.png)
If app A require some data from webservice it needs to create a request. 
eg- i want todo of ranga.
Webservice recive the request process it and send back list of todos of ranga as response to app A;

So how does data exhange between app take place= via request response.

![Alt text](image-10.png)
![Alt text](image-11.png)       
To make a web service platform independent we should make a request and response as platform independent.
![Alt text](image-12.png)
![Alt text](image-13.png)
.
![Alt text](image-14.png)
![Alt text](image-15.png)
--
# 7. Web services key terminology

![Alt text](image-16.png)
Input to webservice is request. Output from webservice is response.  
Format of Request and response is message exchange format.It would be xml or Json.
![Alt text](image-17.png)
![Alt text](image-19.png)

![Alt text](image-20.png)
![Alt text](image-21.png)

![Alt text](image-18.png)
Transport defines how the service is called.  
 If service is exposed over internet आप  url से  call कर  रहे  हो .
or service exposed over a queue.   
2 popular format http and mq 
![Alt text](image-22.png)
--

# 8 Introduction to Soap web service.
![Alt text](image-24.png)
==
![Alt text](image-23.png)  
SOAP= simple object Access protocol(This is no longer abbreviation like request response, soap is also term)   
Communicate / message exchange restriction via xml only.   

Soap define specific way for building webservices.

***Format we use in soap is xml***
![Alt text](image-25.png)

## Speicfic xml request and response structure in Soap

![Alt text](image-27.png)

![Alt text](image-28.png)

## eg of Soap based response
![Alt text](image-29.png)

![Alt text](image-30.png)
![Alt text](image-31.png)

--
# 9. Introduction to Restful web service.
![Alt text](image-32.png)  
Roy Feilding ने   बनाए है  इसने  http भी  बनाया  था .
![Alt text](image-33.png)

![Alt text](image-35.png)

## A resource is sth which you want to exposed to outside world.
![Alt text](image-36.png)

![Alt text](image-34.png)

![Alt text](image-40.png)


![Alt text](image-41.png)


![Alt text](image-38.png)

![Alt text](image-39.png)
==
# 10. Soap vs Restful web services.
![Alt text](image-42.png)
![Alt text](image-43.png)
==


# Section -3 Restful web service with Spring boot
# 12 step-0  bulding rest api with boot
![Alt text](image-117.png)
![Alt text](image-118.png)
==
# 14 step-1 Building rest api with boot
![Alt text](image-120.png)
![Alt text](image-121.png)

![Alt text](image-122.png)
==
# 15 Step-2 Creating HelloWorld! Rest API  

***The webservices package is main package here.***  
![Alt text](image-123.png)
### HelloWorldController.java
```java
package com.adi.rest.webservices.helloworld;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;

//   expose rest-api
// When someone fire /hello-world  => Hello World!(it return piece of text)

@RestController
public class HelloWorldController {

	
	//expose this url 
	
	//on which path / url -> is given by path
	
	@RequestMapping(method = RequestMethod.GET,path = "/hello-world")
	public String helloWorld() {
		
		return "Hello World!";
	}
}

```
![Alt text](image-124.png)

### Code improvement
```java
package com.adi.rest.webservices.helloworld;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class HelloWorldController {

	@GetMapping(path = "/hello-world")
	public String helloWorld() {
		
		return "Hello World!";
	}
}
```
Same output
==
# 16. Step-3 Enhancing HelloWorld! rest api to return bean.
### How to return  a json back from rest api

### HelloWorldController.java
```java
package com.adi.rest.webservices.helloworld;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class HelloWorldController {

	@GetMapping(path = "/hello-world")
	public String helloWorld() {
		
		return "Hello World!";
	}
	
	
	@GetMapping(path = "/hello-world-bean")
	public HelloWorldBean helloWorldBean() {
		
		return  new HelloWorldBean("Hello World!");
	}
}

```


### Specify code mein kaha insert hona hai
![Alt text](image-126.png)
```java
package com.adi.rest.webservices.helloworld;

public class HelloWorldBean {

	private String message;

	public HelloWorldBean(String message) {
		this.message = message;
	}

	public String getMessage() {
		return message;
	}

	public void setMessage(String message) {
		this.message = message;
	}

	@Override
	public String toString() {
		return "HelloWorldBean [message=" + message + "]";
	}

}
```
![Alt text](image-127.png)

### //need to create getter and setter in HelloWorldBean class otherwise exception. 
![Alt text](image-125.png)
==
# 17 step-4 what's happening in background? Theroy

### We change log level to debug in application.properties
```properties
logging.level.org.springframework=debug
```
If you don't see the log
![Alt text](image-160.png)
कोई  भी  request सबसे  पहले  dispatcher servlet के  पास  आती 
![Alt text](image-161.png)
dispatcher servlet उस  request को  map करता  appropriate controller method के  साथ . 

Once find it will return response.

Dispather servlet is configured by Autoconfiguration
![Alt text](image-162.png)

![Alt text](image-163.png)
### How helloworld bean is converted into json
![Alt text](image-164.png)

RestController has ResponseBody annotation - which tells this bean should be return as ease. By the way the jakartas Convertor is alos autoconfigured by spring boot.
![Alt text](image-165.png)
![Alt text](image-166.png)

### 3 Who is configure error mapping.
![Alt text](image-167.png)
![Alt text](image-168.png)
![Alt text](image-169.png)


==
# 18 Step-05 Enhancing rest api via @PathVariable.

### What are Path Parameters?
let's look at the url   
/users/{id}/todos/{id}  =>  /users/1/todos/101   
yaha hum specific user ke specific todos ko capture kar rahe 
hai.  

ye jo value yaha hai 1,101 ye varaibles ki value hai. This variables are called as path parameter.

### HelloWorldController.java
```java
package com.adi.rest.webservices.helloworld;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class HelloWorldController {

	@GetMapping(path = "/hello-world")
	public String helloWorld() {
		
		return "Hello World!";
	}
	
	
	@GetMapping(path = "/hello-world-bean")
	public HelloWorldBean helloWorldBean() {
		
		return  new HelloWorldBean("Hello World!");
	}
	
	
	// /hello-world/path-variable/{name}
	//{name} it indicate that name is variable
	
	// /hello-world/path-variable/Aditya = to capture this value inside variable
	// use @PathVariable Annotation
	// Whatever your variable is assigned to String name
	//  ये  annotation automatically map कर  देंगे  Aditya को  name से  	
	
	@GetMapping(path = "/hello-world/path-variable/{name}")
	public HelloWorldBean helloWorldPathVariable(@PathVariable String name) {
		
		return  new HelloWorldBean("Hello World!" + name);
	}
}
```
### Output
![Alt text](image-128.png)
==
### Writing code in another way. Use String.format
```java
package com.adi.rest.webservices.helloworld;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class HelloWorldController {

	@GetMapping(path = "/hello-world")
	public String helloWorld() {
		
		return "Hello World!";
	}
	
	
	@GetMapping(path = "/hello-world-bean")
	public HelloWorldBean helloWorldBean() {
		
		return  new HelloWorldBean("Hello World!");
	}
	
	
	//We are using String.format and replacing the name here in %s
	
	@GetMapping(path = "/hello-world/path-variable/{name}")
	public HelloWorldBean helloWorldPathVariable(@PathVariable String name) {
		
		return  new HelloWorldBean(String.format("Hello World! , %s", name));
	}
}
```
### Output
![Alt text](image-129.png)
==
# 19. Step-6 Designing Rest-API for social media app.Th

जब  भी  हम  social media app की  बात  करेंगे ..we talk about
1.	User
2.	उनके  posts
उसके  कुछ  detail हम  store करेंगे .
![Alt text](image-170.png)

![Alt text](image-171.png)
![Alt text](image-172.png)
Go to inspect go to network tab check the request type.
हमको  कुछ  action perform करने  है  अपने  resource पर .
1.	Delete a user
2.	Create a user
3.	Update post
4.	Etc
हमको  request method use करना  होंगे . उपरोक्त  चीजे  करने  के  लिए .
![Alt text](image-173.png)
Patch – यदि  सिर्फ  birth date update करना  है .. part of resource then go for patch.

जब  भी  हम  Rest api की  बात  करेंगे .
1.	हम   resources की  बात  करेंगे 
2.	And actions that perform on those resources.

Let’s design the rest api for our social media app  
***For user***  
![Alt text](image-174.png)  
***For post***  
Remember post are tied to user  
![Alt text](image-175.png)

![Alt text](image-176.png)

we use plurals for request.Much easier to read and understand. And also it make more sense.
![Alt text](image-177.png)


==
# 20 step-7. Creating User bean and UserDao Service.
![Alt text](image-130.png)

In user i want to store id,name and birthDate.  
Let's create a user bean.

### User.java
```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;

public class User {

	private Integer id;
	private String name;
	private LocalDate birthDate;

	public User(Integer id, String name, LocalDate birthDate) {
		super();
		this.id = id;
		this.name = name;
		this.birthDate = birthDate;
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public LocalDate getBirthDate() {
		return birthDate;
	}

	public void  setBirthDate(LocalDate birthDate) {
		this.birthDate = birthDate;
	}

	@Override
	public String toString() {
		return "User [id=" + id + ", name=" + name + ", birthDate=" + birthDate + "]";
	}

}

```
So this is a user bean. हमको  save करना  है  user,update the details of users, delte etc perform all other operations. 

तो  हमको  db operation करना  है  उसके  लिए  dao class बनाना  होंगे .

Target : fetch all users.

```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;

import org.springframework.stereotype.Component;

//ये  UserDaoService spring manage करे  that's why @Component

@Component
public class UserDaoService {

	//वैसे  तो  हमें  सारी चीजे  db में  store करनी  है .
		//But time being हम  return करेंगे  static list.
	
	//static empty list is created
	private static List<User> users = new ArrayList<>();
	
	//initialize this empty list 
	static {
		
		//LocalDate.now() will give the current date
		// minusYear() कितने  साल  पीछे 
		users.add(new User(1, "Adam", LocalDate.now().minusYears(30)));
		users.add(new User(2, "Eve", LocalDate.now().minusYears(25)));
		users.add(new User(3, "Jim", LocalDate.now().minusYears(20)));
	}
	
	//Target to fetch all users
	public List<User> findAll(){
		
		return users;		
	}	
}
```
ok
==

# 22. Step-08 Implementing get method for User Resource.

```java
package com.adi.rest.webservices.user;

import java.util.List;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserResource {

    private	UserDaoService service;
    
    //for injection require 
    //Getter&setter -for setter injection 
    //or Constructor for Constructor injection
   
    public UserResource(UserDaoService service) {
		
		this.service = service;
	}
    
	
	// GET/users
	@GetMapping("/users")
	public List<User> retriveAllUsers(){
		
		return service.findAll();
	}

	
}
```
![Alt text](image-178.png)

### Get the details of specific user

#### UserDaoService.java
```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;

import org.springframework.stereotype.Component;


@Component
public class UserDaoService {

	private static List<User> users = new ArrayList<>();
	
	static {
		users.add(new User(1, "Adam", LocalDate.now().minusYears(30)));
		users.add(new User(2, "Eve", LocalDate.now().minusYears(25)));
		users.add(new User(3, "Jim", LocalDate.now().minusYears(20)));
	}
	
	//Target to fetch all users
	public List<User> findAll(){
		
		return users;		
	}
	
	//If id mathces 
	//find first one whose id is matching and get it back.
	
	//Target to fetch specific user
	public User findOne(int id) {
		
	 return	users.stream()
			 	.filter(user -> user.getId().equals(id))
			 	.findFirst()
			 	.get();
	}
	
}
```
#### UserResource.java
```java
package com.adi.rest.webservices.user;

import java.util.List;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserResource {

    private	UserDaoService service;
    
    public UserResource(UserDaoService service) {
		
		this.service = service;
	}    
	
	// GET/users
	@GetMapping("/users")
	public List<User> retriveAllUsers(){
		
		return service.findAll();
	}

	
	
	//Get/users/{id}
	@GetMapping("/users/{id}")
	public User retriveUser(@PathVariable int id) {
		
		return service.findOne(id);
	}
	
}
```

![Alt text](image-179.png)

### Write in another way
#### UserDaoService.java
```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;

import org.springframework.stereotype.Component;

@Component
public class UserDaoService {

	private static List<User> users = new ArrayList<>();

	static {
		users.add(new User(1, "Adam", LocalDate.now().minusYears(30)));
		users.add(new User(2, "Eve", LocalDate.now().minusYears(25)));
		users.add(new User(3, "Jim", LocalDate.now().minusYears(20)));
	}

	// Target to fetch all users
	public List<User> findAll() {

		return users;
	}

	// Target to fetch specific user
	public User findOne(int id) {

		Predicate<? super User> predicate = user -> user.getId().equals(id);
		return users.stream().filter(predicate).findFirst().get();
	}

}
```
Output is same
==
# 23 Step-09 Implementing Post method to create a resource.

Add extention of  Talent api tester  in chrome  

```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;

import org.springframework.stereotype.Component;

@Component
public class UserDaoService {

	//3
	private static int userCount = 0;
	
	private static List<User> users = new ArrayList<>();

	static {
		users.add(new User(++userCount, "Adam", LocalDate.now().minusYears(30)));
		users.add(new User(++userCount, "Eve", LocalDate.now().minusYears(25)));
		users.add(new User(++userCount, "Jim", LocalDate.now().minusYears(20)));
	}

	// Target to fetch all users
	public List<User> findAll() {

		return users;
	}

	// Target to fetch specific user
	public User findOne(int id) {

		Predicate<? super User> predicate = user -> user.getId().equals(id);
		return users.stream().filter(predicate).findFirst().get();
	}
	
	//for post
	//once you get user detail you want to save 
	//here is list
	
	//Wheenver you want to save you need to dynamically return id.
	// so we play with count variable.
	//go to 3
	
	public int save(User user) {
		user.setId(++userCount);
		users.add(user);
		return userCount;
	}

}
```
```java
package com.adi.rest.webservices.user;

import java.util.List;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserResource {

    private	UserDaoService service;
    
    public UserResource(UserDaoService service) {
		
		this.service = service;
	}    
	
	// GET/users
	@GetMapping("/users")
	public List<User> retriveAllUsers(){
		
		return service.findAll();
	}

	//Get/users/{id}
	@GetMapping("/users/{id}")
	public User retriveUser(@PathVariable int id) {
		
		return service.findOne(id);
	}
	
	//Here we need to pass request along with entire body of user
	//Therfore @RequestBody annotation
		
	// Post/users
	@PostMapping("/users")
	public void createUser(@RequestBody User user) {
		
		service.save(user);
	}
	
}
```

![Alt text](image-180.png)
![Alt text](image-181.png)
==
# 24 Step-10 Enhancing Post method to return correct HttpStatusCode and Location.

### Sending Correct response status
![Alt text](image-182.png)

![Alt text](image-183.png)

### Setting Correct response status 
***For post we set 201 as created status***  

***सो  हम  response status किसकी  सहायता  से  set कर  पावेंगे?***   
    ResponseEntity की  सहयता  से 

In ResponseEntity there are different method for differnt status.

ResponseEntity.created(null).build();
![Alt text](image-185.png)

```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;

import org.springframework.stereotype.Component;

@Component
public class UserDaoService {

	//3
	private static int userCount = 0;
	
	private static List<User> users = new ArrayList<>();

	static {
		users.add(new User(++userCount, "Adam", LocalDate.now().minusYears(30)));
		users.add(new User(++userCount, "Eve", LocalDate.now().minusYears(25)));
		users.add(new User(++userCount, "Jim", LocalDate.now().minusYears(20)));
	}

	public List<User> findAll() {

		return users;
	}

	public User findOne(int id) {

		Predicate<? super User> predicate = user -> user.getId().equals(id);
		return users.stream().filter(predicate).findFirst().get();
	}
	
    //Instead of id return user.
	public User save(User user) {
		user.setId(++userCount);
		users.add(user);
		return user;
	}

}
```

```java
package com.adi.rest.webservices.user;

import java.util.List;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserResource {

	private UserDaoService service;

	public UserResource(UserDaoService service) {

		this.service = service;
	}

	@GetMapping("/users")
	public List<User> retriveAllUsers() {

		return service.findAll();
	}

	@GetMapping("/users/{id}")
	public User retriveUser(@PathVariable int id) {

		return service.findOne(id);
	}

    //Main changes
	// Setting Response status
	//Type of ResponseEntity is User.
	@PostMapping("/users")
	public ResponseEntity<User> createUser(@RequestBody User user) {

		service.save(user);
		//For post we set 201 as created
		//created method available in ResponseEntity for setting status.
		// .build() we want to return ResponseEntity back 
		//instead of bodyBuilder.
		return ResponseEntity.created(null).build();
	}

}
```
![Alt text](image-184.png)

***Improve further***  
When we create a rest api we need to think in terms of consumer.

यहा  पर  conusmer of Api नया  user create कर  रहा  है .
जैसे  ही  user create हो  गया  उसको  201 का  response status code  भेजा  हमने .  

क्या  हम  साथ  में  उसको  URI भी  भेज  सकते  जो  create हुआ .
माने /users/4 so that वो  वह  जेक  details check कर  लेवे .की  कोनसा  नया  User add हुआ .

How to implement URI ?
Whenever you want to create URI for specific resource. you need to mention specific Header i.e Location.  
![Alt text](image-188.png)

![Alt text](image-186.png)
```java
package com.adi.rest.webservices.user;

import java.net.URI;
import java.util.List;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

@RestController
public class UserResource {

	private UserDaoService service;

	public UserResource(UserDaoService service) {

		this.service = service;
	}

	@GetMapping("/users")
	public List<User> retriveAllUsers() {

		return service.findAll();
	}

	@GetMapping("/users/{id}")
	public User retriveUser(@PathVariable int id) {

		return service.findOne(id);
	}


	@PostMapping("/users")
	public ResponseEntity<User> createUser(@RequestBody User user) {
		
		
		User savedUser = service.save(user);
		// /users/4  => // /users/{id}  ==> // /users/user.getId()
		// currentRequestUrl is upto /users
		//  after append  /4 to this
		
		// 1. we get upto /users  ==> ServletUriComponentsBuilder.fromCurrentRequest()
        //i.e http://localhost:8080/users
		// we append this  /{id} id  ==> .path("/{id}")
		// replace id with user.getId()
		//Convert all with toUri()
        //i.e http://localhost:8080/users/4 
		
		//From Uri of Current request + we add a path + replace via id + convert to Uri
		
		URI location =ServletUriComponentsBuilder.fromCurrentRequest()
								 .path("/{id}")
								 .buildAndExpand(savedUser.getId())
								 .toUri();
		
		
	
		return ResponseEntity.created(location).build();
	}

}
```
![Alt text](image-187.png)
He can fire getRequest on location to check the details.

![Alt text](image-189.png)
==
# 25 Step-11 Implementing Exception Handling -404 Resource Not Found.

![Alt text](image-190.png)  
Browser पर  अभी  1 type किया  तो  proper response दिया  with status code 200.(i.e Ok) because user id 1 is exist.

क्या  होंगे  यदि  में  browser पर  कुछ  ऐसा   दालु  जो  user exist ही  नहीं  करता  हो 
.
![Alt text](image-191.png)

लम्बा  चौड़ा  exception आया  वो  भी  get() method सेलम्बा  चौड़ा  exception आया  वो  भी  get() method से

1) explore get() method.  
current scenario
![Alt text](image-192.png)

### upgrade furthur pass null from it.
![Alt text](image-193.png)

### Output
![Alt text](image-194.png)  
Nothing comes in output  
When we right clk inspect on network security tab  
give re hit
![Alt text](image-195.png)
This is also not proper way.
==
### Furthur Upgrade
![Alt text](image-196.png)

### Create custome Exception
![Alt text](image-197.png)  
If you extends with Exception it will become checked Exception.That's why we go with runtime i.e uncehcked exception.

![Alt text](image-198.png)
Check it out
![Alt text](image-199.png)
Again exception comes but this time from our Custom Exception class.

### But if sth not found the status should be 404 here 500 status is reflect

हम  कैसे  custom exception का  status set करे  404.   
use Annotation of ResponseStatus .

![Alt text](image-200.png)

Check it out
![Alt text](image-201.png)
Now browser पर  proper दिखा  रहा  है .

We don't require so much log trace.
Go to pom.xml and comment dev tool dependancy.
![Alt text](image-202.png)
restart app and check it out.
![Alt text](image-203.png)

![Alt text](image-204.png)
![Alt text](image-205.png)


### Now go to talent api test and execute same type of request.

![Alt text](image-206.png)
जब  भी  हम  browser से  fire करते  हमको  Html response मिलता 
  .  
और  जब  हम  talent api से  करते  हमको  json response मिलता .

```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;

import org.springframework.stereotype.Component;

@Component
public class UserDaoService {

	private static int userCount = 0;
	
	private static List<User> users = new ArrayList<>();

	static {
		users.add(new User(++userCount, "Adam", LocalDate.now().minusYears(30)));
		users.add(new User(++userCount, "Eve", LocalDate.now().minusYears(25)));
		users.add(new User(++userCount, "Jim", LocalDate.now().minusYears(20)));
	}

	public List<User> findAll() {

		return users;
	}

	public User findOne(int id) {

		Predicate<? super User> predicate = user -> user.getId().equals(id);
	
		//we use orElse() method
		//If a value is present, returns the value, otherwise returns other.
		return users.stream().filter(predicate).findFirst().orElse(null);
	}
	
	public User save(User user) {
		user.setId(++userCount);
		users.add(user);
		return user;
	}

}
```
```java
package com.adi.rest.webservices.user;

import java.net.URI;
import java.util.List;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

@RestController
public class UserResource {

	private UserDaoService service;

	public UserResource(UserDaoService service) {

		this.service = service;
	}

	@GetMapping("/users")
	public List<User> retriveAllUsers() {

		return service.findAll();
	}

	@GetMapping("/users/{id}")
	public User retriveUser(@PathVariable int id) {
		
		//Capture null value to a variable.
		User user = service.findOne(id);
		
		if(user == null) {
			//Custom exception whcih super class is RunTimeException
			throw new UserNotFoundException("id : "+ id);
		}
		
		return user;
	}


	@PostMapping("/users")
	public ResponseEntity<User> createUser(@RequestBody User user) {
		
		
		User savedUser = service.save(user);		
		URI location =ServletUriComponentsBuilder.fromCurrentRequest()
								 .path("/{id}")
								 .buildAndExpand(savedUser.getId())
								 .toUri();
		return ResponseEntity.created(location).build();
	}

}
```
```java
package com.adi.rest.webservices.user;

import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.ResponseStatus;

@ResponseStatus(code = HttpStatus.NOT_FOUND)
public class UserNotFoundException extends RuntimeException {

	 
	public UserNotFoundException(String message) {
		super(message);		
	}

	
}
```
==
# 27 step-12 Implementing Generic Exception Handling for all Resources.
### Exception Response  Predefined Structure via Spring boot.
![Alt text](image-207.png)
***How spring handle this structure.***   
via ResponseEntityExceptionHandler class इसमें  कई  सारी  method है .  
इसके  
handleException() method की  सहयता  से . अभी  current structure आ  रहा  है .   

यदि  आपको  custom strucure बनानी  है .. तो  इसका  same type का  implementation provide करना  होंगे .   
1. so first extends this class  
2. provide implementation of this method 
3. and sping को  बताना  होंगे  की  exception handle करने  के  लिए  ये  चला . via @ControllerAdvice

### Custom Structure of Exception Response.

![Alt text](image-208.png)
but nothing change in output
![Alt text](image-209.png)

We need to tell spring framework.. use this..
![Alt text](image-211.png)

![Alt text](image-210.png)

For perfection we use LocalDateAndTime instead of LocalDate
![Alt text](image-212.png)
![Alt text](image-213.png)
![Alt text](image-214.png)


अभी  हम  500 status return कर  रहे  है . instead of 404.  
Target सब  exception के  लिए  500 but userNotfound के  लिए  404.

![Alt text](image-215.png)
![Alt text](image-216.png)

Cutomized properly
```java
package com.adi.rest.webservices.exceptions;

import java.time.LocalDateTime;

public class ErrorDetails {
	//timestamp
	//message
	//details
	
	private LocalDateTime timestamp;
	private String message;
	private String details;
	public ErrorDetails(LocalDateTime timestamp, String message, String details) {
		super();
		this.timestamp = timestamp;
		this.message = message;
		this.details = details;
	}
	public LocalDateTime getTimestamp() {
		return timestamp;
	}
	public String getMessage() {
		return message;
	}
	public String getDetails() {
		return details;
	}
		
}
```
```java
package com.adi.rest.webservices.exceptions;

import java.time.LocalDateTime;

import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.context.request.WebRequest;
import org.springframework.web.servlet.mvc.method.annotation.ResponseEntityExceptionHandler;

import com.adi.rest.webservices.user.UserNotFoundException;

//Activate for all controller  in project
@ControllerAdvice
public class CustomizedResponseEntityExceptionHandler extends ResponseEntityExceptionHandler {
	
	// 1
	// What type of exception you handle- here we handle all type of exception
	@ExceptionHandler(Exception.class)
	public final ResponseEntity<ErrorDetails> handleAllException(Exception ex, WebRequest request) throws Exception {
		
		//2. 
		//Create own custom exception object
		ErrorDetails errorDetails = new ErrorDetails(LocalDateTime.now(), 
													 ex.getMessage(),
													 request.getDescription(false));
		
		//3.
		//return ResponseEntity
		return new ResponseEntity<ErrorDetails>(errorDetails,HttpStatus.INTERNAL_SERVER_ERROR);
	}
	
	
	@ExceptionHandler(UserNotFoundException.class)
	public final ResponseEntity<ErrorDetails> handleUserNotFoundException(Exception ex, WebRequest request) throws Exception {
		
		
		ErrorDetails errorDetails = new ErrorDetails(LocalDateTime.now(), 
													 ex.getMessage(),
													 request.getDescription(false));
		
		return new ResponseEntity<ErrorDetails>(errorDetails,HttpStatus.NOT_FOUND);
	}
}
```
# 28 Step-13 Implementing delete method for user Resource

![Alt text](image-217.png)

![Alt text](image-218.png)  
if delete is successful you will get 200 response back.
![Alt text](image-219.png)

![Alt text](image-220.png)
### UserDaoService.java
```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;

import org.springframework.stereotype.Component;

@Component
public class UserDaoService {

	private static int userCount = 0;
	
	private static List<User> users = new ArrayList<>();

	static {
		users.add(new User(++userCount, "Adam", LocalDate.now().minusYears(30)));
		users.add(new User(++userCount, "Eve", LocalDate.now().minusYears(25)));
		users.add(new User(++userCount, "Jim", LocalDate.now().minusYears(20)));
	}

	public List<User> findAll() {

		return users;
	}

	public User findOne(int id) {

		Predicate<? super User> predicate = user -> user.getId().equals(id);	
		return users.stream().filter(predicate).findFirst().orElse(null);
	}
	
	//delete
	public void deleteById(int id) {

		Predicate<? super User> predicate = user -> user.getId().equals(id);
		
		//users.removeIf() the predicate matches
		//if id mathces we remove the user.
		users.removeIf(predicate);		
	}
	
	public User save(User user) {
		user.setId(++userCount);
		users.add(user);
		return user;
	}

}

```
### UserResource.java
```java
package com.adi.rest.webservices.user;

import java.net.URI;
import java.util.List;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

@RestController
public class UserResource {

	private UserDaoService service;

	public UserResource(UserDaoService service) {

		this.service = service;
	}

	@GetMapping("/users")
	public List<User> retriveAllUsers() {

		return service.findAll();
	}

	@GetMapping("/users/{id}")
	public User retriveUser(@PathVariable int id) {
		
		User user = service.findOne(id);		
		if(user == null)
			throw new UserNotFoundException("id : "+ id);		
		
		return user;
	}

	//delete user
	@DeleteMapping("/users/{id}")
	public void deleteUser(@PathVariable int id) {
		
		service.deleteById(id);			
	}

	@PostMapping("/users")
	public ResponseEntity<User> createUser(@RequestBody User user) {
		
		
		User savedUser = service.save(user);		
		URI location =ServletUriComponentsBuilder.fromCurrentRequest()
								 .path("/{id}")
								 .buildAndExpand(savedUser.getId())
								 .toUri();
		return ResponseEntity.created(location).build();
	}

}

```
# 29 step-14 Implementing validation for rest api.
![Alt text](image-221.png)

new user is created
![Alt text](image-222.png)

if some one try this to create new user  with
empty user name and future date. 

![Alt text](image-223.png)
still user is  created, And this is wrong one.
![Alt text](image-224.png)

We want to add   validation to rest api.
1. Add validation dependacny in pom.xml
![Alt text](image-225.png)

2. Add @Valid annotation 

Jaha data binding ho rahi hai, aur waha apne @Valid annotation lagaya so at that time of binding all the validation is invoked on object.

![Alt text](image-226.png)

Post method execute karte samay, request mein body bheji ja rahi hai.

 Aur wo request body ko bind kar rahe hai apne user object se. via @RequestBody annotation.

 Yadi hum yaha @Valid annotation lagaye so yahi par validation ka logic lag javenga jo bhi hum object par lagana chahte hai.

3. On bean let's add validation.
![Alt text](image-227.png) 

Run and Check:
![Alt text](image-228.png)
![Alt text](image-229.png)
Validation works successfully.

4. But We need to provide appropriate message to consumer.  
Go to ***ResponseEntityExceptionHandler*** class

![Alt text](image-230.png) 
and override this method to provide appropriate message to consumer.
![Alt text](image-232.png)
![Alt text](image-231.png)

![Alt text](image-233.png)

5. customized message 
![Alt text](image-234.png)

Now check:
![Alt text](image-235.png)

6. show properly

![Alt text](image-236.png)
![Alt text](image-237.png)
solve that get next error.

![Alt text](image-238.png)

7. Another approach
![Alt text](image-239.png)
![Alt text](image-240.png)

![Alt text](image-241.png)
```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;

import jakarta.validation.constraints.Past;
import jakarta.validation.constraints.Size;

public class User {

	private Integer id;	
	
	
	@Size(min = 2,message = "Name should have 2 charcter atleaset.")
	private String name;
	
	
	@Past(message = "birthdate should always in past.")
	private LocalDate birthDate;

	public User(Integer id, String name, LocalDate birthDate) {
		super();
		this.id = id;
		this.name = name;
		this.birthDate = birthDate;
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public LocalDate getBirthDate() {
		return birthDate;
	}

	public void  setBirthDate(LocalDate birthDate) {
		this.birthDate = birthDate;
	}

	@Override
	public String toString() {
		return "User [id=" + id + ", name=" + name + ", birthDate=" + birthDate + "]";
	}

}
```
```java
package com.adi.rest.webservices.user;

import java.net.URI;
import java.util.List;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

import jakarta.validation.Valid;

@RestController
public class UserResource {

	private UserDaoService service;

	public UserResource(UserDaoService service) {

		this.service = service;
	}

	@GetMapping("/users")
	public List<User> retriveAllUsers() {

		return service.findAll();
	}

	@GetMapping("/users/{id}")
	public User retriveUser(@PathVariable int id) {
		
		User user = service.findOne(id);		
		if(user == null)
			throw new UserNotFoundException("id : "+ id);		
		
		return user;
	}

	//delete user
	@DeleteMapping("/users/{id}")
	public void deleteUser(@PathVariable int id) {
		
		service.deleteById(id);			
	}

	@PostMapping("/users")
	public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
		
		
		User savedUser = service.save(user);		
		URI location =ServletUriComponentsBuilder.fromCurrentRequest()
								 .path("/{id}")
								 .buildAndExpand(savedUser.getId())
								 .toUri();
		return ResponseEntity.created(location).build();
	}

}
```
```java
package com.adi.rest.webservices.exceptions;

import java.time.LocalDateTime;

import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpStatus;
import org.springframework.http.HttpStatusCode;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.MethodArgumentNotValidException;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.context.request.WebRequest;
import org.springframework.web.servlet.mvc.method.annotation.ResponseEntityExceptionHandler;

import com.adi.rest.webservices.user.UserNotFoundException;


@ControllerAdvice
public class CustomizedResponseEntityExceptionHandler extends ResponseEntityExceptionHandler {
	

	@ExceptionHandler(Exception.class)
	public final ResponseEntity<ErrorDetails> handleAllException(Exception ex, WebRequest request) throws Exception {
		
		
		ErrorDetails errorDetails = new ErrorDetails(LocalDateTime.now(), 
													 ex.getMessage(),
													 request.getDescription(false));
		
	
		return new ResponseEntity<ErrorDetails>(errorDetails,HttpStatus.INTERNAL_SERVER_ERROR);
	}
	
	
	@ExceptionHandler(UserNotFoundException.class)
	public final ResponseEntity<ErrorDetails> handleUserNotFoundException(Exception ex, WebRequest request) throws Exception {
		
		
		ErrorDetails errorDetails = new ErrorDetails(LocalDateTime.now(), 
													 ex.getMessage(),
													 request.getDescription(false));
		
		return new ResponseEntity<ErrorDetails>(errorDetails,HttpStatus.NOT_FOUND);
	}
	
	
	@Override
	protected ResponseEntity<Object> handleMethodArgumentNotValid(
			MethodArgumentNotValidException ex, HttpHeaders headers, HttpStatusCode status, WebRequest request) {
			
		//loop aroung and get all error - this is aproach  -- getFiledErrors(). loop araound it appned string and return back.
		//another one - 
		//return count back
		ErrorDetails errorDetails = new ErrorDetails(LocalDateTime.now(), 
										" Total Errors : "+ex.getErrorCount() + " First Error : " +  ex.getFieldError().getDefaultMessage(),
										request.getDescription(false));
		
	
		
		return new ResponseEntity<>(errorDetails,HttpStatus.BAD_REQUEST);
	}
}
```
==
# 30 Step-15 Overview of Advance Rest api
![Alt text](image-242.png)
==
# 31 Step-16 OpenApi and Swagger
![Alt text](image-243.png)

swagger tool आज  भी  जिन्दा  है .. जिससे  हम  चीजे  visiualize कर  सकते . जबकि  swagger specification को  use करके  open api आज  market में  boom कर  रहा  है .
![Alt text](image-244.png)
==
# 33 Step=17  Configuring swagger doc

![Alt text](image-246.png)
![Alt text](image-245.png)

2 resources we have created. 
1. user resources
2. hello-worold-controller resource

![Alt text](image-247.png)


![Alt text](image-249.png)
![Alt text](image-248.png)
![Alt text](image-250.png)

![Alt text](image-251.png)

U can play with UI on swaggerUI
![Alt text](image-252.png)
![Alt text](image-253.png)
==
# 34 Step-18 Exploring Content negotiation- Implementing support for xml

same resource differnt representation. maane kisiko json kisiko xml
1. Part-1
![Alt text](image-254.png)

![Alt text](image-255.png)

![Alt text](image-256.png)
![Alt text](image-257.png)

1. Add dependancy
![Alt text](image-260.png)

Check output:
![Alt text](image-261.png)
we reqiuire content of xml type.
![Alt text](image-262.png)
jab bhi user header mein accept aur application/xml bhejenga we have convert into xml.available.

If user wan't json
![Alt text](image-263.png)
![Alt text](image-264.png) 
Comment this depedancy. it is problem for new spring framework feature.

2. Part-2
![Alt text](image-254.png)
![Alt text](image-258.png)

![Alt text](image-256.png)
![Alt text](image-259.png)
![Alt text](image-266.png)
# 35 Step-19 internationalization i18n
![Alt text](image-254.png)
![Alt text](image-258.png)

![Alt text](image-256.png)
![Alt text](image-259.png)

![Alt text](image-265.png)

hum header mein - accept language header bhejenge

![Alt text](image-267.png)
![Alt text](image-268.png)

Target :  
en - english  
nl -dutch so on so forth

step-1 Define this messsages somewhere

Remember : 
   1. folder is important - resources  
2.  name of file is messages.properties..

![Alt text](image-269.png)


step-2 Write the code to pick those value

```java
package com.adi.rest.webservices.helloworld;

import java.util.Locale;

import org.springframework.context.MessageSource;
import org.springframework.context.i18n.LocaleContextHolder;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class HelloWorldController {

	//	Strategy interface for resolving messages, with support for the parameterizationand internationalization of such messages.
	private MessageSource messageSource;
	
	
	
	public HelloWorldController(MessageSource messageSource) {		
		this.messageSource = messageSource;
	}


	@GetMapping(path = "/hello-world")
	public String helloWorld() {
		
		return "Hello World!";
	}
	
	
	@GetMapping(path = "/hello-world-bean")
	public HelloWorldBean helloWorldBean() {
		
		return  new HelloWorldBean("Hello World!");
	}
	
	@GetMapping(path = "/hello-world/path-variable/{name}")
	public HelloWorldBean helloWorldPathVariable(@PathVariable String name) {
		
		return  new HelloWorldBean(String.format("Hello World! , %s", name));
	}
	
	//Internationalization 
	@GetMapping(path = "/hello-world-internationalized")
	public String helloWorldInternationalized() {
		
		//From where you get the locale from incoming Request - header(part)
		//LocaleContextHolder:= Simple holder class that associates a LocaleContext instance with the current thread.
		//getLocale():Return the Locale associated with the current thread, if any,or the system default Locale otherwise. 
		Locale locale = LocaleContextHolder.getLocale();
		
		// step-2 pick property which is set
		//1. parameter is code
		//2 . if you have any variable which can replace message.. abhi kuch nhi hai isiliye leave that
		//3  Default message
		//4. locale
	
		return messageSource.getMessage("good.morning.message", null, "Default Message", locale);
		
	}
}

```

![Alt text](image-270.png)

### Now configure dutch language..
![Alt text](image-272.png)
![Alt text](image-271.png)

==
# 37 Step-20 Versioning Rest api - URI versioning.

![Alt text](image-273.png)  
***Target***

![Alt text](image-274.png)

Best practice: don't force customer for chnage. Since they need to write code to accept your change. 

Basically rest api aap kisi aur ki chij apne app  mein use kar rahe ho.. aap jo chahte the.. wo usne banake rakhi hai to hum fhir se kyu banaye..usse use karee.

So hum apne code mein manipulate karke uska app reuse karte. ..  
yadi future mein changes hue.. to thoda bahut hame bhi apne code mein change karna honga.

![Alt text](image-275.png)

![Alt text](image-276.png)
## Url versioning


#### PersonV1.java
```java
package com.adi.rest.webservices.versioning;

public class PersonV1 {
	
	private String name;

	public PersonV1(String name) {
		super();
		this.name = name;
	}

	public String getName() {
		return name;
	}

	@Override
	public String toString() {
		return "PersonV1 [name=" + name + "]";
	}
	
}
```
#### VersioningPersonController.java
```java
package com.adi.rest.webservices.versioning;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class VersioningPersonController {

	@GetMapping("/v1/person")
	public PersonV1 getFirstVersionOfPerson() {
		
		return new PersonV1("Bob Charlie");
	}
	
	@GetMapping("/v2/person")
	public PersonV2 getSecondVersionOfPerson() {
		
		return new PersonV2(new Name("Bob","charlie"));
	}
}

```

#### PersonV2.java
```java
package com.adi.rest.webservices.versioning;

public class PersonV2 {

	private Name name;

	public PersonV2(Name name) {
		super();
		this.name = name;
	}

	public Name getName() {
		return name;
	}

	@Override
	public String toString() {
		return "PersonV2 [name=" + name + "]";
	}	
}
```
#### Name.java
```java
package com.adi.rest.webservices.versioning;

public class Name {

	private String firstName;
	private String lastName;
	
	public Name(String firstName, String lastName) {
		super();
		this.firstName = firstName;
		this.lastName = lastName;
	}
	public String getFirstName() {
		return firstName;
	}
	public String getLastName() {
		return lastName;
	}
	@Override
	public String toString() {
		return "Name [firstName=" + firstName + ", lastName=" + lastName + "]";
	}	
}
```
![Alt text](image-277.png)
![Alt text](image-278.png)
==
# 38 Step-21 Versioning continue

![Alt text](image-279.png)
### RequestParameter versioning
![Alt text](image-280.png)
![Alt text](image-281.png)

### header versioning
![Alt text](image-282.png)
![Alt text](image-283.png)
![Alt text](image-284.png)

![Alt text](image-285.png)
![Alt text](image-286.png)
--
### Medial type versioning
![Alt text](image-287.png)
![Alt text](image-289.png)
![Alt text](image-288.png)


![Alt text](image-291.png)
![Alt text](image-290.png)

```java
package com.adi.rest.webservices.versioning;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class VersioningPersonController {

	@GetMapping("/v1/person")
	public PersonV1 getFirstVersionOfPerson() {

		return new PersonV1("Bob Charlie");
	}

	@GetMapping("/v2/person")
	public PersonV2 getSecondVersionOfPerson() {

		return new PersonV2(new Name("Bob", "charlie"));
	}

	// RequestParameter versioning
	@GetMapping(path = "/person", params = "version=1")
	public PersonV1 getFirstVersionOfPersonRequestParameter() {

		return new PersonV1("Bob Charlie");
	}

	@GetMapping(path = "/person", params = "version=2")
	public PersonV2 getSecondVersionOfPersonRequestParameter() {

		return new PersonV2(new Name("Bob", "charlie"));
	}

	// Header versioning
	@GetMapping(path = "/person/header", headers = "X-API-VERSION=1")
	public PersonV1 getFirstVersionOfPersonRequestHeader() {

		return new PersonV1("Bob Charlie1");
	}

	@GetMapping(path = "/person/header", headers = "X-API-VERSION=2")
	public PersonV2 getSecondVersionOfPersonRequestHeader() {

		return new PersonV2(new Name("Bob", "charlie1"));
	}

	// Media type Versioning	
	@GetMapping(path = "/person/accept", produces = "application/vnd.company.app-v1+json")
	public PersonV1 getFirstVersionOfPersonAcceptHeader() {

		return new PersonV1("Bob Charlie2");
	}
	
	@GetMapping(path = "/person/accept", produces = "application/vnd.company.app-v2+json")
	public PersonV2 getSecondVersionOfPersonAcceptHeader() {

		return new PersonV2(new Name("Bob", "charlie2"));
	}
}
```
Factors to consider

URI pollution:    
Uri versioning & request parameter versioning isme hum naye url bana rahe to represent new version. So ye uri pollution ho gaya.. uri badh gaye.
On the contrary hum same url use kar rahe header and media type versioning mein to waha uri pollution nhi ho raha.

Misuse of httpHeader :  
http header ye versioning ke liye nahi banaya gaya hai.
Ye header and mIme type versioning misuse the http header.

Caching:  
Caching is done based on the url . Header aur mime type versioning mein same url use kar rahe. to usme caching ki dikkat jati hai bahut adhik. Header par bhi dyan dena padta isme caching ke liye.

Can we execute request on the browser?
uri and request parmeter version execute hote browser par.  
par mime aur header versioning ke liye cmd line ya rest api client lagta.

Api doc:   
uri and request parameter versioning ke liye api doc banana aasan hai but contrary header and mime versioning type ke liye kathin.
![Alt text](image-292.png)
--
# 39 step-22 implementing Hateos

![Alt text](image-294.png)

jab bhi aap website par jate ho tab aap data aur actions dekhte ho.

![Alt text](image-293.png)
ye website par data hai aur sath he sath aap ispar login karke *(starr) de sakte.. fork kar sakte.

Typically website show you data and action.

![Alt text](image-295.png)
![Alt text](image-296.png) 

name, birthdate ye data hai api ka. .. aap links par click karke navigate kar sakte dusere jagah par.

That's hateos.
![Alt text](image-297.png)
Custom format mein appko khud sab banana padenga..

Another apraoch use standard implementation defined by HAL(json hypertext app lang) it is a simple format that give easy way to hyperlink between different resources.

This standard provide.  
How we can link other resources in rest api.

![Alt text](image-298.png)  
ye standard hai _links provide all other hyperlinks.

All app follow this standard.

Spring hateous allow us to genrate HAL(json hyperlink app lang) responses with hyperlinks to resources.

1. Add dependency  
![Alt text](image-299.png)

2. Scenario  
Go  to user resource abhi output kya mil riya hai
![Alt text](image-300.png)  
we get detail of specific user.  
Target: humko iske response mein uprokt ke sath sath link bhi add karni hai.

http://localhost:8080/users

3. Hateoas concept  
EntityModel  
WebMvcLinkBuilder


aapko response mein user bean ke sath link bhejna hai. Humko user bean ke structure ko change nhi karna.. 

So we wrap the user bean into entity model.

![Alt text](image-301.png)

run and check nothing happen
![Alt text](image-302.png)

4. Now we need to add links here  
EntityModel mein link add karna hai via WebMvcLinkBuilder

Inside we have methodOn() method which pick up link of specific method and add it as link.

![Alt text](image-303.png)
import static org.springframework.hateoas.server.mvc.WebMvcLinkBuilder.*;


//Will use the link  http://localhost:8080 of specific mehtod retriveAllUsers() 
		
		//which calss this.getClass() - ye class ki method hai
		//konsi method hai..retriveAllUsers()
		
		WebMvcLinkBuilder linkBuilder = linkTo(methodOn(this.getClass()).retriveAllUsers());

5. 

		//Add the link to entity model
		//all-users speicfy karnege.. relation ka
		entityModel.add(linkBuilder.withRel("all-user"));

```java
package com.adi.rest.webservices.user;

import java.net.URI;
import java.util.List;
 
import static org.springframework.hateoas.server.mvc.WebMvcLinkBuilder.*;

import org.springframework.hateoas.EntityModel;
import org.springframework.hateoas.server.mvc.WebMvcLinkBuilder;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

import jakarta.validation.Valid;

@RestController
public class UserResource {

	private UserDaoService service;

	public UserResource(UserDaoService service) {

		this.service = service;
	}

	@GetMapping("/users")
	public List<User> retriveAllUsers() {

		return service.findAll();
	}

	//http://localhost:8080
	//EntityModel: A simple EntityModel wrapping a domain object and adding links to it.
	@GetMapping("/users/{id}")
	public EntityModel<User> retriveUser(@PathVariable int id) {
		
		User user = service.findOne(id);		
		if(user == null)
			throw new UserNotFoundException("id : "+ id);		
		
		//Create Entity model
		// .of() is the static method use to create entity model
		//We want entity model around the user.
		EntityModel<User> entityModel = EntityModel.of(user);
		
		
		//2 
		//EntityModel mein link add karna hai via WebMvcLinkBuilder
		//Inside we have methodOn() method which pick up link of specific method and add it as link.
		
		//Will use the link  http://localhost:8080 of specific mehtod retriveAllUsers() 
		
		//which calss this.getClass() - ye class ki method hai
		//konsi method hai..retriveAllUsers()
		
		WebMvcLinkBuilder linkBuilder = linkTo(methodOn(this.getClass()).retriveAllUsers());
		
		//3
		//Add the link to entity model
		//all-users speicfy karnege.. relation ka
		entityModel.add(linkBuilder.withRel("all-user"));
		return entityModel;
	}

	//delete user
	@DeleteMapping("/users/{id}")
	public void deleteUser(@PathVariable int id) {
		
		service.deleteById(id);			
	}

	@PostMapping("/users")
	public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
		
		
		User savedUser = service.save(user);		
		URI location =ServletUriComponentsBuilder.fromCurrentRequest()
								 .path("/{id}")
								 .buildAndExpand(savedUser.getId())
								 .toUri();
		return ResponseEntity.created(location).build();
	}
}

```

![Alt text](image-304.png)
==
# 40 Step-23 Implementing static filtering for rest api.

Serialization: aap jo object ko json ya xml mein convert kar rahe ho use serialization kahenge.
![Alt text](image-308.png)

Jo user ka structure hai wohi json ka response hai.
![Alt text](image-305.png)

User class mein id, name aur birthdate hai.

![Alt text](image-309.png)

1. appko yadi attribute name bean ke change karna hai so use @JsonProperty annotatoin

![Alt text](image-306.png)
![Alt text](image-307.png)


Situation: appko exact sturcute nhi bhejna hai response mein.

 aapke pass pasword hai usse aapko aage nahi bhjena.

![Alt text](image-310.png)

![Alt text](image-311.png)

Eg:  
![Alt text](image-312.png)  

yaha mere pass 3 field hai, 2nd field ie. feild2 password wali hai.. mereko nahi bhejna ye.  

![Alt text](image-313.png)

2. Via static filtering.

![Alt text](image-314.png)
![Alt text](image-315.png)
![Alt text](image-316.png)

### how can we do static filetering.

![Alt text](image-317.png)
![Alt text](image-318.png)

#### Same thing happen for list also

![Alt text](image-319.png)

Even if we created filtering list, the field2 is not display due to JsonIgnore annotation.

![Alt text](image-320.png)

agar aapne koyi field par @JsonIgnore use kiya hai. so wo reponse mein display nhi hongi.. chahe kitne alag alag aap rest-api call karo.

```java
package com.adi.rest.webservices.filtering;

import com.fasterxml.jackson.annotation.JsonIgnore;

public class SomeBean {
	
	private String field1;
	
	@JsonIgnore
	private String field2;
	
	private String field3;
	
	public SomeBean(String field1, String field2, String field3) {
		super();
		this.field1 = field1;
		this.field2 = field2;
		this.field3 = field3;
	}

	public String getField1() {
		return field1;
	}

	public String getField2() {
		return field2;
	}

	public String getField3() {
		return field3;
	}

	@Override
	public String toString() {
		return "SomeBean [field1=" + field1 + ", field2=" + field2 + ", field3=" + field3 + "]";
	}	
}
```

3. via @JsonIgnoreProperties  
isse aapko class ke upar define karna hota hai.

![Alt text](image-321.png)
![Alt text](image-322.png)

you can also add multiple field but it will became an array then

![Alt text](image-323.png)
![Alt text](image-324.png)


Prefer @JsonIgnore since kal chalke property ka name change hua so @JsonIgnoreProperty mein wo set karna honga.

```java
package com.adi.rest.webservices.filtering;

import java.util.Arrays;
import java.util.List;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class FilteringController {

	@GetMapping("/filtering")
	public SomeBean filtering() {
		
		return new SomeBean("value1","value2","value3");
	}
	
	
	@GetMapping("/filtering-list")
	public List<SomeBean> filteringList() {
		
		return Arrays.asList(
				new SomeBean("value1","value2","value3"),
				new SomeBean("value4","value5","value6")
				);
	}
}
```

```java
package com.adi.rest.webservices.filtering;

import com.fasterxml.jackson.annotation.JsonIgnoreProperties;

@JsonIgnoreProperties({"field1","field2"})
public class SomeBean {
	
	private String field1;
	

	private String field2;
	
	private String field3;
	
	public SomeBean(String field1, String field2, String field3) {
		super();
		this.field1 = field1;
		this.field2 = field2;
		this.field3 = field3;
	}

	public String getField1() {
		return field1;
	}

	public String getField2() {
		return field2;
	}

	public String getField3() {
		return field3;
	}

	@Override
	public String toString() {
		return "SomeBean [field1=" + field1 + ", field2=" + field2 + ", field3=" + field3 + "]";
	}	
}

```

```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;

import com.fasterxml.jackson.annotation.JsonProperty;

import jakarta.validation.constraints.Past;
import jakarta.validation.constraints.Size;

public class User {

	private Integer id;	
		
	@Size(min = 2,message = "Name should have 2 charcter atleaset.")
	@JsonProperty("user_name")
	private String name;
	
	
	@Past(message = "birthdate should always in past.")
	@JsonProperty("birth_date")
	private LocalDate birthDate;

	public User(Integer id, String name, LocalDate birthDate) {
		super();
		this.id = id;
		this.name = name;
		this.birthDate = birthDate;
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public LocalDate getBirthDate() {
		return birthDate;
	}

	public void  setBirthDate(LocalDate birthDate) {
		this.birthDate = birthDate;
	}

	@Override
	public String toString() {
		return "User [id=" + id + ", name=" + name + ", birthDate=" + birthDate + "]";
	}

}

```
===  
# 41 step-24. Implementing dynamic filtering
![Alt text](image-325.png)
![Alt text](image-326.png)
![Alt text](image-327.png)

***static filter*** :  
Same filtering for bean accross different rest api.  

/filtering  and /filtering-list are 2 different API.   
When  we apply @JsonIgnore on particular field i.e field2 It won't appear in 2 diff API. 

***dynamic filtering***

Situation: For same bean, We have differnt filterling logic in different api.

for /filtering api - we need to filter field2  
![Alt text](image-328.png)  
and   
for  /filtering-list api - we need to filter field1  
![Alt text](image-329.png)

and both field1,field2 and field3 belongs to same bean name Somebean.

ab hum bean par filtering logic nahi laga sakte.. humko rest api ke andar lagana honga.

Now ab data ke sath filtering bhi batana hai so MappingJacksonValue comes.

1. 
![Alt text](image-330.png)


2. set filter
![Alt text](image-331.png)
![Alt text](image-332.png)
![Alt text](image-333.png)

3) on filtering-list

![Alt text](image-334.png)

![Alt text](image-335.png)
![Alt text](image-332.png)
![Alt text](image-336.png)

```java
package com.adi.rest.webservices.filtering;

import java.util.Arrays;
import java.util.List;

import org.springframework.http.converter.json.MappingJacksonValue;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import com.fasterxml.jackson.databind.ser.FilterProvider;
import com.fasterxml.jackson.databind.ser.impl.SimpleBeanPropertyFilter;
import com.fasterxml.jackson.databind.ser.impl.SimpleFilterProvider;

@RestController
public class FilteringController {

	@GetMapping("/filtering")
	public MappingJacksonValue filtering() {		
		SomeBean someBean = new SomeBean("value1","value2","value3");
		
		//1 
		MappingJacksonValue mappingJacksonValue = new MappingJacksonValue(someBean);
		
		SimpleBeanPropertyFilter filter= SimpleBeanPropertyFilter.filterOutAllExcept("field1","field3");
		
		
		
		//FilterProvider allow you to set multiple filter
		//we create SimpleFilerProvider
		//in that we create our customized filter and add it.
		//addFilter (id, object)
		FilterProvider filters = new SimpleFilterProvider().addFilter("SomeBeanFilter", filter);
		
		
		//2
		mappingJacksonValue.setFilters(filters);
		
		return mappingJacksonValue;
	}
	
	
	@GetMapping("/filtering-list")
	public MappingJacksonValue filteringList() {
		
		List<SomeBean> list = Arrays.asList(
				new SomeBean("value1","value2","value3"),
				new SomeBean("value4","value5","value6")
				);
		
		MappingJacksonValue value = new MappingJacksonValue(list);
		
		
		SimpleBeanPropertyFilter filter = SimpleBeanPropertyFilter.filterOutAllExcept("field2","field3");
		FilterProvider filters = new SimpleFilterProvider().addFilter("SomeBeanFilter", filter );
		value.setFilters(filters );
		
		return value;
	}
}

```
```java
package com.adi.rest.webservices.filtering;

import com.fasterxml.jackson.annotation.JsonFilter;
import com.fasterxml.jackson.annotation.JsonIgnoreProperties;

@JsonFilter("SomeBeanFilter")
public class SomeBean {
	
	private String field1;
	

	private String field2;
	
	private String field3;
	
	public SomeBean(String field1, String field2, String field3) {
		super();
		this.field1 = field1;
		this.field2 = field2;
		this.field3 = field3;
	}

	public String getField1() {
		return field1;
	}

	public String getField2() {
		return field2;
	}

	public String getField3() {
		return field3;
	}

	@Override
	public String toString() {
		return "SomeBean [field1=" + field1 + ", field2=" + field2 + ", field3=" + field3 + "]";
	}	
}
```
==
# 42  step-25 Monitoring Api with Spring Boot Actuator.
![Alt text](image-337.png)

Add dependency in pom.xml  
![Alt text](image-338.png)

Output:  
![Alt text](image-339.png)

By default only health of actuator is visible.
![Alt text](image-340.png)

If you want to expose more info of actuator.. go to app properties
![Alt text](image-341.png)

![Alt text](image-342.png)

1. beans
provide info about all beans which are loading in our app context.

![Alt text](image-343.png)

2. env
detials about environment where our app is running.


3. metric  
![Alt text](image-344.png)

How many http request are send to the app
![Alt text](image-345.png)

4. mappings
![Alt text](image-346.png)

==
# 43 Step-26 Exploring Api with Spring Boot HAL EXplorer


HAL - Json hypertext application language. 

Basically ye provide karta hai hyperlink resources ke bich in our api.

specific resource hai /users/1 ==> it will give details of single user.  
aur 2nd resource hai /users  ==> It will give detials of all user.   

yaha ye link kar denga... 
![Alt text](image-353.png)

here all-users ki link dikh rahi hai.  
This format is HAL format.
![Alt text](image-354.png)
--

Yadi appka api Hal use kar raha hai so you can use Hal explorer to explore your api.

non technical team play with your api.
![Alt text](image-355.png)

![Alt text](image-356.png)

Add dependency in pom.xml  
![Alt text](image-347.png)

Type localhost:8080
![Alt text](image-348.png)

![Alt text](image-349.png)

Explore bean get request
![Alt text](image-350.png)
![Alt text](image-351.png)

Similarly you expolre metrics

### let's explore api which we created.
![Alt text](image-352.png)
==

# 47 Step-28 Creating User entity and test some data

Let's create an Entity.  
hum chahte hai JPA manage kare sab so apni bean ko sajao. 
![Alt text](image-398.png)

If i write this i get exception

![Alt text](image-399.png)

Why we get this error?  
Since user is a reserve word / Keyword in H2 (in memory db) Therefore we get error. So we need to modify the table name.
![Alt text](image-400.png)

See the log
![Alt text](image-401.png)
h2 console is avialble, This is dynamic url. Lets create static url.

![Alt text](image-402.png)

Go to h2 console
localhost:8080/h2-console
![Alt text](image-403.png)
![Alt text](image-404.png)

 h2 db mein aap data insert karne ke liye data.sql file ka use kar sakte like aapne schema.sql ka use kiya tha table insert karne ke liye.

JPA automatically table create karta yadi usko @Entity mane propert bean par annotation mil gaya to. So don't like to create schema.sql in this case.

 Let's insert some data.
 ![Alt text](image-405.png)
 ![Alt text](image-406.png)

 When i save this got an exception
 ![Alt text](image-407.png)

 database mein table create hone se pehle apka data insert ho raha.That's why error.

 ![Alt text](image-408.png)

 Go-back to h2-console and relogin
 ![Alt text](image-409.png)

Inserting furthur details  
![Alt text](image-411.png)

![Alt text](image-412.png)
==
# 48 step-29 Enchancing RestApi to connect to h2 using JPA and hibernate.

Now we go for database.
![Alt text](image-413.png)
Now we use UserRepository and talk with db.

![Alt text](image-414.png)

Whenever you get exception like Ambigous mapping your mapping leads to duplication. Require unique mapping.

1. 
![Alt text](image-415.png)
Create default constructor in User otherwise you won't get proper output.
![Alt text](image-416.png)

2. To find specific user
![Alt text](image-417.png)

![Alt text](image-418.png)

3. delete user 
![ ](image-419.png)
![Alt text](image-420.png)

![Alt text](image-421.png)

4. create a user
![Alt text](image-422.png)
![Alt text](image-423.png)
![Alt text](image-424.png)

```java
package com.adi.rest.webservices.user;

import java.net.URI;
import java.util.List;
import java.util.Optional;

import static org.springframework.hateoas.server.mvc.WebMvcLinkBuilder.*;

import org.springframework.hateoas.EntityModel;
import org.springframework.hateoas.server.mvc.WebMvcLinkBuilder;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

import com.adi.rest.webservices.jpa.UserRepository;

import jakarta.validation.Valid;

@RestController
public class UserJpaResource {

	private UserRepository userRepository;

	public UserJpaResource(UserRepository userRepository) {

		this.userRepository = userRepository;
	}

	@GetMapping("/jpa/users")
	public List<User> retriveAllUsers() {

		return userRepository.findAll();
	}

	
	@GetMapping("/jpa/users/{id}")
	public EntityModel<User> retriveUser(@PathVariable int id) {
		
		Optional<User> user = userRepository.findById(id);	
		
		if(user.isEmpty())
			throw new UserNotFoundException("id : "+ id);		
		
		
		EntityModel<User> entityModel = EntityModel.of(user.get());			
		
		WebMvcLinkBuilder linkBuilder = linkTo(methodOn(this.getClass()).retriveAllUsers());
		
		entityModel.add(linkBuilder.withRel("all-user"));
		return entityModel;
	}

	
	@DeleteMapping("/jpa/users/{id}")
	public void deleteUser(@PathVariable int id) {
		
		userRepository.deleteById(id);			
	}

	@PostMapping("/jpa/users")
	public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
		
		
		User savedUser = userRepository.save(user);		
		URI location =ServletUriComponentsBuilder.fromCurrentRequest()
								 .path("/{id}")
								 .buildAndExpand(savedUser.getId())
								 .toUri();
		return ResponseEntity.created(location).build();
	}

}
```

```java
package com.adi.rest.webservices.jpa;

import org.springframework.data.jpa.repository.JpaRepository;

import com.adi.rest.webservices.user.User;

public interface UserRepository extends JpaRepository<User, Integer>{

}
```

```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;

import com.fasterxml.jackson.annotation.JsonProperty;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.Id;
import jakarta.validation.constraints.Past;
import jakarta.validation.constraints.Size;

@Entity(name = "user_details")
public class User {

	
	@Id
	@GeneratedValue
	private Integer id;	
		
	@Size(min = 2,message = "Name should have 2 charcter atleaset.")
//	@JsonProperty("user_name")
	private String name;
	
	
	@Past(message = "birthdate should always in past.")
//	@JsonProperty("birth_date")
	private LocalDate birthDate;
	
	protected User() {
		
	}

	public User(Integer id, String name, LocalDate birthDate) {
		super();
		this.id = id;
		this.name = name;
		this.birthDate = birthDate;
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public LocalDate getBirthDate() {
		return birthDate;
	}

	public void  setBirthDate(LocalDate birthDate) {
		this.birthDate = birthDate;
	}

	@Override
	public String toString() {
		return "User [id=" + id + ", name=" + name + ", birthDate=" + birthDate + "]";
	}

}
```
# 49 Step-30  Creating a post entity with many to one relationship with User Entity.

Here 
 1.  we want to create a  Post entity.
 2.  Established relationship with user_details
 3.  Populated some data in the post entity.

![Alt text](image-425.png)
 
 1. Create a Post as entity
 ![Alt text](image-426.png)
 If you go to h2-console. Table for Post is also created.
 ![Alt text](image-427.png)
 ![Alt text](image-431.png)

 2. Now we want to map post to  specific user.  

Terminology : Multiple post or Single post belongs to specific user.  
So class Post contain User and Class User contains 
List of Post>

![Alt text](image-432.png)
![Alt text](image-433.png)


## Now established relationship 
A single user has Many post
![Alt text](image-434.png)
Here you can configure here mappedBy attribute, here you can configure the fields which  owns the relationship.

Mapped By = which fileds in post owns the relationship .
![Alt text](image-436.png)
Basically multiple table banenge.. foreign key ke.. hum ek se hi pata laga sakte dono taraf ka.. So why to create extra table space.

Similarly in post we have reverse relationship
![Alt text](image-437.png)

Rest api responses mein ab hamare pass 2 bean hai. 
1. User bean ka response 
2. Post bean ka response

We don't want post to be part of Json responses for user bean and vice versa. So use JsonIgnore.

![Alt text](image-438.png)
![Alt text](image-439.png)

Let's customized @ManyToOne annotation

Agar apko same query mein post details ke sath user_details bhi fetch karna hia so you are asking for Eager loaded. (this is by default for ManyToOne relationship) use Lazy Loaded.. Mereko jo manga wo hi chaiye.

![Alt text](image-440.png)

Go to application.properties and make show_sql= true
![Alt text](image-441.png)

![Alt text](image-442.png)

![Alt text](image-444.png)
![Alt text](image-443.png)

Go to h2 console and see relationship in action
![Alt text](image-445.png)

## 3. Create some data in post table

Column not found error comes, Always use single quote for sql
![Alt text](image-446.png)

![Alt text](image-447.png)

Go to h2 console
![Alt text](image-448.png)

```java
package com.adi.rest.webservice.user;

import com.fasterxml.jackson.annotation.JsonIgnore;

import jakarta.persistence.Entity;
import jakarta.persistence.FetchType;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.Id;
import jakarta.persistence.ManyToOne;

@Entity
public class Post {

	@Id
	@GeneratedValue
	private int id;
	
	private String description;

	@ManyToOne(fetch = FetchType.LAZY)
	@JsonIgnore
	private User user;
	 
	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getDescription() {
		return description;
	}

	public void setDescription(String description) {
		this.description = description;
	}

	@Override
	public String toString() {
		return "Post [id=" + id + ", description=" + description + "]";
	}
	
}
```

```java
package com.adi.rest.webservice.user;

import java.time.LocalDate;
import java.util.List;

import com.fasterxml.jackson.annotation.JsonIgnore;
import com.fasterxml.jackson.annotation.JsonProperty;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.Id;
import jakarta.persistence.ManyToOne;
import jakarta.persistence.OneToMany;
import jakarta.validation.constraints.Past;
import jakarta.validation.constraints.Size;

@Entity(name = "user_details")
public class User {
	
	@Id
	@GeneratedValue
	private Integer id;
	
	@Size(min = 2,message = "Name should have 2 character atleast")
	@JsonProperty(value = "user_name")
	private String name;
	
	@Past(message = "birthDate should always in past")
	@JsonProperty("birth_date")
	private LocalDate birthDate;
	
	@OneToMany(mappedBy = "user")
	@JsonIgnore
	private List<Post> posts;
	
	public User() {
		super();
		
	}
	public User(Integer id, String name, LocalDate birthDate) {
		super();
		this.id = id;
		this.name = name;
		this.birthDate = birthDate;
	}
	public Integer getId() {
		return id;
	}
	public void setId(Integer id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public LocalDate getBirthDate() {
		return birthDate;
	}
	public void setBirthDate(LocalDate birthDate) {
		this.birthDate = birthDate;
	}
	@Override
	public String toString() {
		return "User [id=" + id + ", name=" + name + ", birthDate=" + birthDate + "]";
	}
}

```

```properties
server.port=8081
logging.level.org.springframework=info

management.endpoints.web.exposure.include=*

spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
spring.jpa.defer-datasource-initialization=true

spring.jpa.show-sql=true

```

```sql
insert into user_details(id,birth_date,name) 
values(1001,current_date(),'Aditya');

insert into user_details(id,birth_date,name) 
values(1002,current_date(),'ranga');


insert into user_details(id,birth_date,name) 
values(1003,current_date(),'rahul');

insert into post(id,description,user_id) 
values(20001,'Learn Aws',1001);

insert into post(id,description,user_id) 
values(20002,'Learn DevOps',1001);

insert into post(id,description,user_id) 
values(20003,'Get Aws Certified',1002);

insert into post(id,description,user_id) 
values(20004,'Get  DevOps Certified',1002);
```
---
# 50 Step-31 Implementing a Get Api to retrieve all Post from the users.

Require getter and setter in User class for List of Post
![Alt text](image-449.png)

First retrive User then post
![Alt text](image-450.png)

![Alt text](image-451.png)

```java
package com.adi.rest.webservices.user;

import java.time.LocalDate;
import java.util.List;

import com.fasterxml.jackson.annotation.JsonIgnore;
import com.fasterxml.jackson.annotation.JsonProperty;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.Id;
import jakarta.persistence.OneToMany;
import jakarta.validation.constraints.Past;
import jakarta.validation.constraints.Size;

@Entity(name = "user_details")
public class User {

	@Id
	@GeneratedValue
	private Integer id;

	@Size(min = 2, message = "Name should have 2 charcter atleaset.")
//	@JsonProperty("user_name")
	private String name;

	@Past(message = "birthdate should always in past.")
//	@JsonProperty("birth_date")
	private LocalDate birthDate;

	@OneToMany(mappedBy = "user")
	@JsonIgnore
	private List<Post> posts;

	public List<Post> getPosts() {
		return posts;
	}

	public void setPosts(List<Post> posts) {
		this.posts = posts;
	}
	protected User() {

	}

	public User(Integer id, String name, LocalDate birthDate) {
		super();
		this.id = id;
		this.name = name;
		this.birthDate = birthDate;
	}

	public Integer getId() {
		return id;
	}

	public void setId(Integer id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public LocalDate getBirthDate() {
		return birthDate;
	}

	public void setBirthDate(LocalDate birthDate) {
		this.birthDate = birthDate;
	}

	@Override
	public String toString() {
		return "User [id=" + id + ", name=" + name + ", birthDate=" + birthDate + "]";
	}

}
```

```java
package com.adi.rest.webservices.user;

import java.net.URI;
import java.util.List;
import java.util.Optional;

import static org.springframework.hateoas.server.mvc.WebMvcLinkBuilder.*;

import org.springframework.hateoas.EntityModel;
import org.springframework.hateoas.server.mvc.WebMvcLinkBuilder;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

import com.adi.rest.webservices.jpa.UserRepository;

import jakarta.validation.Valid;

@RestController
public class UserJpaResource {

	private UserRepository userRepository;

	public UserJpaResource(UserRepository userRepository) {

		this.userRepository = userRepository;
	}

	@GetMapping("/jpa/users")
	public List<User> retriveAllUsers() {

		return userRepository.findAll();
	}

	
	@GetMapping("/jpa/users/{id}")
	public EntityModel<User> retriveUser(@PathVariable int id) {
		
		Optional<User> user = userRepository.findById(id);	
		
		if(user.isEmpty())
			throw new UserNotFoundException("id : "+ id);		
		
		
		EntityModel<User> entityModel = EntityModel.of(user.get());			
		
		WebMvcLinkBuilder linkBuilder = linkTo(methodOn(this.getClass()).retriveAllUsers());
		
		entityModel.add(linkBuilder.withRel("all-user"));
		return entityModel;
	}

	
	@DeleteMapping("/jpa/users/{id}")
	public void deleteUser(@PathVariable int id) {
		
		userRepository.deleteById(id);			
	}
	
	
	@GetMapping("/jpa/users/{id}/posts")
	public List<Post> retriveAllPostOfAUser(@PathVariable int id) {
		
		//retrive a user
		Optional<User> user = userRepository.findById(id);
		
		if(user.isEmpty()) 
			throw new UserNotFoundException("id : "+id);
		
		return user.get().getPosts();
	}

	@PostMapping("/jpa/users")
	public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
		
		
		User savedUser = userRepository.save(user);		
		URI location =ServletUriComponentsBuilder.fromCurrentRequest()
								 .path("/{id}")
								 .buildAndExpand(savedUser.getId())
								 .toUri();
		return ResponseEntity.created(location).build();
	}

}
```
==
# 51 Step-32 Implementing Post Api to create a Post for a User.

To play with user we have userrepository (jisme hum save,delete etc kar sakte..hume predefined method milte) and we require PostRepository to play with Post

![Alt text](image-452.png)

For creating post initilaize via constructor injection to PostRepository
![Alt text](image-453.png)

### Creating a post for user
1. along with id we require requestBody
2. also Valid that request body

![Alt text](image-454.png)

3. Also create a getter and setter in post
![Alt text](image-455.png)

4. if user is ok then set that user in post.



5. So that in post - id is automatically created , user is store, desc comes from request body... 
		now we need to save the post. via postRepository

6. Now build uri for it
![Alt text](image-456.png)
-----------
# 52 Step-33 Exploring JPA and hibernate quries for RestApi-Theory

If you execute this url  localhost:8081/jpa/users
![Alt text](image-457.png)
Hibernate: select u1_0.id,u1_0.birth_date,u1_0.name from user_details u1_0

This query is executed in background.
Select id,birth_date,name from user_details.

![Alt text](image-458.png)

This is the code from this the above query generated automatically.

2.  fire this  http://localhost:8081/jpa/users/1001/posts

![Alt text](image-459.png)

![Alt text](image-460.png)

Here 2 queries fired.
![Alt text](image-461.png)

here first we return User back. Then we get post for specific user back..
So first we are getting user_detials then post_details.

3. 
![Alt text](image-462.png)

![Alt text](image-463.png)

![Alt text](image-464.png)

Here we are trying to insert new Post.

first fetch user_details.  
the post_sequence is generated post id which is next squence of previous id..  
then we save everthying in Post table.
![Alt text](image-465.png)
--
# 53 Step-34 Connecting Rest APi To mysql database

Currently we are storing data in IN_memory_database(h2)

How to store them in mysql database.

We launch up mysql database as a docker container.

When you are using JPA and hibernate switching from one to other database is easy.

------------
# 54 step-34z Optional Installing Docker.
Docker credentials:  
adit.rathor123@gmail.com  
Hanuman@123
![Alt text](image-466.png)

![Alt text](image-467.png)

![Alt text](image-468.png)

![Alt text](image-469.png)

1. For wsl update use following command

![Alt text](image-470.png)


2.  Hit command docker version  

![Alt text](image-471.png)

If you won't see client and server run docker desktop

Again rehit samething
![Alt text](image-472.png)

3. Launch Mysql as docker container
docker run --detach --env MYSQL_ROOT_PASSWORD=dummypassword --env MYSQL_USER=social-media-user --env MYSQL_PASSWORD=dummypassword --env MYSQL_DATABASE=social-media-database --name mysql --publish 3306:3306 mysql:8-oracle

Changes port to 3307 as bellow

![Alt text](image-473.png)

Whenever you want to run sth in OS you need to assign the port to it.

![Alt text](image-474.png)

4. Connect this with App   
Go to application.properties

Insetad of connecting to h2 in memory db we are connecting to mysql
![Alt text](image-475.png)

jab hum inmemomry db i.e h2 db ki baat karte, to spring auto configuration directly look at entity and create the tables. But in case of mysql Spring autoconfiguration table create nhi karta.

So we need to mention explicitly,also add dialect
![Alt text](image-476.png)

5. Go to pom.xml  
Here we need to configure dependency which can talk with mysql db.

***incomplete***
==
# 58. Step-36 Implementing Basic Authentication with Spring Security.

![Alt text](image-477.png)

Here anybody can access and send request to our Rest API. Sala koyi bhi aake apne application ko access kar sakta.

We require security and authentication for our rest API. Here SpringSecurity comes in picture.

1. Add spring security dependency in pom.xml
![Alt text](image-478.png)

2.  After adding dependency the password is generated in console
![Alt text](image-479.png)

3. If i go to browser and type localhost:8080/jpa/users form is diplay
![Alt text](image-480.png)  

username : user
password : console based

![Alt text](image-481.png)

4. In talent Api tester
![Alt text](image-482.png)

U can see the details  
![Alt text](image-483.png)

Now har baar password change hote rahenge whenever you restart the application.

5. Go to application.properties
![Alt text](image-485.png)


putting username and password 
![Alt text](image-484.png) 

har jagah authentication provide karta spring security.
--
# 59 Step-37 Enhancing Spring Security Configuration for Basic Authentication

For Post we get forbidden error  
![Alt text](image-486.png)

Jab bhi request send karte hai apni application ko, so it should be intercepted by Spring Security and Spring security executes a series of filter also called as filters chains. In filter chain there are series of checks.


1. All request should be authenticated.(credentials that are attached with all the request.)

2. if request is not authenticated.Then a web page is shown asking for credential.
![Alt text](image-480.png)  

3. CSRF (check) -> Post,Put (it impact our post/put request)

![Alt text](image-487.png)

Airport par aap jaa rahe ho.. So series of checks se hokar apko gujarna padta. Called as Filter chains.
1. aapke sath adhar card, plane tkt chaiye.
2. agar boarding pass nahi hai, So aapko window se nikalna honga.
3. All bagage should be check.etc

Target : Here 2 things we need to modify
1. hum rest api bana rahe hai..so itna bada web page dikhane ka koyi matlab nahi(web page web app ki liye dikhate.)
2. CSRF disabled(so that Post request work)

1. For first point here we use HttpBasic Authentication . Ye instead of web page a pop-up aavenga aur credentials le levenga.

So existing filter chain ko override karna honga.  
So Target 
![Alt text](image-488.png)

1. Create a Configuration class and define a bean of SecurityFilterChain inside in it.

![Alt text](image-489.png)

Now run app
![Alt text](image-490.png) 

It doesn't ask for credential. Here you override out defualt filter chain which is defined by Spring Security.

2. Customize it
![Alt text](image-491.png)  
After this line.   

![Alt text](image-492.png)

All request is authenticated. We won't have authority to view this page.

![Alt text](image-493.png)
![Alt text](image-494.png)

![Alt text](image-495.png)

![Alt text](image-496.png)
Now ask for basic authentication

![Alt text](image-497.png)

![Alt text](image-498.png)

![Alt text](image-499.png)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>3.1.3</version>
		<relativePath /> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.adi.rest.webservice </groupId>
	<artifactId>restful-web-service</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>restful-web-service</name>
	<description>Demo project for Spring Boot</description>
	<properties>
		<java.version>17</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-security</artifactId>
		</dependency>
		
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.data</groupId>
			<artifactId>spring-data-rest-hal-explorer</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-hateoas</artifactId>
			<version>3.1.3</version>
		</dependency>
		<!--
	<dependency>
   		 <groupId>com.fasterxml.jackson.dataformat</groupId>
		<artifactId>jackson-dataformat-xml</artifactId>
	</dependency>
		<dependency>
      <groupId>org.springdoc</groupId>
		<artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
		<version>2.0.0</version>
   </dependency>
   
   -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-validation</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
			<optional>true</optional>
		</dependency>


		<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>

```
```properties
#server.port=8081
logging.level.org.springframework=info

spring.security.user.name=user
spring.security.user.password=pass

spring.datasource.url=jdbc:h2:mem:testdb

spring.h2.console.enabled=true
spring.jpa.defer-datasource-initialization=true

spring.jpa.show-sql=true

```

```java
package com.adi.rest.webservice.security;

import static org.springframework.security.config.Customizer.withDefaults;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;

import jakarta.security.auth.message.config.AuthConfig;

@Configuration
public class SpringSecurityConfiguration {

	@Bean
	public  SecurityFilterChain  filterChain(HttpSecurity httpSecurity) throws Exception {
		
		
//		 1. All request should be aunthenticated
		
//		all request that comming in i require authenticate 
		
		httpSecurity.authorizeHttpRequests(auth -> auth.anyRequest().authenticated());
		
//		 2. Instead of Web page use basic HTTP Basic Authentication
		
		//httpBasic mein defaultSetting enable karni hai via withDefaults() method
		//ye method kaha hai?
		 // Customizer class mein withDefaults() hai
		//static import karo isse 
		httpSecurity.httpBasic(withDefaults());
		
		
//		 3. Disable CSRF
		
		httpSecurity.csrf().disable();
		
		
		return httpSecurity.build();
	}
}

```
# Section-4 Quick introduction to Microservices
# 60. Intro Microservices with Spring Cloud

Why are microservices needed?  
What are the challenges associate with them?  
How does spring cloud help us to solve them.
--
# 61 Step-1 Intro to microservices

Fuzzy - Difficult to understand

Defination:   
![Alt text](image-500.png)

***Long defination:***  
![Alt text](image-501.png)
![Alt text](image-502.png)
![Alt text](image-503.png)


Understand Microservices:  
![Alt text](image-504.png)

1. Services which are exposed by Rest
2. Small deployable unit with very well though out boundaries
3. this should be cloud enalbed

imp keyword:
1. Rest
2. Small deployable units
3. cloud enabled



2nd pont: Small deployable units
![Alt text](image-505.png)

3rd point:  cloud enaled
![Alt text](image-506.png)

cloud enabled bole to kal microservice 3 par jayda load aaya to easily uke instance badha sake. 

hum easily instance add kar sake previous wale delete kar sake. without having problem This is called cloud enabled.

---
# 62  Step-2 challenges with microservices

## Challenge
### 1. Bounded Context
![Alt text](image-507.png)
What is the right context for your microservices.

### 2. Configuration management
![Alt text](image-508.png)

### 3. Dynamic Scale up and scale down
![Alt text](image-509.png)

### 4. Visibility
![Alt text](image-510.png)
how i know my all microservices are up and running.

### 5. Pack of cards:
 ![Alt text](image-511.png)
 How do i prevent if one microservices is down so my entire app won't down.  
 How i build fault tolerance in my microservices.
--
# 63 Step-3 Intro to Spring Cloud

Distributed system mein common problem ko address karta Spring cloud.

In umbrella of Spring cloud there are multiple project which address to the problem.

Like   
1 .  Spring Cloud Config project resloved configuration problem  
2. Spring Cloud bus Project resolved communication problem.  
3 . Spring Cloud Netflix resolves problem of Eureka Server.

![Alt text](image-514.png)

Hamare pass multiple microservices hote hai.  
Multiple envrionments hote hai.  
Multiple instance bhi hote hai
![Alt text](image-515.png)
So there will be lot of configuration.

![Alt text](image-516.png)

Spring cloud Config server provide an approach jaha aap sare configuration ek jagah git mein store kar sakte.(centralize location )

Spring cloud config server ye expose karenga microservices ko different environment ke hisab se.

![Alt text](image-518.png)
![Alt text](image-517.png)

yaha CurrencyCalculationService talk kar rahi hai CurrencyExchangeService ke sath.

yaha CureencyExchangeService ke multiple instance present hai.

At any point of time we can add up or remove instances of CurrencyExchService.

![Alt text](image-519.png)

### Naming Server(Eureka)
iske 2 kaam hai  
1. instances / services register karna
2.  discovery client.

kisi bhi time par CurrencyCalulationService ye naming server ko puch sakta hai ki kitne instance of CurrencyExcService abhi avialable hai. Aur response ye url return karenga.

### Ribbion
iski sahayata se CurrencyCaluService equally apna load distribute kar sakta hai sare CurrecncyExcService instances par.

### Feign
ye rest client banane ke kaam ata

![Alt text](image-520.png)

Hum  request ko id assign karenge accross multiple componennt via Spring Cloud.   
So that we can easily track down request kaha bhaski.  
Hum Zipkin Distributed Tracing use karenge to trace request accross multiple component.


Har microservices ke kuch common feature hote hai. like logging,security analytics etc.  
We dont implment this common feture in every micorservices. 
Netflix Zull Api Gateway provide solution to this.

![Alt text](image-521.png)  
yadi Service down rehi so hystrix help us to provide proper response.
--
# 64 Step-04 Advantages of microservice Architecture.
![Alt text](image-522.png)

![Alt text](image-523.png)

Unlike monotlith application we can create microservices with diff technology.

microservice 1 - java mein bani ho  
microservice 2 - js mein bani ho so on so forth

they can communicate with each other..Jo mahol technology hongi future mein usme hame banate aata.

![Alt text](image-524.png)

Amazon webiste par festive season par jayada laod rehta yadi compare kiya jaye baki mahino se.  
So you can dynamically scale up resources/app whenever required.

![Alt text](image-525.png)
microservices ye smaller component hai.. so easy release when compare with monolith applicaton.
--
# 65 Step-05 Microservices Components  - Standardizing Ports and Url

![Alt text](image-526.png)  
we create 7 diff project so port standardize karna jaruri hai

![Alt text](image-528.png)
--
# Section-5 : Microservices with Spring Cloud-V1 

# Section-6 : Microservices with Spring Cloud-V2
# 123 What's new in v2?

Before Spring version 2.3 Ribbion was load balancer abhi with new version Spring cloud Load Balancer is there

![Alt text](image-529.png)

# 125 Have you already completed v1?
![Alt text](image-530.png)

# 127 step-1 Setting up Limits Microservices V2

![Alt text](image-531.png)

***Let's create a limit microservice***

hume limits-service connect karna hai to Spring Cloud Config server. Therefore here in dependency we add Config Client.

![Alt text](image-532.png)

***Note: Don't have any spaces in folder path other wise microservice have problem***
![Alt text](image-533.png)

![Alt text](image-534.png)

![Alt text](image-535.png)

```properties
spring.config.import=optional:configserver:http://localhost:8888
```

# 129 Step-2 Creating a hardcoded limits-service V2

***Target: Create a Rest-Api which returning hardcoded data, enhance it to pick value from configuration and then from centralized configuration***

***Create a Rest-Api which returning hardcoded data***

***Limits.java***
```java
package com.adi.microservices.bean;

public class Limits {

	private int minimum;
	private int maximum;

	public Limits() {
		super();
		// TODO Auto-generated constructor stub
	}

	public Limits(int minimum, int maximum) {
		super();
		this.minimum = minimum;
		this.maximum = maximum;
	}

	public int getMinimum() {
		return minimum;
	}

	public void setMinimum(int minimum) {
		this.minimum = minimum;
	}

	public int getMaximum() {
		return maximum;
	}

	public void setMaximum(int maximum) {
		this.maximum = maximum;
	}

}
```
***LimitsController.java***
```java
package com.adi.microservices.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import com.adi.microservices.bean.Limits;

@RestController
public class LimitsController {

	@GetMapping("/limits")
	public Limits retriveLimits() {
		
		return new Limits(1,1000);		
	}
}
```
application.properties
```properties
spring.config.import=optional:configserver:http://localhost:8888

```

![Alt text](image-536.png)

# 130 Step-3 Enhance limits-service - Get configuration from application.props

1. First we set the value in application.properties  

```properties
spring.config.import=optional:configserver:http://localhost:8888

limits-service.minimum=2
limits-service.maximum=998 

```

2.  Pick up values from application.properties file. For this Create a Configuration class and fetch everything via ConfigProperties annotation

```java
package com.adi.microservices.configuration;

import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.stereotype.Component;

//Give proper name of Configuration Properties since in our application there are many.

@Component
@ConfigurationProperties("limits-service")
public class Configuration {

	private int minimum;
	private int maximum;

	public int getMinimum() {
		return minimum;
	}

	public void setMinimum(int minimum) {
		this.minimum = minimum;
	}

	public int getMaximum() {
		return maximum;
	}

	public void setMaximum(int maximum) {
		this.maximum = maximum;
	}

}
```
3. Now controller part
```java
package com.adi.microservices.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import com.adi.microservices.bean.Limits;
import com.adi.microservices.configuration.Configuration;

@RestController
public class LimitsController {

	@Autowired
	private Configuration configuration;
	
	@GetMapping("/limits")
	public Limits retriveLimits() {
		
		return new Limits(configuration.getMinimum(),
		                 configuration.getMaximum());		
	}
}

```
Output:
![Alt text](image-538.png)

# 134 Step-4 Setting up Spring Cloud Config Server.-v2

Make sure use same version of Spring boot For config server as where config client uses.

![Alt text](image-539.png)

![Alt text](image-540.png)
For Config Server we uses 8888

Also give proper name to every project.
![Alt text](image-541.png)

# 132 Step-5 Installing Git and creating a local git repository

![Alt text](image-543.png)

Based on os downlaod and install

![Alt text](image-544.png)

## Check git version  

![Alt text](image-545.png)

### Go to particular folder where you want to create a git repo

![Alt text](image-546.png)

## Create a proper folder

![Alt text](image-547.png)

### cd to particular folder

![Alt text](image-548.png)

## For present working directory use command

![Alt text](image-549.png)

![Alt text](image-550.png)

## Create a git repository via git init

![Alt text](image-551.png)

Now here we store our centralize configuration, use proper editor for that.

Here we use Visual studio and open that folder in that.

### Here we create limits-service.properties file

![Alt text](image-552.png)

![Alt text](image-553.png)

### Now we commit changes

dir or ls: This is our file i.e limits-service.properties

![Alt text](image-554.png)

### Now we want to add this in our git repository

## First add
![Alt text](image-555.png)

## Then commit via git commit -m "comments"
![Alt text](image-556.png)

# 134 step-6 Connect Spring cloud Config Server to local Git Repository -v2

### So How to connect with github.. Go to app.properties and configure folder there
![Alt text](image-557.png)

```properties
spring.application.name=spring-cloud-config-server
server.port=8888

spring.cloud.config.server.git.uri=file:///C:/Users/Asus/OneDrive/Desktop/study/Ranga/Projects/prac1/git/git-localconfig-repo
```

```java
package com.adi.microservices;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.config.server.EnableConfigServer;

@EnableConfigServer
@SpringBootApplication
public class SpringCloudConfigServerApplication {

	public static void main(String[] args) {
		SpringApplication.run(SpringCloudConfigServerApplication.class, args);
	}

}
```
fire: http://localhost:8888/limits-service/default
![Alt text](image-558.png)

## If any problem make sure
![Alt text](image-559.png)

port and path both are correct.

# 135 step-7 Connect Limits Service to Spring Cloud Config Server.- V2


## How to do that

### Add dependecy
![Alt text](image-560.png)

### Configure the config server already done for limits-services
![Alt text](image-561.png)

### Now we need to tell this limits microservice to make use of configuration which are provided by git via Spring cloud config server.So how would you tell?

![Alt text](image-562.png)


## So value configure in git hub
![Alt text](image-563.png)

### limit-service applicaton.properties
```properties
spring.config.import=optional:configserver:http://localhost:8888

spring.application.name=limits-service
limits-service.minimum=2
limits-service.maximum=998 

```

![Alt text](image-564.png)


So LimitsServiceApplication fetching config server from http://localhost:8888
From server it require limits-service   
having profile uses as default

![Alt text](image-565.png)

so url become http://localhost:8888/limits-service/default
![Alt text](image-566.png)

Yaha se value pick kar levenga.
Git repo ki value has higher priority than property present at application.properties.

# 136 Step-8 Configuring Profiles for Limits Service

Here in Limits microservice we successfully fetch configuration from Git repo,
![Alt text](image-567.png)
let say there are multiple environment for limit microservice.  
Dev,QA,Stage,Prod environments.

How do you store separate configuration for limits microservice in diff environment.,

![Alt text](image-568.png)

We do copy pasting in particular folder 
![Alt text](image-569.png)

![Alt text](image-570.png)

![Alt text](image-571.png)

How do you call this?  
http://localhost:8888/limits-service/dev
![Alt text](image-572.png)

http://localhost:8888/limits-service/qa
![Alt text](image-573.png)

### How to configure dev profile for limits microservice.

```properties
spring.config.import=optional:configserver:http://localhost:8888

spring.application.name=limits-service
limits-service.minimum=2
limits-service.maximum=998 


spring.profiles.active=dev

spring.cloud.config.profile=dev

```

![Alt text](image-574.png)

![Alt text](image-575.png)

### Similarly for qa

```properties
spring.config.import=optional:configserver:http://localhost:8888

spring.application.name=limits-service
limits-service.minimum=2
limits-service.maximum=998 


spring.profiles.active=qa

spring.cloud.config.profile=qa

```

![Alt text](image-576.png)
![Alt text](image-577.png)

## How would you configure for other microservices.
![Alt text](image-578.png)

# 137  Debugging guide for microservices + Docker + docker compose

![Alt text](image-579.png)	

https://github.com/in28minutes/spring-microservices-v3/blob/main/03.microservices/01-step-by-step-changes/readme.md#spring-cloud-config-server---steps-01-to-08

# 138 Step-9 Intro to Currency Conversion and Exchange microservices.

![Alt text](image-580.png)
![Alt text](image-581.png)
![Alt text](image-582.png)

Currency Conversion microservice interanally call karengi currency exchange service ko aur puchengi ki aaj ka rate kya hai.. and calculate karke result devengi.

# 139 Step-10 Setting up Currency Exchange microservice.
![Alt text](image-583.png)

![Alt text](image-584.png)

![Alt text](image-585.png)

# 141 Step-11 Create a simple hardcoded currency-exchange-service

### Create a rest-api 
Uri for currency-exchange-service  
http://localhost:8000/currency-exchange/from/USD/to/INR

```java
package com.adi.microservices.controller;

import java.math.BigDecimal;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

import com.adi.microservices.bean.CurrencyExchange;

@RestController
public class CurrencyExchangeController {

	//http://localhost:8000/currency-exchange/from/USD/to/INR
	
	@GetMapping("/currency-exchange/from/{from}/to/{to}")
	public CurrencyExchange retriveExchangeValue(
								@PathVariable String from,
							    @PathVariable String to) {
		
		
		return new CurrencyExchange(1000L, from, to, BigDecimal.valueOf(50));
	}
	
}

```

```java
package com.adi.microservices.bean;
/*
 * Response Structure
{
   "id":10001,
   "from":"USD",
   "to":"INR",
   "conversionMultiple":65.00,
   "environment":"8000 instance-id"
}
 * */

import java.math.BigDecimal;

public class CurrencyExchange {

	private Long id;
	private String from;
	private String to;
	private BigDecimal conversionMultiple;
	public CurrencyExchange() {
		super();
		// TODO Auto-generated constructor stub
	}
	public CurrencyExchange(Long id, String from, String to, BigDecimal conversionMultiple) {
		super();
		this.id = id;
		this.from = from;
		this.to = to;
		this.conversionMultiple = conversionMultiple;
	}
	public Long getId() {
		return id;
	}
	public void setId(Long id) {
		this.id = id;
	}
	public String getFrom() {
		return from;
	}
	public void setFrom(String from) {
		this.from = from;
	}
	public String getTo() {
		return to;
	}
	public void setTo(String to) {
		this.to = to;
	}
	public BigDecimal getConversionMultiple() {
		return conversionMultiple;
	}
	public void setConversionMultiple(BigDecimal conversionMultiple) {
		this.conversionMultiple = conversionMultiple;
	}
	
}

```

![Alt text](image-586.png)

# 142 Step-12 Setting up the dynamic port in the response
![Alt text](image-587.png)

currency conversion microservice ko pata kaise chalenga ki currency exchnge ka konsa instance response provide kar raha hai.

Different port par instance honge.  
1. Add environment to identify the port also getter and setter
![Alt text](image-589.png)

2. Extract local variable and set port of environment.
![Alt text](image-588.png)
![Alt text](image-590.png)

3. How would i get value of port. Spring offer Environment 
![Alt text](image-591.png)

![Alt text](image-592.png)

### I want to launch this application on port 8001 as well i.e multiple instances
![Alt text](image-593.png)

![Alt text](image-594.png)

![Alt text](image-595.png)

![Alt text](image-596.png)

![Alt text](image-597.png)

![Alt text](image-598.png)

```java
package com.adi.microservices.bean;
/*
 * Response Structure
{
   "id":10001,
   "from":"USD",
   "to":"INR",
   "conversionMultiple":65.00,
   "environment":"8000 instance-id"
}
 * */

import java.math.BigDecimal;

public class CurrencyExchange {

	private Long id;
	private String from;
	private String to;
	private BigDecimal conversionMultiple;
	private String environment;
	
	public CurrencyExchange() {
		super();
		// TODO Auto-generated constructor stub
	}
	public CurrencyExchange(Long id, String from, String to, BigDecimal conversionMultiple) {
		super();
		this.id = id;
		this.from = from;
		this.to = to;
		this.conversionMultiple = conversionMultiple;
	}
	public Long getId() {
		return id;
	}
	public void setId(Long id) {
		this.id = id;
	}
	public String getFrom() {
		return from;
	}
	public void setFrom(String from) {
		this.from = from;
	}
	public String getTo() {
		return to;
	}
	public void setTo(String to) {
		this.to = to;
	}
	public BigDecimal getConversionMultiple() {
		return conversionMultiple;
	}
	public void setConversionMultiple(BigDecimal conversionMultiple) {
		this.conversionMultiple = conversionMultiple;
	}
	public String getEnvironment() {
		return environment;
	}
	public void setEnvironment(String environment) {
		this.environment = environment;
	}
	
}

```

```java
package com.adi.microservices.controller;

import java.math.BigDecimal;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.core.env.Environment;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

import com.adi.microservices.bean.CurrencyExchange;

@RestController
public class CurrencyExchangeController {
	
	// use core environment to fetch port value
	@Autowired
	private Environment environment;
	

	//http://localhost:8000/currency-exchange/from/USD/to/INR	
	@GetMapping("/currency-exchange/from/{from}/to/{to}")
	public CurrencyExchange retriveExchangeValue(
								@PathVariable String from,
							    @PathVariable String to) {
		
			
		
		CurrencyExchange currencyExchange = new CurrencyExchange(1000L, from, to, 
													BigDecimal.valueOf(50));
		
		String port = environment.getProperty("local.server.port");
		
		
		currencyExchange.setEnvironment(port);
		
		return currencyExchange;
	}
	
}

```

# 143 Step-13 Configure Jpa and Initialize Data

apne passs abhi hardcoded rest-api hai.. let's fetch some details from db.

hum yaha in-memory db use karenge ie. h2 and jpa use karenge to talk to the db.

![Alt text](image-599.png)

![Alt text](image-600.png)

A random in-memory db is created for us.
![Alt text](image-601.png)

![Alt text](image-602.png)

fire : localhost:8000/h2-console
![Alt text](image-603.png)

### 1. Let's create an entity. Once you define Spring Data JPa create table for us.
![Alt text](image-604.png)

![Alt text](image-605.png)

jdbc-Syntax-Error
![Alt text](image-606.png)

from is an sql keyword..
![Alt text](image-607.png)

![Alt text](image-608.png)

***Note:IN java camel case is used to separate words, while in db _ underscore is used***

### Insert data into it.
data.sql under resource folder
![Alt text](image-609.png)

abhi naye version of spring mein.. table create hone se pehle hi data load ho raha therefore.

```
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'dataSourceScriptDatabaseInitializer' defined in class path resource 

Failed to execute SQL script statement
```

![Alt text](image-610.png)

![Alt text](image-611.png)

 