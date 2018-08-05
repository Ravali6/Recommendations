# Movie Recommendation system
The purpose of our project is to use machine learning to provide tailored movie selections based on user preferences. We propose to deliver an interactive environment by using an SQL database and a Python machine learning classifier (most likely a random forest) to make recommendations based on user-based criteria from an HTML front-end.
Statement of Proposal: We propose to utilize machine learning through a front-end, user based application - a web site - to recommend movies based on the user’s preferences.
Scope and Objectives
Our main goals are follows in the order of importance.
Using data from the user to trigger the dataset available for the movies to make recommendation.
Provide a list of movies according to the different choices made by the user using genre, IMDB score, etc.
Provide a clean and logical UI. 
We will implement content based recommendation first.
After implementing the content based recommendation, we will go for a hybrid of content based recommendation and a more modern approach

Supplementary Requirements
1.2.1 Extensibility
Instead of using a traditional content based recommendation system, project can be extended to the following modern approaches:
Collaborative Filtering: The idea of collaborative filtering is in finding the users in a community that share appreciations.
Context-aware Approach: Context is the information about the environment of a user and the details of the situation he/she is in. By paying attention and utilize such information in giving the recommendations is called Context-aware approach.
Semantic-based Approach: Using a text mining method to create a knowledge base through the user search and likes/dislikes. 
Cross-domain Approach: Creating the local neighbourhoods for each user according to domains and computing similarities to make predictions and recommendations.
Cross-lingual Approach: Users receive recommendations to the items that have descriptions in languages they don’t speak and understand.
1.2.2 Reusability
The process of implementing or updating software systems using existing software components. The following layers of reuse involved in the development:
Implementation: Reusable classes and methods(programming)
Design : Reusable designs and components(patterns)
Architecture: Reuse of application frameworks, middleware, services
Whole system: Configuration and reuse of applications
Benefits of reusability:
Accelerated development, lower development costs, reduced process risk, and standards compliance.

1.2.3 Reliability
The probability of failure-free software operation for a specified period of time in a specified environment.
Our plan to achieve reliability includes:
using reliable control tools 
programming carefully to control the process that is used
testing thoroughly by using formal techniques for proving correctness

1.2.4 Documentation
Current PyFlicks version is documented in GitHub. GitHub controls and manages the project sophisticatedly.
Customer Requirements

Use case description:
Register Account 
A guest is encouraged to register in order to take advantage of benefits only open to members, such as receiving personalised recommendations from the system. The registration will capture personal details, login information and a knowledge base about the user’s preferences and interests.
Update Account
A registered user can update his/her profile with modified preferences, a valid username and password.

View Profile
Upon the successful login the user can view his/her profile  
Search Movie
All users will be able to search for a movie. There will be two types of search: simple and advanced.
Rate a movie
A user can Rate a movie in a numeric scale based on his/her knowledge on the movie (in the scale of 1 to 5).
Watch movie
A user can enable this option before rating a movie.
Add movies to favorites
The members should be able to add any movie to their favorites.
Delete movies from favorites
The members should be able to remove any movie from their favorites list.
Add Movie with Description
System Administrator can successfully add movies to the model with description.
Generate Movie Recommendation
Administrator can able to generate the recommendations to the user based on user’s favorite list.
Architectural Design

PHP:Maintaining a PHP+Apache server is far more simpler than maintaining a TomCat or Glassfish server. Cheaper hosting options available for PHP than for Javascript.
Machine Learning: The modern algorithm technique used in place of a lengthy rule-based standard algorithm. It is very flexible for UI Applications.
Subsystem Architecture

Application-specific layer consists of Application UI, Recommender Logic and Server subsystems. These are connected to the ML Interface, local storage, Database Interface and Data store subsystems in Application generic layer. Data Store is extended tp DB Connection and DB Tables in the same layer. Middleware layer is embedded with PHP, MySQL and Scikit subsystems. System software layer is maintained with TCP/IP subsystem connected with PHP.
Deployment Model

Use Case Realization Design
4.1 Sequence diagram
Search Movie
View Profile 
Add movie to Favorites
Delete movie from Favorites
Rate a Movie
Watch a Movie
View Control Panel
Register Account
4.1 Class Diagram

