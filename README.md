# Labelbox Introduction to API
In this file you'll find the necessary resources and examples to get started using the Labelbox API both directly through GraphQL and with our Python package.
### Additional Resources
1. [GraphQL Documentation](https://graphql.org/learn/)
2. [Python Labelbox Package Documentation](https://labelbox.com/docs/python-client-api/getting-started)



## GraphQL Queries and Mutations
In this section we will be executing our queries through the [API explorer](https://app.labelbox.com/explorer).
To start off, run the following query:
```
query {
  user {
    id
    email
    role
    organization {
      id
      name
    }
    projects {
      id
      name
    }
  }
}
```
This query retrieves your own user information. In GraphQL terminology, "user" is our root object from which we select all of its fields we want to retrieve ("id", "email", "role") and a sub-object: "organization". Hovering over the syntax will give more information about each object/field. The Documentation Explorer to the upper right provides more Schema details; try searching "User" to explore other fields you can select.

### Creating parameterized queries

We can use some of the data we just retrieved to construct a more involved query. Copy and paste the project ID into the Query Variables section in the bottom left pane, like so:
```
 { "project_id" : "<PROJECT ID HERE>" }
```
In the main text window, run the following:
```
query byProjects($project_id: ID!) {
  projects(where: {id_contains: $project_id}) {
    members {
      user {
        email
        id
        role
      }
    }
  }
}

```
This time, we've created a function for our query by naming it ```byProjects()``` and assigning it a parameter, ```$project_id``` of type ```ID```. In the bottom pane we've tossed our function an argument for project ID. The resulting data is the member info for only the project we specified.

### Common Queries
1. Get DataRows by Dataset
```
query getDataRows($dataset_id: ID!) {
  datasets(where: {id_contains: $dataset_id}) {
    name
    id
    dataRows {
      id
      externalId
    }
  }
}
```
  Query Variables: ``` {"dataset_id": "<DATASET ID HERE>"}```

2. Get stringified JSON Labels associated with a Project (paginated)
You can also filter Labels by review, creator, etc.
```
query getLabels($project_id: ID!) {
  projects(where: {id_contains: $project_id}) {
    id
    name
    labels(first: 10) {
      id
      createdBy {
        email
      }
      label
    }
  }
}
```
  Query Variables: ```{"project_id": "<PROJECT ID HERE>"}```

3. Get Ontology of a Project - objects, classifications, tools and all
```
query getOntology($project_id: ID!){
  project(where: {id: $project_id}){
    ontology{
      normalized
    }
  }
}
```
  Query Variables: ```{"project_id": "<PROJECT ID HERE>"}```

4. Get Reviews of a Project
```
query getReviews($project_id:ID!){
  project(where: {id: $project_id}) {
    reviews(first: 20) {
      id
      score
      createdAt
      updatedAt
    }
  }
}
```
