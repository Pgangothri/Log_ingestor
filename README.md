# Log Ingestor and Query Interface

#### Project Demo

![Project Demo](https://github.com/MasterZesty/log-ingestor-with-query-interface/blob/ffeae08b03cc207a6010ec697ada831b826b9774/docs/demo/project_demo.gif)
## Overview
This system is designed to efficiently ingest, store, and query vast volumes of log data. It comprises a Log Ingestor responsible for accepting log data over HTTP and a Query Interface that enables users to perform full-text searches and apply filters on various log attributes.

## Technologies Used
- **Programming Language**: Python
- **Database**: MySQL
- **Technologies**: Kafka , Kafka Rest Proxy, Kafka Schema Registry
- **Frontend**: HTML CSS JavaScript
- **Backend**: Flask

## Features Implemented
1. **Log Ingestor**
   - Ingests logs in the provided JSON format via HTTP on port `3000`.
   - Ensures scalability to handle high log volumes.
   - Optimizes I/O operations and database write speeds.

![Log Ingestor Demo](https://github.com/MasterZesty/log-ingestor-with-query-interface/blob/ffeae08b03cc207a6010ec697ada831b826b9774/docs/demo/log_ingestor.png)
   
2. **Query Interface**
   - Offers a user-friendly interface (Web UI/CLI) for full-text search.
   - Includes filters for:
       - level
       - message
       - resourceId
       - timestamp
       - traceId
       - spanId
       - commit
       - metadata.parentResourceId
   - Implements efficient search algorithms for quick results.

![Query Interface Demo](https://github.com/MasterZesty/log-ingestor-with-query-interface/blob/main/docs/demo/query_interface_demo.gif)


3. **Advanced Features (To be Implemented...)**
   - Search within specific date ranges.
   - Utilization of regular expressions for search.
   - Combining multiple filters for precise queries.
   - Real-time log ingestion and searching capabilities.
   - Role-based access control to the query interface.

## System Architecture

### System Architecture Diagram

![System Architecture Diagram](https://github.com/MasterZesty/log-ingestor-with-query-interface/blob/99270e69b6919d0beec3ef1ef5a3e0a9cd428db5/docs/imgs/architecture_v1.0.0.svg)
### Log Ingestor I - Log Publisher Service
- Utilizes an HTTP server to receive logs.
- Parses incoming JSON logs and publishes them to kafka topic.

### Log Ingestor II - Log Consume Service
- Subscribes to the Kafka topic and consumes the log from topic.
- Stores log from topic to primary read database instance.

### Query Interface - Log Search Service
- Provides a user interface for search and filtering.
- Processes user queries and translates them into database queries.
- Utilizes optimized indexing for faster search results.

### Database Structure
- **MYSQL - Relational Database**: Stores structured log data, optimizing for structured queries and joins.
- **NoSQL Database (e.g., Elasticsearch)**: Facilitates full-text search and complex queries efficiently. (To be implemented...)

### Scalability and Performance
- **Scalability**: Implements database sharding for distributing load.
- **Caching Mechanism**: Utilizes caching strategies for frequently accessed data.
- **Load Balancing**: Distributes incoming requests across multiple servers for enhanced performance.

## How to Run the Pro