Subsystem Design
Application UI
Because PyFlicks is a web-based application, the user interface is built using HTML and CSS. Our goal is to create an interface that is simple and easy to navigate while still providing ways to reach each part of our system. It interacts with the web browser to render web pages and with PHP to receive content to display. The CSS design relies heavily on new web technologies like CSS grid and flexbox. These features rely on the assumption that users are using up-to-date web browsers like Safari, Google Chrome, and Firefox.
Page load time is a large consideration in designing any web-based applications. PyFlicks is not bottlenecked by the application UI load times, allowing us to generate and display pages as quickly as limited by PHP server-side processing.
Machine Learning Classifier
PyFlicks delivers recommendations using a machine learning classifier. The original design of the classifier used a support vector machine, but testing has shown that a random forest yields faster and better results. Furthermore, random forest recommendations vary slightly with each run of the classifier. This built-in randomness allows users to use the same training data see a fresh set of recommendations if they are not satisfied with current recommendations.
	The classifier interacts only with the SQL database. Input data is provided based on a given user’s preferences and all the movies included in the PyFlicks database. Every movie is classified as “not recommended” with standard weighting. Those movies included in the user’s list of preferred movies will be classified as “recommended” with an increased weighting. The classifier determines the likelihood of each movie in the database being classified in the “recommended” category and ranks the films in this order. The top movies not included in the user’s original preferences will be entered into the database as recommendations correlated with the user’s user ID.
	In a future model, user’s preferences could include moveis that the given user dislikes. These movies would be classified as “not recommended” with increased weight, reducing the likelihood of similar movies being included in the classifier’s recommendations.

Human Interfaces

Testing Plan & Results
7.1 UI & PHP testing plan
	Since the UI is built primarily on HTML CSS and PHP. This will be tested mainly by use. With UI features it is easy to see if the functionality is correct. Examples; page redirects properly, elements have the intended look. Elements and Features of the UI are tested repeatedly by using them during the implementation.

7.2 Machine learning testing plan
Testing for the machine learning classifier primarily examines speed and accuracy. Speed has been tested for both classifier training and classification using Python’s time and calendar libraries. Tests have shown the a random forest classifier greatly outperforms a support vector machine in training, but at the cost of a slight disadvantage.
Classifier
Time to Train
Time to Classify Results
Support Vector Machine
~300 seconds
~0 seconds
Random Forest
~0 seconds
~30 seconds
Accuracy was be tested qualitatively. Qualitative testing asked a group of test users to specify their preferences and then assess their satisfaction with the relevance of the classifier’s recommendations. Qualitative tests were also performed by designing movie test groups with a single significant common factor (such as a genre or year) and confirming that recommendations are being made according to the common factor.
	With a larger user base, it would be possible to carry out quantitative testing by measuring user satisfaction using the built-in movie rating system.
Project Status and Summary
Project Status
At this point in time the project is finished. nearly every feature we planned to do initially has been completed. Initially we planned to have the Machine learning and UI directly communicate with each other. We quickly realized that this was unreasonable since the Machine Learning took roughly 30 seconds to classify. Instead we had the Machine learning place the generated recommendations in the database, and the UI would read from the database to display them.  We may at a future date consider adding more features, such as movie playback, however there are no plans at this time.

Difficulties Encountered
We ran into issues implementing the hybrid user recommendation system. To fully use the hybrid system, we require a large number of users with rated movies. In order to use the system we need roughly 500 active users, something which we were unable to get over the course of the project.

Over the course of the project we had to redesign and add to the database. In the database we were initially missing several tables that became key at by the end of the project.  We also needed to add several elements to certain existing tables, which also became important to the finished project.
Journal of Project Activities
Over the course of this project, our group did not keep a running journal of meetings and discussions. The majority of our recorded communication was simply scheduling meetings. Any discussion about the project itself was done in person and unrecorded.
Individual Contributions
Team Member
Contributions
Paco Coursey
Application UI, PHP development, SQL
Ravali Kommuri
Subsystem design, Report, Collaborative System Development
Application UI, Reports, Gantt chart
Machine learning classifier, Feature vector
Database, PHP, Application flow, Python-SQL interface, Hybrid System Development

Project Schedule
See attached Gantt Chart.
Appendices
See attached source files and documentation.

Recommendation engines that run on collaborative filtering recommend each item (products advertised on your site) based on user actions. The more user actions an item has, the easier it is to tell which user would be interested in it and what other items are similar to it. As time progresses, the system will be able to give more and more accurate recommendations.


