```typescript
  "${self:custom.AuctionTable.Arn}"

  Resource: { "Fn::GetAtt": ["catalogItemsQueue", "Arn"] }
```

```typescript
  Resource: { Ref: "createProductTopic" },

  environment: {
    TABLE_STOCKS: "${.env:TABLE_STOCKS}"
  }
```
