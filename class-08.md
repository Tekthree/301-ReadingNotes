# Reading Notes
## Class 08
_____________________________________________________________________________________________________________________________________



### Best Practices in API Design

- The benefits of a well-designed API include: improved developer experience, faster documentation, and higher adoption for your API

Characteristics of a well-designed API
- A well designed API will be easy to work with, and its resources and associated operations can quickly be memorized by developers who work with it constantly.
- Implementing and integrating with an API with good design will be a straightforward process, and writing incorrect code will be a less likely outcome. It has informative feedback, and doesn’t enforce strict guidelines on the API’s end consumer.
- a complete API will make it possible for developers to make full- fledged applications against the data
- Having the same plurality across all resources and collections respectively for consistency is good practice. Keeping these nouns self explanatory helps developers understand the kind of resource described from the URL

- We shouldn’t use verbs in our endpoint paths. Instead, we should use the nouns which represent the entity that the endpoint that we’re retrieving or manipulating as the pathname.

GET retrieves resources.
POST submits new data to the server.
PUT updates existing data.
DELETE removes data.

- When designing endpoints, it makes sense to group those that contain associated information. That is, if one object can contain another object, you should design the endpoint to reflect that.
(Best practices for REST API design)[https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/]
