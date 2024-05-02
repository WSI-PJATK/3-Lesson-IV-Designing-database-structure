# 3-Lesson-IV-Designing-database-structure
3 Lesson IV - Designing database structure 15.03.2024 11:45 | Number of chapters: 5

## Introduction

In the previous lecture we learned about the concept of the relational data model. This model assumes that all the data is stored in the logical structures of tables. Its mathematical description comes from the relational algebra. The outline of this model was presented in the second lecture. In the fourth lecture we will discuss the problem of designing a relational database. In particular, we will answer the questions: why do we need to design database structures? How does the design process look like? What tools and notations do we use in the designing process? And finally - how do we create a database using a given model? During the WSI course we will present an outline of these topics. We will discuss them in depth during database related subjects like RBD, SBD and APBD.

### Learning outcome

- The student has a good understanding of the database design process, including the stages involved and their roles.

- The student can explain the importance of CASE tools in database development.

- The student knows the definitions of "entity" and the concept of a table model in a relational database.

- The student is well-versed in terms like entity, attribute, attribute domain, and entity key.

- The student understands relations in databases, including parent and child entities.

- The student can create a basic database diagram using CASE tools.

- The student is familiar with different database diagram notations, especially the one used in MS Visio.

## Draft of the process for designing a database
In the database design process we can distinguish three main stages or three perspectives defining this process:

### The Concept Design Stage

At this stage, we need to define the project's requirements. This is the marketing phase where we determine the necessary functions for our customer and consider their budget constraints.

The drafts at this stage are quite vague - lacking details and not specifying any technology. However, they should be clear enough for the customer to understand and make corrections, similar to the process of designing and constructing a car.  

### The Logical Design Stage

At this stage we transform the draft into a logical model. We create the model structure, specific solutions for the problem defined at the concept stage which will fulfil the client’s business needs. We design all the segments of the whole solution and define the connections between them. This time we can compare it to an architectural project with general plans but without the technical plans.

### The Implementation stage

At this stage, we convert the draft into a technological model. We consider all constraints related to available technology, while also ensuring that all conditions specified in the logical design are met.

…and then we create the prototype, debug it, implement the solution and we can work on the next improved version.

As mentioned before, a database is usually part of the entire information system, which is important to keep in mind when designing it. Similarly, before developing the whole system, a detailed analysis should be done to answer specific questions.

- What are we trying to achieve with our project?
- What are the main goals of our project and how can our system help address or improve certain issues?
- What specific activities need to be completed for our project?
- Who will be responsible for carrying out these activities?
- What kind of information will be stored in our database to meet all the project's needs?
- How much is the estimated cost of this solution?

From the database designer’s point of view the next to the last question concerning functionality of the future database is the most important one. However the answer to this question depends on the answers to the other questions.

The problems discussed above belong to the analysis stage of the designing process.

Then comes the project stage, in which the future system documentation is written. We should also make a detailed description of the system’s functions and define its users (“actors”). At the same time we should outline the structure of the database in a way which guarantees the possibility to record all the required data. We should also define all the integrity constraints, guaranteeing the logical consistency of data.

The documentation of the system functions and the definition of the actors is often presented in the form of a use case diagram.

On the other hand, the implementation model of a database can be represented by the entity relationship diagram.

The third and final stage is the implementation.

This description should be sufficient to explain what the entity diagram is and what role it plays in the design process. This role will be explained further on.

## What is an entity relationship diagram (ERD)?  
An **entity relationship diagram** is a model which can represent a part of reality needed for the system and also the database structure. Just like every model it represents a simplification of the real or database object it describes. At the stage of preliminary analysis the objects needed for our database are identified. The role of the entity diagram is to create models of these objects and relationships between them. The graphic character of the diagram makes it easier to understand the database structure. It is important to understand the relationships between the database objects which can often be quite complicated.

The use case diagram presented in the previous lecture was basically the input data for graphical user interface (GUI). The entity relationship diagram has a different function as it is a model of the data structure. Thus, it puts aside client’s perspective of our application, or deals with it in a small extent.

There is a list of requirements for a proper entity relationship diagram. It should

* Unambiguously present users’ requirements for the data stored in it,

* Allow to check if the analyst fully grasped the users’ requirements and the character of the environment in which the system will be utilized,

* Be much simpler from the database itself , as it puts aside the implementation details, which must be later developed by the database designer so that our database can exist and carry out its tasks.

### CASE (Computer Aided Software Engineering) tools

