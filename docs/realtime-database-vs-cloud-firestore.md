|			| Realtime Database | Cloud Firestore	| 
|---			| ---				| ---			 	|
|Data Model	| NoSQL - a large JSON tree, easier to store simple data, harder to organize complex, hierarchical data at scale | NoSQL - documents in collections, simple data in documents, complex hierarchical data at scale in subcollections within documents, less denomalization and flattening |
|Querying	| Deep query with limited sorting and filtering. In a single query, you can either sort or filter, not both, on a property | Index query with compound sorting and filtering and chaining. Default query type is indexed. Query performance is proportional to the size of result set, not data set |
|Writes and Transactions | Basice write and transactions | Atomic write and transactions. Operations are batched and completed atomically |
|Scalability | Requires sharding | Fully automatic |
|Security	| Only validated using cascaded read and write rules | Server SDKs use IAM. Rules don't cascade unless wildcard is used. |
