# GraphQL Exploration
Exploration of GraphQL through various sources.

## Learning GraphQL - [LinkedIn Learning](https://www.linkedin.com/learning/learning-graphql-2018)

### What is GraphQL?
- Declarative data fetching specification
- Developed by Facebook, open-sourced in 2015
- Language Agnostic
- Used by variety of companies due to performance benefits and ease of use

---

### Why use GraphQL?
The use of REST endpoints is very useful at the beginning and we would typically start off with examples such as:
- /api/ohio/cleaveland
- /api/ohio/cleaveland/neighborhoods
- /api/ohio/cleaveland/shops

As apparent from the above example, the more types of info we want to get from our endpoints, the larger the number of specific endpoints are needed. The chaos can quickly add up, leading to delayed or unacceptable response times as we have to make calls to ohio then to cleaveland and then so on and so forth.

An alternative to this is GraphQL, in GraphQL we use a query that looks very like a JSON object but without the values.

**Query:**
```
{
    state{
        name
        population
        people
    }
}
```

**Response:**
```
{
    "data":{
        "state":{
            "name":"Ohio",
            "population": 11,590,000,
            "people": [...]
        }
    }
}
```

#### **Benefits of GraphQL:**
- Defines shape of desired data and calls it at once rather than making multiple REST calls
- Backward compatible
- Version-free
- Can wrap around existing API structure
- Deprecated fields don't break a GraphQL query

---

#### **Commenting Your Queries:**
 We can add comments to our queires using the '#' character as shown below
 ```
 {
    # My First Query
    state{
        name
    }
}
 ```

 ---

#### **Passing Arguments:**
For this next part, we'll be utilising the [Github GraphQL API Explorer](https://docs.github.com/en/graphql/overview/explorer).

We can also pass arguments to properties that support argument passing such as repository owner on the Github GraphQL API Explorer. Here we are getting the id, url and resource path of facebook's github profile.

Note: Double quotation marks are required for paramters, single quotation marks will throw an error.

 ```
{
    repositoryOwner(login:"facebook"){
        id
        url
        resourcePath
    }
}
 ```

**Response:**
 ```
 {
  "data": {
    "repositoryOwner": {
      "id": "MDEyOk9yZ2FuaXphdGlvbjY5NjMx",
      "url": "https://github.com/facebook",
      "resourcePath": "/facebook"
    }
  }
}
 ```

 ---

 #### **Required Arguments:**
Some queries can have required arguments such as the following query where owner is required for the query to be executed.

```
{
  repository(name:"graphql", owner:"facebook"){
    id
    description
    homepageUrl
  }
}
```

**Response:**
 ```
 {
  "data": {
    "repository": {
      "id": "MDEwOlJlcG9zaXRvcnkzODM0MjIyMQ==",
      "description": "GraphQL is a query language and execution engine tied to any backend service.",
      "homepageUrl": "https://spec.graphql.org"
    }
  }
}
 ```

 ---


