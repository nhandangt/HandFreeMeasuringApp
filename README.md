
1	Introduction

Augmented Reality (AR) is a technology that improves the sensorial perception of a user by adding virtual objects directly to their surrounding environment. The modern AR platforms, such as smartphones and tablet computers, are moving the application fields of this technology from research labs to a wide range of application domains. The purpose of this project is to create a platform for rehabilitation engineers, which will help them measure an object and project it in a  3D space using AR technology. Since the design of an individual's surrounding plays a significant role in shaping their independence level, this application can be beneficial for rehabilitation engineers to design a customized environment that works for individuals with disabilities without coming into close proximity to the measure surfaces or touch any objects.  

In this quarter, we focused primarily on building the secured sign up and log in for the users who will use this measure-free application as a useful tools for them in their project. Furthermore, we have developed an iOS-based application that will store the measurement database based on user distinct database account. This function and dataframe will help each user write and read their own customer’s profiles that other users can not be accessed to. 

2	Review

AR is a technology that combines digital information with physical world using real-time computing methods. It provides users a real-time interactive experience while combining the virtual and real worlds. The rapid improvement of smartphones, tablet computers, video cameras, graphics processing capabilities, and wireless communication functions with which these so-called smart systems are equipped to have significantly improved AR technology's usability and practicality.

There are several AR applications that have been developed for smartphone platforms. For example, Milan Metro Augmented Reality [1] is a AR navigation application that guides the user to find underground stations using the phone camera. Another similar navigation application is Junaio Augmented Reality [2], which provides information about local events, offers, and listings by directly overlaid on the image captured by the smartphone camera. Other applications, such as Happy Measure [3], help the user with room planning for interior decoration and design. Using a marker placed on the object and the image captured by the smartphone camera, this application allows measuring the object's size. In this way, it helps in the creation of a 3D model of the object according to the previous measurements. IKEA’s AR catalog [4], which is also based on a similar concept, allows users to directly bring various types of virtual exhibits at home to match multiple furniture styles. It helps the user to do so without moving any of the furniture at home. These practical applications demonstrate that the use of AR technology has been gradually expanding from exhibitions and physical stores to personalized mobile experiences. 

3	Implementation

The purpose of creating the CARRT AR Measure application is to measure the dimensions of objects in real-time and save them to a database of each users. In this quarter, we have implemented the functionality of the sign up and log in for user using email and password autheticiation, and let the users to manage their own customer’s profile in a private mode.

3(a) Sign up and Log in Implementation

We started by creating the Users Interfaces (UI) which contanining: View Controller, Sign up View Controller, Log in View Controller.
-	The View Controller UI is for users to choose the option Sign up if they are new users, and Log in if they are existing user.
 
	Figure 1. The Home View Controller UI
-	Sign up View Controller UI is for users to sign up with their information to create a user’s profile such as: First Name, Last Name, Email, and Password.
	 
	Figure 2. The Sign up View Controller UI
-	Log in View Controller UI is for the users to log in into their existing account by entering correctly email and password.
 
	Figure 3. The Log in View Controller UI
Sign up process: 
-	We implemented the Swift code to set up the user account email and password. It is linked with Firebase so whenever the user register their account by email, Firebase will instantly create the user with a unique user UID for each user in Authenticiation of Firebase. After that, we implemented the function to read the user information and store it to Firestore to get more detailed user profile such as: first name, last name, user UID. 
 
Figure 4. The unique user UID is created in Firebase Authentiation after user registered 
 
Figure 5. How Firestore SQL database organize user profile
-	In this process, we implemented the SQL database by create the main collection “usersUID” which consisting all of documents (sub-collection of “usersUID”) and the document ID = user UID. By doing this, we can organize each user profile into a unique document which allow restricted access but not public access. This will be helpful for part 3(b) later on.
-	There is one more function was implemented which is the text field validating fucntion to make sure users do not leave any text field blank or forgot to fill out required informations.
-	The last function is to make sure the user’s password has met the requirement which are containing 8 characters, 1 special character, and numbers.
 
	Figure 7. Password Validating Function
 
Figure 8. Text Field Validating Function

Log in process:
-	When user already had an account, they will enter correct email and password. That information will be checked with the user authenticiation information on Firebase to let them in if it is correct user information. If the information is invalid, the user will see an error alert to let them know why and try again.
-	
3(b) Users and their Customers Database Implementation

Because the demand that each rehabilitation engineer need to store their own customer’s profile which just only them can see it, the SQL database management needs to be used to established the database. 

We implementation 4 UI for this process: Home View Controller, Add Customer View Controller, View Customer View Controller, Measure View Controller.
-	Home View Controller: if the user is signed up or logged in successfully, they can explore the main general functions of this application. They can choose add new customer profile or view their old customer’s profile.
 
Figure 9. Home View Controller
-	Add Customer View Controller: in this UI, the user can provide the Customer’s full name, and customer’s location. When they hit Save button, the information will be store on Firebase. And if storing successfully, they will be direct to Measure View Controller.
 
Figure 10. Add Customer View Controller UI
-	View Customer View Controller: in this UI, the user can see their own customer’s profile which is the customers of the current user logged in. 
-	Measure View Controller: After add new customer’s profile, they will be directed to this UI. They can choose 2 options: adding a separate measurement, or adding the whole floor plan
 
Figure 11. Measure View Controller

Data Management process: 
-	Each user will have a distinct user UID when they sign up at the first time. And all of their information, especially their customer’s profile will be store as fields in the document has document ID = user UID. Therefore, when accessing to show customer’s profile. The current logged in user just can access to the the document that has their user UID. 

4	Results

We tested in many input any case to check all the functions: sign up, log in, validating text field, validating password, log in with wrong password, saving customer’s profield and checking data base on Firebase how it was managed. The results of those tests are showed in the screen recording video.

5	Future work

In the third quarter, we will combine the current work with the LIDAR camera measure free function which was done in the first quarter. 

