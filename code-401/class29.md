# Save data in a local database using Room 
The Room persistence library provides an abstraction layer over SQLite to allow fluent database access while harnessing the full power of SQLite. In particular, Room provides the following benefits:

* Compile-time verification of SQL queries.

* Convenience annotations that minimize repetitive and error-prone boilerplate code.

* Streamlined database migration paths.

### Setup
To use Room in your app, add the following dependencies to your app's build.gradle file:
dependencies {
    def room_version = "2.3.0"

    implementation "androidx.room:room-runtime:$room_version"
    annotationProcessor "androidx.room:room-compiler:$room_version"

    // optional - RxJava2 support for Room
    implementation "androidx.room:room-rxjava2:$room_version"

    // optional - RxJava3 support for Room
    implementation "androidx.room:room-rxjava3:$room_version"

    // optional - Guava support for Room, including Optional and ListenableFuture
    implementation "androidx.room:room-guava:$room_version"

    // optional - Test helpers
    testImplementation "androidx.room:room-testing:$room_version"

    // optional - Paging 3 Integration
    implementation "androidx.room:room-paging:2.4.0-beta01"
}

### Primary components
* The database class that holds the database and serves as the main access point for the underlying connection to your app's persisted data.
* Data entities that represent tables in your app's database.
* Data access objects (DAOs) that provide methods that your app can use to query, update, insert, and delete data in the database.
![](https://developer.android.com/images/training/data-storage/room_architecture.png)


# Defining data using Room entities 
You define each Room entity as a class that is annotated with @Entity. A Room entity includes fields for each column in the corresponding table in the database, including one or more columns that comprise the primary key.

By default, Room uses the class name as the database table name. If you want the table to have a different name, set the tableName property of the @Entity annotation. Similarly, Room uses the field names as column names in the database by default. If you want a column to have a different name, add the @ColumnInfo annotation to the field and set the name property. 

# Provide table search support

Room supports several types of annotations that make it easier for you to search for details in your database's tables. Use full-text search unless your app's minSdkVersion is less than 16.


# Define relationships between objects

Because SQLite is a relational database, you can define relationships between entities. Even though most object-relational mapping libraries allow entity objects to reference each other, Room explicitly forbids this

### Two possible approaches
1. Intermediate data class
2. Multimap return types

### Create embedded objects
Sometimes, you'd like to express an entity or data object as a cohesive whole in your database logic, even if the object contains several fields. In these situations, you can use the @Embedded annotation to represent an object that you'd like to decompose into its subfields within a table. You can then query the embedded fields just as you would for other individual columns.

# Define one-to-one relationships
A one-to-one relationship between two entities is a relationship where each instance of the parent entity corresponds to exactly one instance of the child entity, and vice-versa.
# Define many-to-many relationships
A many-to-many relationship between two entities is a relationship where each instance of the parent entity corresponds to zero or more instances of the child entity, and vice-versa.
# Define nested relationships
Sometimes, you might need to query a set of three or more tables that are all related to each other. In that case, you would define nested relationships between the tables.
![](https://developer.android.com/images/training/data-storage/room_nested_relationships.png)
# Accessing data using Room DAOs 
When you use the Room persistence library to store your app's data, you interact with the stored data by defining data access objects, or DAOs. Each DAO includes methods that offer abstract access to your app's database. At compile time, Room automatically generates implementations of the DAOs that you define.

By using DAOs to access your app's database instead of query builders or direct queries, you can preserve separation of concerns, a critical architectural principle. DAOs also make it easier for you to mock database access when you test your app.


# Anatomy of a DAO
You can define each DAO as either an interface or an abstract class. For basic use cases, you should usually use an interface. In either case, you must always annotate your DAOs with @Dao. DAOs don't have properties, but they do define one or more methods for interacting with the data in your app's database.

### There are two types of DAO methods that define database interactions:

1. convenience methods that let you insert, update, and delete rows in your database without writing any SQL code.
2. Query methods that let you write your own SQL query to interact with the database.
## Convenience methods
Room provides convenience annotations for defining methods that perform simple inserts, updates, and deletes without requiring you to write a SQL statement.
* Insert
@Dao
public interface UserDao {
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    public void insertUsers(User... users);

    @Insert
    public void insertBothUsers(User user1, User user2);

    @Insert
    public void insertUsersAndFriends(User user, List<User> friends);
}