CASE tools are specialized programs which aid the designing of the information systems and allow to create various types of diagrams useful in the design process. The CASE tools provide graphic tools to design and draw diagrams on screen. The tools used to create the entity relationship diagrams must take into account the specific details of various database servers, for example the available data types. They should be (and usually are) able to translate the graphical version of the diagram into an SQL script. The script can then be run in the appropriate DBMS environment in order to generate all the database objects and integrity constraints.

In our lectures diagrams are made in **Microsoft Visio for Enterprise Architects 2003.**

The definition of an entity consists of the attributes (characteristics, properties) which are sufficient to unambiguously distinguish an entity from the other ones.

We must distinguish the notion of entity as a class of objects and as an instance of this class, i.e. a single instance of the object (single copy) of a given type. For example the “PERSON” entity as a type defines attributes necessary to describe a certain group of people. Only after we substitute specific values for its attributes we obtain an instance of this entity which will represent a particular person. It should be emphasized that if the entity is used to describe a selected class of objects (in our example a specific group of people), each single object of this class (in our case each specific person) must be described with the same attributes. Note that it may be hard in practice to describe two different groups of people, e.g. a group of prisoners and a group of preschoolers, with the same attributes.

But the principle:

**Entia non sunt multiplicanda praeter necessitatem (novacula Occami) - entities must not be multiplied beyond necessity – known as the Occam's razor
**
… also relates to the databases!

Entities are usually represented graphically as rectangles. The graphical representations of entities vary (slightly) according to the notation adopted by the specific CASE tool.

### Attribute  

It is crucial to correctly choose the attributes for describing an entity. Note that attributes represent certain abstract features or characteristics, not the specific values. The attribute of the Student entity is Name, not a specific value (say “Smith”) the attribute can take. The attribute should describe the entity rather than its relations with other entities, for instance in an airline’s database the attribute Seat_number should be an attribute of the Airliner entity, not Passenger, despite the fact that the passenger sits on a specific seat during the flight. In the same way the place won by an athlete in a competition is neither an attribute of the entity Athlete or Competition, but most preferably the Competition_results entity.

Consider now the entity as a model for future table in the database. It is clear that the attributes are nothing else but the models for the future columns, specifying their names. If we also define their domains, i.e. we specify the data types we will use to store the values of the attribute, we will define the domains of the columns table.

### First Normal Form (1NF)
The concept of the “First Normal Form” (1NF) was formulated as one of the Codd’s rules. It is the first condition we must meet when we normalize the database structure. Its purpose is to eliminate any anomalies in the data insertion, modification and deletion as well as any uncontrolled data redundancy. The whole normalization process and the subsequent normal forms will be thoroughly discussed during the relational databases course in the future semesters.

An entity (and thus also its corresponding table) is in the first normal form if:

* It describes one type (one class) of objects; e.g. the information about the car owners and their cars IS NOT stored in a single entity that contains attributes of both the owners as well as the cars,

* Its attribute values are elementary (atomic , indivisible) - each column represents a scalar (atomic) value rather than an array, list or anything that has its own structure; e.g. the Person entity DOES NOT include an attribute called Names which contains all the person’s names stored in a list.

* It does not contain collections (i.e. repeating groups of information); e.g. in order to store the information about sportsmen we DO NOT ADD to the Athlete entity an attribute called Medals containing all the medals won by him or her.

* It has a key, i.e. a set of attributes whose values distinguish each row from the other ones.

The order of the attributes should not encode any information, i.e. any change in the order of attributes should have no influence on the information content; e.g. in order to record information about the competition results we DO NOT create an entity called Result with attributes Athlete 1, Athlete 2, Athlete 3, ...

The above definition of the 1NF is a bit of an over-interpretation of the original one. The latter consists only of the first three points, but I allowed myself to extend it slightly for the sake of the further argument. All the information above is true and correct .

### Key 
The term "entity key" describes a set of entity's attributes whose values are unique (unambiguous) for its every instance. Similarly, the term "table key" describes a set of columns whose values will be unique (unambiguous) for every row in the table. Obviously it is possible that these sets contain only one element. Each table (entity) may contain none, one or more sets fulfilling the uniqueness condition, for example the Social security number or the PESEL can be the key in the Person entity or the Registration_number in the Car entity. However if there is no attribute with the uniqueness property in the entity we need to add an artificial attribute (column in the table) that meets this requirement. This is usually an attribute of integer type. The table column will then contain integers which uniquely identify the instances. But it can also be an attribute of the text type – e.g. the lecture code in the studies curriculum.

