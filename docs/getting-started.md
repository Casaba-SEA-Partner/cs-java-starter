# Getting Started with GraphQL API

## Query vs. Mutation

There are few types of element in GraphQL: query, mutation etc. They all can be used in different way.

### Query

Query is mainly for retrieving data from server, like if you want to 
query shop's menus / brands and categories using following query:

```graphql
{
  shop {
    name,
    brands {
      name
    }
    
    menus {
      name
      children {
        name
      }
   }
    
    categories {
      name
      code
      children {
        name
        code
      }
    }
  }
}
```

Query can run with parameters, say if you want check the details for a specific product: 

```graphql
{
	shop {    
    productByCode(codes: { codes: ["5601018"] }) {
      id
      code
      title
      skus {
        options {
          frontName
          value {
            displayName
          }
        }
        salePrice {
          amount
        }
      }
    }
  }
}
```

### Mutation

Mutation is to create / update server side data.

e.g. if you want to create(reigster) a new user:
```graphql
mutation {
  bffUserRegister(input: {
    account: "email@baozun.com",
    nickname: "Someone",
    isAcceptPromotion: false,
    password: "password",
    source: PC,
  }) {
    userCode
  }
}
```

Mutation often respond with some useful queries you can use to fetch details, e.g. if you want to retrieve something when the user logging in:

```graphql
mutation {
  bffUserLogin(input: {
    account: "email@baozun.com",
    password: "password"
  }) {
    token,
    customer {
      nickName
    	email
      orders {
        edges {
          node {
            orderCode
          }
        }
      }
    }
  }
}
```

## User session

All queries runs without sessions if you don't prodvide the user token in header, you can also add a new header in the request, so that you can access / modify the customer's data.

User session only returned after a customer logged in:
```graphql
{
  customer {
    account
    nickName
    bffWishList {
      title
    }
  }
}
```


