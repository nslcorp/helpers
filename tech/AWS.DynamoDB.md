```typescript
import {DocumentClient} from "aws-sdk/clients/dynamodb";
const dynamoDB: DocumentClient = new DynamoDB.DocumentClient();

// create item. ==> response null
await dynamoDB.put({ TableName: "...", Item: {...}}).promise();
```

```typescript
// getItemById
const response = await dynamoDB
  .get({ TableName: "...", Key: { id: "..." } })
  .promise();
const data = response.Item;
```

```typescript
// scan:: getAllItems
const response = await dynamoDB.scan({ TableName: "..." }).promise();
const data = response.Items;
```

```typescript
// updage::
const response = await dynamoDB.update({
    TableName: "..",
    Key: { id },
    UpdateExpression: "set propertyRoot.childPropertyName = :amount",
    ExpressionAttributeValues: { ":amount": amount },
    ReturnValues: "ALL_NEW",
  })
  .promise();
```

```typescript
  const response = await dynamodb
  .query({
    TableName: "...",
    IndexName: "myIndexName",
    KeyConditionExpression: "#status = :status AND endingAt <= :now",
    ExpressionAttributeValues: {
      ":status": "OPEN",
      ":now": new Date().toISOString(),
    },
    ExpressionAttributeNames: {
      "#status": "status",
    },
  })
  .promise();
  //status is a reserverd word. For reserverd word using #status and ExpressionAttributeNames mapping

  const data = response.Items
```