If the entity has more than one set of attributes whose values meet the requirement of uniqueness for every instance of the entity, then you should arbitrarily choose one of them to act as the primary key. If the entity has only one set, then there is no dilemma involved - it automatically becomes a primary key. Thus, we can identify a few keys in the entity, but only one of them can be used as our primary key.

Every CASE tool allows us to select the attribute (or multiple attributes) as the primary key during the design phase of our diagram. The illustration below shows this process in MS Visio.

### Data types – attributes domains
Data types or attribute domains are sets of values which can be stored by variables in the table columns. The principal types of data which we will encounter in every DBMS is the numeric type, the text type and the date type. For each of these types specific implementations provide a number of subtypes. For example: for a numeric type there is the two-byte integer and the four-byte one, the floating point number stored in four or eight bytes etc. Therefore we should find out what types are available before we start working in the specific DBMS environment.

When we speak about the entity-relationship diagram as a model of the future database we operate on the level of abstract concepts. On the other hand, on the database level we are closer to the concrete implementation. Hence, at the conceptual level (entity-relationship diagram) we are talking about the domain types as a general concept. However when we implement the database in a specific DBMS we use the types of data specific to the database solution.

CASE tools usually offer a choice of one of these approaches - either operate on universal data types not associated with a particular DBMS or choose data types implemented in the specific DBMS. MS Visio distinguishes between these two specifications of the data types. We can choose platform independent data types (Portable Data Type) or database specific data types (Physical Data Type).

The following illustration shows the selection process of the attribute’s domain (data type) from the drop-down list representing the physical data types (Oracle Server).

### Relationship
The relationship is defined as an ordered list of entities in the relational model. Individual entities can appear on the list multiple times. Each relationship defines a certain dependence between the sets of copies (instances) of the entities belonging to it. This correlation is called the instance of the relationship. In other words an instance of the relationship is the relationship between the entities instances. For example, the relationship between the Person entities and the Car entities can be described as the OwnerOfTheCar. Every instance of the Person entity will be able to have a relationship with an instance of the Car entity thus creating information about the cars and their owners.

The relationship can be formally represented using the relational notation:

Z(E1 ,...,En)

which means: entities E1 , ..., En are included in the Z relationship

You can also describe the relationship verbally, e.g.:

* An employee works in a department (relationship between the Employee and the Department entity)

* An employee has a specific function in the project (relationship between the Employee and the Project entity)

* The company produces goods (relationship between the Company and the Goods entity)

In practice, when designing a database, we define relationships through their verbal description.
 
### Binary relationship
Binary relationship is a relationship that exists between two entities. It is represented graphically as a line connecting two frames (entities). An instance of a binary relationship is a two argument relation in the Cartesian product of the entities instances collections.

The graph below shows the relationship between the Student and the City entities . This relationship can be described as follows: every student was born in a city, each student in ONE city, but… many students could have been born in ONE city.

After defining the relationship in the CASE tool (in our case MS Visio), the primary key from one entity forming the relationship is transferred to the entity on the other side of the relationship. This way we can create a foreign key.

In the first lecture we described the example of the Course and Lecturer tables and a relationship between them: for each course there is one teacher responsible, but one teacher may be responsible for several courses. In that example, the ID of a lecturer was placed in the Courses table and served as the indicator in order to determine which teacher is responsible for that item. A similar case is shown in the example above. The city ID (i.e. primary key of the City entity) is placed in the Student entity in order to indicate his or her place of birth. One instance of the Student entity is associated with one instance of the City entity, thus creating a single instance of a relationship.

Let us go back to the definition of the relationship as an ORDERED list of entities. The relationship in our example can be described as follows: ONE student was born in ONE city, but in ONE city MANY students could have been born. This definition is not symmetric! For each student you can specify one city where he or she was born, but for each city we can potentially find many students who were born in it. A relationship of this kind is called a one-to-many relationship. Here the entity City is located on the ONE side of the relationship and entity Student on the MANY side. We also use other names: Student represents the child entity and City represents the parent entity.

When we define a relationship in a CASE tool, an attribute is automatically added to the entity on the “many” side, containing the value of the primary key of the other entity. Thus we have added a foreign key to the entity attributes. It will serve as a pointer linking the rows on the “many” side with one row on the “one” side of the relationship.

In our example MS Visio has automatically created in the Student entity the attribute IdMiasto (labeled FK1 - foreign key), defining the relationship between the instances of the Student entity with the instances of the City entity.
