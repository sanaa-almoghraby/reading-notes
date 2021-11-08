# Add relationships between types
## @connection
The @connection directive enables you to specify relationships between @model types. Currently, this supports one-to-one, one-to-many, and many-to-one relationships. You may implement many-to-many relationships using two one-to-many connections and a joining @model type. 

## Definition
directive @connection(keyName: String, fields: [String!]) on FIELD_DEFINITION


## Usage
Relationships between types are specified by annotating fields on an @model object type with the @connection directive.

The fields argument can be provided and indicates which fields can be queried by to get connected objects. The keyName argument can optionally be used to specify the name of secondary index (an index that was set up using @key) that should be queried from the other type in the relationship.

When specifying a keyName, the fields argument should be provided to indicate which field(s) will be used to get connected objects. If keyName is not provided, then @connection queries the target table's primary index.
      
* Has one
 you can define a one-to-one connection where a project has one team

 type Project @model {
  id: ID!
  name: String
  team: Team @connection
}

type Team @model {
  id: ID!
  name: String!
}

can also define the field you would like to use for the connection by populating the first argument to the fields array and matching it to a field on the type

##  Belongs to
You can make a connection bi-directional by adding a many-to-one connection to types that already have a one-to-many connection. 

## Many-to-many connections
You can implement many to many using two 1-M @connections, an @key, and a joining @model. 
## Alternative definition
The above definition is the recommended way to create relationships between model types in your API. This involves defining index structures using @key and connection resolvers using @connection. There is an older parameterization of @connection that creates indices and connection resolvers that is still functional for backwards compatibility reasons. It is recommended to use @key and the new @connection via the fields argument.
## Limit
The default number of nested objects is 100. You can override this behavior by setting the limit argument. 

## Generates
In order to keep connection queries fast and efficient, the GraphQL transform manages global secondary indexes (GSIs) on the generated tables on your behalf when using @connection