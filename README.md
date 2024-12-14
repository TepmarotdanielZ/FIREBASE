## I. ESP32 GETTING STARTED WITH FIREBASE (REAL TIME DATABASE)

This guide will get you started quickly with Firebase using the ESP32 board. Firebase is Google’s mobile application development platform that includes many services to manage data from IOS, Android, or web applications. You’ll create a Firebase project with a realtime database (RTDB), and you’ll learn how to store and read values from the database with your ESP32.


![TEST_1](https://github.com/user-attachments/assets/1acb2162-ccf9-4aaf-a111-f5c1f19a525d)


In a later tutorial, you’ll learn how to create a Firebase web app that you can access from anywhere to monitor and control your ESP32 using Firebase’s real-time database:

## 1. WHAT IS FIREBASE?


<div align="center">  
    <img src="https://github.com/user-attachments/assets/4586ddc4-6f7f-47ed-aa09-de0106e87a92" alt="Description of the image" />  
</div>

<p align="center">  
    <img src="https://github.com/user-attachments/assets/4586ddc4-6f7f-47ed-aa09-de0106e87a92" alt="Description of the image" style="max-width: 100%; height: auto;" />  
</p>


Firebase is Google’s mobile application development platform that helps you build, improve, and grow your app. It has many services used to manage data from any Android, IOS, or web application.

The following paragraph clearly explains the advantages of using Firebase:

“Firebase is a toolset to “build, improve, and grow your app”, and the tools it gives you cover a large portion of the services that developers would normally have to build themselves but don’t really want to build because they’d rather be focusing on the app experience itself. This includes things like analytics, authentication, databases, configuration, file storage, push messaging, and the list goes on. The services are hosted in the cloud and scale with little to no effort on the part of the developer.”

This paragraph was taken from  [this article](https://medium.com/firebase-developers/what-is-firebase-the-complete-story-abridged-bcc730c5f2c0), and we recommend that you read that article if you want to understand better what firebase is and what it allows you to do.

You can use the ESP32 to connect and interact with your Firebase project, and you can create applications to control the ESP32 via Firebase from anywhere in the world.

In this tutorial, we’ll create a Firebase project with a realtime database, and we’ll use the ESP32 to store and read data from the database. The ESP32 can interact with the database from anywhere in the world as long as it is connected to the internet.

This means that you can have two ESP32 boards in different networks, with one board storing data and the other board reading the most recent data, for example.


<div align="center">  
    <img src="https://github.com/user-attachments/assets/71291ecb-2c26-4703-87c9-4ba12bdcf0fd" alt="Image" />  
</div> 

In a later tutorial, we’ll create a web app using Firebase that will control the ESP32 to display sensor readings or control outputs from anywhere in the world.


<div align="center">  
    <img src="https://github.com/user-attachments/assets/3f925731-4034-478b-ada4-79c7e037489c" alt="Image" />  
</div>



## 2. PROJECT OVERVIEW

In this tutorial, you’ll learn how to create a Firebase project with a realtime database and store and read data from the database using the ESP32.

To follow this project, first, you need to set up a Firebase project and create a realtime database for that project. Then, you’ll program the ESP32 to store and read data from the database. This tutorial is divided into three sections.

   **1. Create a Firebase Project**
   
   **2. ESP32: Store data to the Firebase Realtime Database**
   
   **3. ESP32: Read data from the Firebase Realtime Database**

Let’s get started!

## II. SET UP A FIREBASE ACCOUNT AND CREATE A NEW PROJECT
## 1. CREATE A NEW PROJECT

Follow the next instructions to create a new project on Firebase.

**1.** Go to [Firebase](https://firebase.google.com/) and sign in using a Google Account.

**2.** Click Get Started, and then Add project to create a new project.

**3.** Give a name to your project, for example: `FIREBASE`.

![FIREBASE](https://github.com/user-attachments/assets/5109d5f6-9ba4-46da-b2d8-9bf9a333ae9a)

**4.** Disable the option Enable Google Analytics for this project as it is not needed and click Create project.

![FIREBASE (1)](https://github.com/user-attachments/assets/526420ba-19c7-4b5a-b19d-222a12aaa2a0)

**5.** It will take a few seconds setting up your project. Then, click Continue when it’s ready.

![FIREBASE (2)](https://github.com/user-attachments/assets/0bdbcb7a-491d-4fa1-a8b8-984dca093435)

**6.** You’ll be redirected to your Project console page.

![image](https://github.com/user-attachments/assets/aad30efb-2c59-4729-aad5-ac69ec7ddeb2)


## 2. SET AUTHENTICATION METHODS

You need to set authentication methods for your app.

“Most apps need to know the identity of a user. In other words, it takes care of logging in and identify the users (in this case, the ESP32). Knowing a user’s identity allows an app to securely save user data in the cloud and provide the same personalized experience across all of the user’s devices.” To learn more about the authentication methods, you can [read the documentation](https://firebase.google.com/docs/auth).

**1.** On the left sidebar, click on **Authentication** and then on **Get started**.

![FIREBASE (3)](https://github.com/user-attachments/assets/5e6d0885-1d75-4f2c-92fb-6bdb5a62b97d)

**2.** There are several authentication methods like email and password, Google Account, Facebook account,

![image](https://github.com/user-attachments/assets/0fb000e6-90e2-410c-a7b9-5b72ad410a95)

and others.

**3.** For testing purposes, we can select the Anonymous user (require authentication without requiring users to sign in first by creating temporary anonymous accounts). Enable that option and click **Save**.

![FIREBASE (4)](https://github.com/user-attachments/assets/8e9fc7a1-1009-43ab-8e9a-dd0e6dd51302)

![FIREBASE (5)](https://github.com/user-attachments/assets/f80794c4-125e-455c-91b7-2a5fb0a8a4b6)

**4.** **"Add user"**

**Purpose:**

 * The button allows you to manually create new user accounts directly in your Firebase project. This can be useful for adding test users, customer support accounts, or any other users you want to manage without needing them to sign up through an app interface.

**User Creation Process:**

 * Clicking this button typically opens a form where you can enter user details, such as their email address and password.
 * You might also have options to set other attributes, like whether the account should be enabled or if there are any additional claims.

**Managements:**

 * Once a user is added through this method, they will appear in the user list below with details such as their identifier (like email), the provider of their authentication (email/password), the time of account creation, and whether they are currently signed in.

**Use Cases:**

 * Ideal for application administrators or developers who need to set up accounts for testing purposes without requiring users to sign up through the normal registration flow.

![FIREBASE (16)](https://github.com/user-attachments/assets/b1e35f59-6945-4071-a667-57f11cf701b5)


**5.** **"Add an Email/Password user"** : This section is specifically designed for adding new users to your Firebase Authentication system using email and password credentials. Here’s a breakdown of its components:

**Components of the Red Box:**

**1. Email Input Field:**

 * This field is where you enter the user's email address. It’s a required field for creating a new user account.
 * Validating the email format is usually enforced to ensure that the input is a correct email address.

**2. Password Input Field:**

 * This field is for the user's password. It must meet any password requirements you have (such as length or complexity).
 * Users should choose a strong password to enhance security.

**3. Add User Button:**

 * Once the email and password are entered, clicking this button will create the user account in Firebase.
 * If the email is already registered or if any other input errors occur, Firebase will provide an error message.

**4. Cancel Button:**

 * This button allows you to dismiss the user creation window without adding a user.

**Purpose:**

**The primary function of this section is to facilitate the manual addition of user accounts to your Firebase project. This is particularly useful for:**

* Administrators who need to create accounts for users without requiring them to use the front-end app.
* Testing purposes, where developers want to quickly add test users

![FIREBASE (17)](https://github.com/user-attachments/assets/5c8eb977-5b3f-4d5b-8a29-247d6c8939df)

**6.** **"Sign-in providers"** : section within the Firebase Authentication settings, specifically focusing on email/password authentication. Here’s a breakdown of its components and purpose:

**Components:**

**1. Components:**

 * This section allows you to manage different authentication methods that your application can use for users to sign in.

**2. Provider:**

 * Under this header, the current authentication methods are listed. In this case, it shows "`Email/Password`" as one of the available sign-in providers.
 * You have the option to enable or configure additional sign-in methods if needed, such as Google, Facebook, or Twitter.

**3. Status Indicator:**

 * Next to "`Email/Password,`" there’s a status indicator (a green checkmark here), which shows that this authentication method is currently enabled. This means users can register and sign in using their email and password.

**4. Add New Provider Button:**

 * This button allows you to add additional sign-in methods to your Firebase project. Clicking this will prompt you to select from various authentication providers supported by Firebase.

**Purpose:**

 * The "`Sign-in providers`" section is crucial for configuring how users will authenticate themselves in your application.
 * By managing this section, developers can:
    * Enable or disable authentication methods based on the needs of their application.
    * Ensure that user accounts can be created securely and that users can log in easily.
  
![FIREBASE (18)](https://github.com/user-attachments/assets/71574826-bb0e-4544-965c-ed49abd5cba4)


## 3. CREATING A REAL-TIME DATABASE

The next step is creating a Realtime Database for your project. Follow the next steps to create the database.

**1.** On the left sidebar click on **Realtime Database** and then, click on **Create Database**.

![FIREBASE (6)](https://github.com/user-attachments/assets/33ca9b2e-1e5c-413d-8b02-b5bb305fa441)

**2.** Select your database location. It should be the closest to your location.

![FIREBASE (8)](https://github.com/user-attachments/assets/f55023c6-430a-4f36-a623-7b17660ad5cb)

**3.** Set up security rules for your database. For testing purposes, select **Start in test mode**. In later tutorials you’ll learn how to secure your database using database rules.

![FIREBASE (9)](https://github.com/user-attachments/assets/fac08d98-5eec-4877-aa7e-897076774304)

**4.** Your database is now created. You need to copy and save the database URL—highlighted in the following image—because you’ll need it later in your ESP32 code.

![FIREBASE (10)](https://github.com/user-attachments/assets/cacd89e6-f66b-4e1b-9905-35360efeadc6)

The Realtime Database is all set. Now, you also need to get your project API key.

## 4. GET THE PROJECT API KEY

**1.** To get your project’s API key, on the left sidebar click on **Project Settings**.

![FIREBASE (11)](https://github.com/user-attachments/assets/e8c26ca5-cbe8-495b-b4ee-b33af45888f2)

**2.** Copy the API Key to a safe place because you’ll need it later.

![FIREBASE (12)](https://github.com/user-attachments/assets/21dabf76-0574-43aa-bfae-3acf8ee46e4c)

Now, you have everything ready to interface the ESP32 with the database.

## 5. SETUP RULES

The `Rules` section of the Firebase Realtime Database. Here’s a breakdown of what this section entails and its purpose:

**Components:**

 **1. Rules Structure:**

 * The rules defined in this section dictate how data can be accessed and modified within your Realtime Database. They are written in a JSON-like syntax.

 **2. Root Object:**

 * The outer curly braces `{}` encapsulate the entire set of rules. This is where you define various rules and conditions.

 **3. UserData Path:**

 * The `"UserData"` key indicates that these rules are intended for a specific path in your database where user-related data is stored. This organizes the rules based on the functionality of the stored data.

 **4. Dynamic User ID (`$uid`) Placeholder:**

 * The `"$uid"` placeholder is a dynamic variable that represents the unique identifier for each user. This means the rules can apply to multiple users based on their unique IDs.

 **5. Read and Write Permissions:**

 * Under each user’s ID (specifically `"$uid"`), the `.read` and `.write` keys define the permissions:
   * `".read": "$uid === auth.uid"`: This rule allows reading data only if the user’s ID matches the authenticated user's ID. In other words, a user can read their own data.
   * `".write": "$uid === auth.uid"`: Similarly, this rule allows writing data only if the user’s ID matches the authenticated user's ID, meaning they can only modify their own data.
  
**Purpose:**

 **1. Data Security:**

 * These rules are crucial for securing your database. By allowing users to access only their own data, you prevent unauthorized access and modifications by other users.

 **2. User-Level Data Management:**

 * The structure enables users to store private data without risking exposure to other users of the application.

![FIREBASE (19)](https://github.com/user-attachments/assets/4b3d8919-273b-4d32-b5be-138ee4354288)

 **6. JSON:**

```json
{
    "rules": {
        "UsersData": {
            "$uid": {
                ".read": "$uid === auth.uid",
                ".write": "$uid === auth.uid"
            }
        }
    }
}
```

The JSON structure you've provided outlines the rules for accessing the **`UsersData`** path in a Firebase Realtime Database. Below, I’ll explain the different components of the structure, ensuring clarity regarding its purpose and function.

**JSON Structure Breakdown:**

 **1. Outer Object (`rules`):**

 * The outermost curly braces `{}` create the root object for your rules. This is where all the database access rules are defined.

 **2. Path to Specific Data (`UsersData`):**

 * The `"UsersData"` key designates a specific path in the database where user-related data will be stored.

 **3. Dynamic User ID (`$uid`):**

 * `"$uid"` is a placeholder that represents individual user IDs. This allows the rules to apply dynamically based on the ID of the user interacting with the database.

 **4. Read Permission (`.read`):**

 * The rule `.read: "$uid === auth.uid"` means that a user can read the data at the path corresponding to their unique user ID only if that user's ID matches the ID of the authenticated user `(auth.uid)`.
 * This ensures that users can only access their own data, which enhances security and privacy.

 **5. Write Permission (`.write`):**

 * Similarly, the rule `.write: "$uid === auth.uid"` restricts write access to the data at that path. Users can only write (or modify) data if their user ID matches auth.uid, ensuring they can only edit their own information.
   
## III. PROGRAM THE ESP32 TO INTERFACE WITH FIREBASE

Now that the Firebase Realtime Database is created, you’ll learn how to interface the ESP32 with the database.

To program the ESP32, you can use [Arduino IDE](https://randomnerdtutorials.com/installing-the-esp32-board-in-arduino-ide-windows-instructions/), [VS Code with the PlatformIO extension](https://randomnerdtutorials.com/vs-code-platformio-ide-esp32-esp8266-arduino/), or other suitable software.

> [!NOTE]  
> for firebase projects, we recommend using VS Code with the PlatformIO extension because if you want to develop a web application to make the bridge between the ESP32 and Firebase, VS Code provides all the tools to do that. However, we won’t build the web application in this tutorial, so you can use Arduino IDE.

## 1. INSTALL THE FIREBASE ESP CLIENT LIBRARY

There is a library with lots of examples to use Firebase with the ESP32: the [Firebase-ESP-Client library](https://github.com/mobizt/Firebase-ESP-Client). This library is compatible with both the ESP32 and ESP8266 boards.

In this tutorial, we’ll look at simple examples to store and read data from the database. The library provides many other examples that you can check [here](https://github.com/mobizt/Firebase-ESP-Client/blob/main/src/core/FirebaseCore.cpp). It also provides detailed documentation explaining how to use the library.

## 2. INSTALLATION VS CODE AND PLATFORM IO

If you’re using VS Code with the PlatformIO extension, click on the **PIO Home** icon and then select the **Libraries tab**. Search for **“Firebase ESP Client“**. Select the **Firebase Arduino Client Library for ESP8266 and ESP32**.

![FIREBASE (13)](https://github.com/user-attachments/assets/71132c0e-410a-4b24-bc1a-405d03a1b438)

Then, click **Add to Project** and select the project you’re working on.

![FIREBASE (14)](https://github.com/user-attachments/assets/8b225155-ac91-47af-a48e-3258237bf3b5)

![image](https://github.com/user-attachments/assets/12a97fca-8b4e-476e-86f1-6ae73eab5543)


Also, change the monitor speed to 115200 by adding the following line to the `platformio.ini` file of your project:

```cpp
monitor_speed = 115200
```

## 2. INSTALLATION ARDUINO IDE

If you’re using Arduino IDE, follow the next steps to install the library.

**1.** Go to **Sketch** > **Include Library** > **Manage Libraries**

**2.** Search for Firebase ESP Client and install the Firebase Arduino Client Library for ESP8266 and ESP32 by Mobitz.


> [!NOTE]  
> We are using version 4.4.14. If you have issues compiling your code with more recent versions of the library, downgrade to version 4.4.14..


![FIREBASE (15)](https://github.com/user-attachments/assets/7eac0508-5bf6-4ec2-9ee0-1d760a548682)

Now, you’re all set to start programming the ESP32 board to interact with the database.

## 3. ESP32 STORE DATA TO FIREBASE

<div align="center">  
    <img src="https://github.com/user-attachments/assets/aef87599-34cd-43ca-ac34-0bde6df5d4fa" alt="Image" />  
</div> 

Copy the following code to your Arduino IDE. This sketch inserts an int and a float number into the database every 15 seconds. This is a simple example showing you how to connect the ESP32 to the database and store data. [This is also compatible with ESP8266 boards](https://randomnerdtutorials.com/esp8266-nodemcu-firebase-realtime-database/).


> [!NOTE]  
> We are using version 4.4.14 of the Firebase ESP Client library. If you have issues compiling your code with more recent versions of the library, downgrade to version 4.4.14.


**FULL CODE**

```cpp

#include <Arduino.h>  
#if defined(ESP32)  
  #include <WiFi.h>  
#elif defined(ESP8266)  
  #include <ESP8266WiFi.h>  
#endif  
#include <Firebase_ESP_Client.h>  
#include <Wire.h>  
#include <Adafruit_Sensor.h>

/* PROVIDE THE TOKEN GENERATION PROCESS INFO. */ 
  #include "addons/TokenHelper.h"  
  
/* PROVIDE THE RTDB PAYLOAD PRINTING INFO AND OTHER HELPER FUNCTIONS. */   
  #include "addons/RTDBHelper.h"  

/* INSERT YOUR NETWORK CREDENTIALS */ 
  #define WIFI_SSID "REPLACE_WITH_YOUR_SSID"  
  #define WIFI_PASSWORD "REPLACE_WITH_YOUR_PASSWORD"  

/* INSERT FIREBASE PROJECT API KEY   */ 
  #define API_KEY "REPLACE_WITH_YOUR_PROJECT_API_KEY"  

/* INSERT RTDB URL */   
  #define DATABASE_URL "REPLACE_WITH_YOUR_DATABASE_URL"  

/* DEFINE USER CREDENTIALS */ 
  #define USER_EMAIL "REPLACE_WITH_THE_USER_EMAIL"  /* REPLACE WITH YOUR FIREBASE USER EMAIL */   
  #define USER_PASSWORD "REPLACE_WITH_THE_USER_PASSWORD" /* REPLACE WITH YOUR FIREBASE USER PASSWORD */   

/* DEFINE FIREBASE OBJECTS */  
  FirebaseData fbdo;  
  FirebaseAuth auth;  
  FirebaseConfig config;  

/* VARIABLE TO SAVE USER UID */   
  String uid;  

/* VARIABLES TO SAVE DATABASE PATHS */ 
  String databasePath;  
  String tempPath;  
  String humPath;  
  String presPath;  

/* BME280 SENSOR */   
/* ADAFRUIT_BME280 BME; I2C */   
  float temperature;  
  float humidity;  
  float pressure;  
  float contador = 1.0;  

/* TIMER VARIABLES (SEND NEW READINGS EVERY FIVE SECONDS) */  
  unsigned long sendDataPrevMillis = 0;  
  unsigned long timerDelay = 5000;  

/* INITIALIZE WIFI */  
void initWiFi() {  
  WiFi.begin(WIFI_SSID, WIFI_PASSWORD);  
  Serial.print("Connecting to WiFi ..");  
  while (WiFi.status() != WL_CONNECTED) {  
    Serial.print('.');  
    delay(1000);  
  }  
  Serial.println(WiFi.localIP());  
  Serial.println();  
}  

/* WRITE FLOAT VALUES TO THE DATABASE */ 
void sendFloat(String path, float value) {  
  if (Firebase.RTDB.setFloat(&fbdo, path.c_str(), value)) {  
    Serial.print("Writing value: ");  
    Serial.print(value);  
    Serial.print(" on the following path: ");  
    Serial.println(path);  
    Serial.println("PASSED");  
    Serial.println("PATH: " + fbdo.dataPath());  
    Serial.println("TYPE: " + fbdo.dataType());  
  } else {  
    Serial.println("FAILED");  
    Serial.println("REASON: " + fbdo.errorReason());  
  }  
}  

void setup() {  
  Serial.begin(115200);  
  initWiFi();  

  /* ASSIGN THE API KEY (REQUIRED) */   
    config.api_key = API_KEY;  

  /* ASSIGN THE USER SIGN IN CREDENTIALS */ 
    auth.user.email = USER_EMAIL;  
    auth.user.password = USER_PASSWORD;  

  /* ASSIGN THE RTDB URL (REQUIRED) */ 
    config.database_url = DATABASE_URL;  

    Firebase.reconnectWiFi(true);  
    fbdo.setResponseSize(4096);  

  /* ASSIGN THE CALLBACK FUNCTION FOR THE LONG RUNNING TOKEN GENERATION TASK */ 
    config.token_status_callback = tokenStatusCallback; /*SEE ADDONS/TOKENHELPER.H */ 

  /* ASSIGN THE MAXIMUM RETRY OF TOKEN GENERATION */ 
    config.max_token_generation_retry = 5;  

  /* INITIALIZE THE LIBRARY WITH THE FIREBASE AUTHEN AND CONFIG */  
    Firebase.begin(&config, &auth);  

  /* GETTING THE USER UID MIGHT TAKE A FEW SECONDS */  
    Serial.println("Getting User UID");  
    while ((auth.token.uid) == "") {  
      Serial.print('.');  
      delay(1000);  
    }  

  /*PRINT USER UID */   
    uid = auth.token.uid.c_str();  
    Serial.print("User UID: ");  
    Serial.println(uid);  

  /* UPDATE DATABASE PATH */ 
    databasePath = "/UsersData/" + uid;  

  /* UPDATE DATABASE PATH FOR SENSOR READINGS  */   
    tempPath = databasePath + "/temperature"; /* --> USERSDATA/<USER_UID>/TEMPERATURE */ 
    humPath = databasePath + "/humidity";     /* --> USERSDATA/<USER_UID>/HUMIDITY */ 
    presPath = databasePath + "/pressure";    /* --> USERSDATA/<USER_UID>/PRESSURE */ 
}  

void loop() {  
  /* SEND NEW READINGS TO DATABASE */   
    if (Firebase.ready() && (millis() - sendDataPrevMillis > timerDelay || sendDataPrevMillis == 0)) {  
      sendDataPrevMillis = millis();  

    /* SIMULATED SENSOR READINGS FOR TESTING */ 
      if (contador > 20) { contador = 1.0; }  
      contador = contador + 1;  
      temperature = contador * 0.1;  
      humidity = contador * 0.2;  
      pressure = contador * 0.3;  

    /* SEND READINGS TO DATABASE */   
      sendFloat(tempPath, temperature);  
      sendFloat(humPath, humidity);  
      sendFloat(presPath, pressure);  
  }  
}

```
You need to insert your network credentials, URL database, and project API key for the project to work.

This sketch was based on the basic example provided by the library. You can find more examples here.

## 4. HOW TO CODE WORK

  **1. Include Libraries:**

```cpp
#include <Arduino.h>  
#if defined(ESP32)  
  #include <WiFi.h>  
#elif defined(ESP8266)  
  #include <ESP8266WiFi.h>  
#endif  
#include <Firebase_ESP_Client.h>  
#include <Wire.h>  
#include <Adafruit_Sensor.h>
```

* This section includes necessary libraries. Depending on whether you are using an ESP32 or ESP8266, it includes the appropriate Wi-Fi library. It also includes Firebase and sensor libraries.

  **2. Firebase and Wi-Fi Configuration:**

```cpp
#define WIFI_SSID "REPLACE_WITH_YOUR_SSID"  
#define WIFI_PASSWORD "REPLACE_WITH_YOUR_PASSWORD"  
#define API_KEY "REPLACE_WITH_YOUR_PROJECT_API_KEY"  
#define DATABASE_URL "REPLACE_WITH_YOUR_DATABASE_URL"  
#define USER_EMAIL "REPLACE_WITH_THE_USER_EMAIL"  
#define USER_PASSWORD "REPLACE_WITH_THE_USER_PASSWORD"
```

* Replace these placeholders with your actual Wi-Fi credentials, Firebase API key, database URL, and user credentials. These are necessary for connecting to Wi-Fi and authenticating with Firebase.

  **3. Firebase Objects and Variables:**

```cpp
FirebaseData fbdo;  
FirebaseAuth auth;  
FirebaseConfig config;  
String uid;  
String databasePath;  
String tempPath;  
String humPath;  
String presPath;
```
* Here, we define objects for Firebase operations and variables to store user IDs and database paths for sensor data.

  **4. Sensor Initialization:**

```cpp
float temperature;  
float humidity;  
float pressure;  
float contador = 1.0;
```

* These variables will hold the simulated sensor readings. `contador` is a counter used to simulate changing sensor values.

  **5. Timer Variables:**

```cpp
unsigned long sendDataPrevMillis = 0;  
unsigned long timerDelay = 5000;
```

* `sendDataPrevMillis` tracks the last time data was sent, and `timerDelay` sets the interval for sending data (5 seconds).

  **6. Wi-Fi Initialization Function:**

  
```cpp
void initWiFi() {  
  WiFi.begin(WIFI_SSID, WIFI_PASSWORD);  
  Serial.print("Connecting to WiFi ..");  
  while (WiFi.status() != WL_CONNECTED) {  
    Serial.print('.');  
    delay(1000);  
  }  
  Serial.println(WiFi.localIP());  
  Serial.println();  
}
```

* This function connects the microcontroller to the specified Wi-Fi network and waits until the connection is established. It prints the local IP address once connected

  **7. Sending Float Values to Firebase:**

 ```cpp
    void sendFloat(String path, float value) {  
      if (Firebase.RTDB.setFloat(&fbdo, path.c_str(), value)) {  
        Serial.print("Writing value: ");  
        Serial.print(value);  
        Serial.print(" on the following path: ");  
        Serial.println(path);  
        Serial.println("PASSED");  
        Serial.println("PATH: " + fbdo.dataPath());  
        Serial.println("TYPE: " + fbdo.dataType());  
      } else {  
        Serial.println("FAILED");  
        Serial.println("REASON: " + fbdo.errorReason());  
      }  
    }
```

* This function sends a float value to a specified path in the Firebase Realtime Database. It checks if the write operation was successful and prints the result.


  **8. Setup Function:**

```cpp
void setup() {  
  Serial.begin(115200);  
  initWiFi();  

  config.api_key = API_KEY;  
  auth.user.email = USER_EMAIL;  
  auth.user.password = USER_PASSWORD;  
  config.database_url = DATABASE_URL;  

  Firebase.reconnectWiFi(true);  
  fbdo.setResponseSize(4096);  
  config.token_status_callback = tokenStatusCallback;  
  config.max_token_generation_retry = 5;  
  Firebase.begin(&config, &auth);  

  Serial.println("Getting User UID");  
  while ((auth.token.uid) == "") {  
    Serial.print('.');  
    delay(1000);  
  }  
  uid = auth.token.uid.c_str();  
  Serial.print("User UID: ");  
  Serial.println(uid);  

  databasePath = "/UsersData/" + uid;  
  tempPath = databasePath + "/temperature";  
  humPath = databasePath + "/humidity";  
  presPath = databasePath + "/pressure";  
}
```

* In the `setup()` function, the serial communication is initialized, Wi-Fi is connected, and Firebase is configured with the provided credentials. It retrieves the user UID, which is used to construct database paths for storing sensor data.


  **9. Main Loop**

```cpp
void loop() {  
  if (Firebase.ready() && (millis() - sendDataPrevMillis > timerDelay || sendDataPrevMillis == 0)) {  
    sendDataPrevMillis = millis();  

    if (contador > 20) { contador = 1.0; }  
    contador = contador + 1;  
    temperature = contador * 0.1;  
    humidity = contador * 0.2;  
    pressure = contador * 0.3;  

    sendFloat(tempPath, temperature);  
    sendFloat(humPath, humidity);  
    sendFloat(presPath, pressure);  
  }  
}
```

* The `loop()` function checks if Firebase is ready and if it's time to send new sensor readings (every 5 seconds). It simulates sensor values based on the `contador` variable and sends these values to the Firebase database using the `sendFloat()` function


> [!Summary]  
> This code connects to Wi-Fi, authenticates a user with Firebase, and periodically sends simulated temperature, humidity, and pressure data to a Firebase Realtime Database. You would need to replace the placeholder strings with actual credentials and database information to use it effectively. If you have any specific questions or need further clarification on any part, feel free to ask!


## IV. RESULT
## 1. ARDUINO IDE TESTING

![FIREBASE (20)](https://github.com/user-attachments/assets/a429d72c-6746-425a-b737-882916952f91)

The output you shared appears to be from an Arduino IDE Serial Monitor, where your ESP32 is communicating with Firebase. Here’s a breakdown of what each part means:

**1. Token Info:**

 * **Type:** This indicates that the token being used is of the type “id token,” specifically a GITKit token, which is typically used for user authentication.
 * **Status:** "ready" means that the ESP32 has successfully authenticated and is ready to send and receive data.

**2. Getting User UID:**

 * The ESP32 retrieves a unique identifier (UID) for the user, which is indicated as `t5MPpjfbTcNXaGzG315w02H4Sf2`. This UID is crucial for structuring data in your database.

**3. Writing Values:**

 * The program is writing sensor data (temperature, humidity, and pressure) to Firebase database paths that include the user UID.
 * For example:
   * **Temperature:** Writing `0.20` to `/UsersData/t5MPpjfbTcNXaGzG315w02H4Sf2/temperature`.
   * **Humidity:** Writing `0.40` to `/UsersData/t5MPpjfbTcNXaGzG315w02H4Sf2/humidity`.
   * **Pressure:** Writing `0.60` to `/UsersData/t5MPpjfbTcNXaGzG315w02H4Sf2/pressure`.
* This indicates that the ESP32 is successfully sending sensor readings to specific paths in the Firebase database.

**4. Data Types:**

 * Each reading is confirmed to be of type `float`, indicating that the data values (temperature, humidity, pressure) are decimal numbers.

 **5. Result Confirmation:**

 * The **"PASSED"** messages indicate that the data was successfully written to the specified paths without issues.

 ## 2. FIREBASE

 ![FIREBASE (21)](https://github.com/user-attachments/assets/8dae6971-608e-4807-9951-22bc8849373f)

In the Firebase Realtime Database, the displayed data provides a structured view of the sensor readings associated with a specific user. Here's a breakdown of the elements in the image:
 
**1. Database Path:**

 * The path shown is: `https://fir-79ca6-default-rtdb.asia-southeast1.firebasedatabase.app/UsersData/t5MPpjfbTcNXaGzG315w02H4Sf2/`
 * This path indicates that the data belongs to a user with the unique ID `t5MPpjfbTcNXaGzG315w02H4Sf2`, which is utilized to keep user-specific data organized.

**2. User Data Structure:**

 * Under the `UsersData` node, each user has their sub-node identified by their UID, and within this sub-node, there are three data points:
   * **Humidity:** A float value of `3.2`. This represents the current humidity percentage recorded by your sensors.
   * **Pressure:** A float value of `4.8`. This indicates the atmospheric pressure sensed by your device.
   * **Temperature:** A float value of `1.6`. This is the temperature reading from the sensor.
  
**3. Data Interpretation:**

 * Each of these readings represents real-time sensor data related to environmental conditions. The values are organized under the user's unique identifier, making it easier to query or update specific user-related data.

**4. Real-Time Updates:**

 * The Realtime Database allows for live synchronization, so any change made to these values from the ESP32 will be instantly reflected here in the Firebase console and vice versa.

## V. RESULT ARDUINO COMMUNICATION TO FIREBASE

![FIREBASE (22)](https://github.com/user-attachments/assets/f09b8998-52dc-457f-912e-245210a77a3b)
