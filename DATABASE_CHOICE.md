# Database Choice

## My Choice

I selected Azure Cosmos DB for NoSQL using the serverless capacity mode.

## Justification

Azure Cosmos DB is the best choice for this Text Analyzer function because the analysis results are JSON documents. Cosmos DB stores JSON data naturally without requiring a fixed relational schema. It also works well with Azure Functions and supports serverless pricing, which is suitable for a student lab because costs are based on actual usage. The Python SDK makes it straightforward to insert and retrieve analysis records from the function code.

## Alternatives Considered

Azure Table Storage was considered because it is simple and low cost, but it is less flexible for nested JSON documents and querying structured analysis results.

Azure SQL Database was considered, but it requires table schema design and is better suited for relational data.

Azure Blob Storage was considered, but it is mainly object storage and does not provide database-style querying for analysis history.

## Cost Considerations

Azure Cosmos DB serverless charges based on request units consumed by database operations. This is suitable for a small lab because there is no need to provision dedicated throughput. The free tier may also reduce or eliminate cost for small development workloads.