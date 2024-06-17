# Secure-Programming-for-Application-Development with Code Analysis 
Comprehensive Guide to Secure Programming and Application Development with Code Analysis

# i)	Security Features – 
The security model of Java utilizes a method known as “Sandboxing” where the users are protected from any hostile programs being downloaded from an untrusted source within a network. As this technique allows all the Java programs to run within the same sandbox, only helping to prevent untrusted activities from any unknown sources. Unlike the other programming languages like C/C++, Java does not use any kind of pointers, as it already has its internal mechanism for managing its memory, giving access only to the verified authority over the data. Primitive being defined along with predefined size with all the operations defined according to the specific order of execution, providing the code being executed in other Java Virtual Machine would not have a different order of execution. Java compiler creates a class every time the user compiles a program in Java to deal with viruses and malicious files as the program is tested by a JVM at the time of execution. The access control functionality secures the program by avoiding any access to the objects that are critical from an untrusted code. 

# 2)	State of Art in security Testing- 
The security test of an application is critical regarding overcoming the vulnerabilities and uncovering all the bugs. Testing needs to be done so that the threats can be encountered, and the system doesn’t get exploited and doesn’t stop functioning. The vulnerabilities should be focused during the development phase of an application. Therefore, an application requires a Secure Software Development Lifecycle (SSDL) during the phase of application development and ever on various other phases.
  # a)	Secure Software Development Lifecycle (SSDL)- 
  It is the collection of the best practices mainly focused on adding security for the standard SDL. Hence, it follows all the steps same as SDL, but each step has been added concerning security measures.

  i)	<b>Phase 1: Requirements –</b>
   With security put into consideration the requirements for the new features are collected from different stakeholders. Security considerations are identified.
 
 ii)	<b>Phase 2: Design-</b> 
 This phase mainly focuses on transplanting requirements within the scope into a plan of what the application should look like. The functional requirements here generally describe what should happen while security  requirements generally focus on what should not.

 iii)	<b>Phase 3: Development-</b> 
 It is the phase where the implementation takes place, turning design into reality. These are some well-established secure coding guidelines an even code reviews that verifies that these guidelines have been 
 followed correctly. Some of the secure coding guidelines are as follows: 

(1)	Making use of the parameterized randomly SQL quires so that there are minimum chances of exploiting these queries

(2)	Validation of user inputs before processing the data contained within.

(3)	Vulnerabilities being checked in opensource libraries before its usage.

(4)	Sanitization of any data which is sent back from the database to the user.


iv)	<b>Phase 4: Verification-</b> 
In this phase the developed application is verified with security concerns where the application must go through various texting cycles to ensure it meets the original requirements and design. The verification phase may include:

(1)	Automated Tests
(2)	Automated Execution
(3)	Automated Deployment

v)	<b>Phase 5: Maintenance and Evolution-</b>
The vulnerabilities left behind which were undetected may be found and put into exploitation. Therefore, these vulnerabilities need to be patched.

  # b)	Threats regarding the standalone application
i)	Exposure of SQL queries and parameter of database- 
The database gets exposed as sometimes the application could be de compiled and in a few certain cases it could show the readable code. Just by exploiting this scenario an attacker could obtain the information related to the database parameters, configuration and SQL queries. This helps the attacker to perform various attacks like SQL injection and manipulation of data.

ii)	Leakage of data- 
Mobile based applications often have a high risk of data leakage of sensitive information from an application cached data stored, through third party application frameworks or from its main source code.

# 3)	Testing of the application – 
This section is for the testing of an application, whose source code is already provided to view and observe the functionality of an application whether it is running without any errors or not. The code will also be revised and tested manually to identify any flaw. If present, various tools would be used for the above experiment.

<b>a)	Using SonarLint: static code testing-</b> 
 The static analysis is done during the development stage of an application. The application may look like it works fine but internally might be insecure. Thus, static doe testing is needed, various other tools could be used to perform this task, but here SonarLint has been taken into consideration as for the given application code.

 ![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/15063da8-e36b-440b-bb99-d0dd0e6b3fd4)
                                
                                 Figure 1: Analysis of UserBook.java using SonarLint

 
 ![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/038c9455-be05-4254-abeb-4c00c84ead12)

                                 Figure 2: analysis of UserLogin.java using SonarLint

 <b>b)	Visual Code Grepper (VCG)-</b>
 Visual Code Grepper is an automated code security tool, mainly meant to serve the purpose of reviewing the code for the language like C/C++, Java, C#, PL/SQL, PHP and COBOL.

 ![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/a32bf61d-9db7-4448-8c7b-55daa54cd641)

                               Figure 3: Code analysis using VCG

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/0513d96e-f980-4e26-8abd-f5d349b4d7d7)

                              Figure 4: severity shown using VCG

<b> c)	Manual Code Review-  </b>

The following are the results of the test being performed: 
 
•)	UserLogin.java- Even after submitting the null characters into the database any user could login to the application without any authentication.

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/30466fb5-9c6e-4f97-8b44-5264477fd27e)

•)	UserForm.java- For creating a new user, even, the null values are being passed as there seems to be no input validation for the null characters for any user in the database.

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/78d98818-108c-43a6-9504-e6af3ff6c1e7)

                                    Figure 6: Lack of input validation, null values

•)	Plain texted passwords-  There is no hashing done on to the password making it more vulnerable. There is no encryption.

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/b3d6d8a6-cd21-4de8-b049-32fb62608ad3)

                                  Figure 7: Passwords stored as plain text in the database

•)	Sensitive data stored as plaintext in the source code- Passwords in the database were stored as plaintext in the source code, also making it easy for the attacker to exploit.

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/be5fe31f-929f-4cd2-b3c4-1aba51b61c9b)

                                  Figure 8: Password stored as plaintext in the source code

# 4)	Proposed solution to the security issues encountered

<b> a)	Mitigating attacks like SQL injection- </b>

Attacks like SQL injection can be mitigated using some prepared statements. By implementing prepared statements through good coding practices, it convinces the developer to write the command of SQL and the user-provided data distinctively. Through this process the SQL command is executed securely which further prevents SQL injection vulnerabilities.

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/602bf80d-7838-4f44-a0ea-28a488c516ff)

                                      Figure 9: Implementation of prepared statements

<b> b)	Input validation for the username and passwords- </b>
There should be a process of input validation while the time any user or new user logs in the application. Regular Expressions could be implemented and utilized for username and password validation for both the user and the librarian, eliminating all the null values. For example: 
                              
                              String regex =  ((?=.*[a-z])(?=.*d)(?=.*[@#$%])(?=.*[A-Z]).{6,16})
                              Password . getText () . Matches(regex) 

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/f2f83877-f045-4f05-9baa-81d2c3b8dcf7)

                                      Figure 10: Input validation for Password using regex


<b> c)	Password encryption – </b>

The password should be hashed and well encrypted as when ever the user signs up for an account and choose a password, the password is stored as the generated block of hash. Various hashing mechanisms should be used such as BCrypt, SCrypt, SHA256, SHA512 and PBKD2. For instance: 

![image](https://github.com/Shresoc/Secure-Programming-for-Application-Development/assets/168186856/49914fb0-0da6-454e-bbf7-b3525e40f718)

                                                   Figure 11: Using SHA-256 for Hashing


# Summary: 
Application development is a daunting task, how sad it would be if some other body which is unauthorize breaches the application successfully and exploits the sensitive data. Therefore, during and after the development of the application, security should remain the critical aspect throughout the process. The architecture and the framework should be known to the developer by following SSDL cycles regarding the security. Even more, various tools like the Visual Code Grepper and SonarLint should be in use to analyze the source code and its flaws.




                  




