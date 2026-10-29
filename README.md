# CA_ADVANCED_DB_ASSESSMENT
Individual Practical Database Portfolio for course MIT 8103. Hands-on technical portfolio demonstrating the practical design, implementation, optimization, and management of advanced database systems.
NAME: FRANCIS COOKEY.
STUDENT ID: xxxx.
COURSE CODE: MIT 8103.

# CASE STUDY: Enterprise Banking Database Design For JPmorgan Chase Nigeria
JPMorgan Chase & Co. is establishing a full-fledged commercial banking operation within the Federal Republic of Nigeria, targeting corporate banking, investment banking, asset management, and high-net-worth treasury operations. Operating under a Commercial Banking License with National/International Authorization issued by the Central Bank of Nigeria (CBN), the infrastructure must strictly comply with CBN regulatory frameworks, including the Guidelines on Cyber-Security Insurance for Banks and OFIs, the Nigerian Data Protection Act (NDPA), and the statutory requirements of the Financial Reporting Council of Nigeria (FRCN).

To support this operational footprint, JPMorgan Chase is deploying the Infosys Finacle Core Banking Solution v11. Finacle is a heavily normalized, highly transactional (OLTP) engine that demands extreme write throughput during peak operational windows, combined with intensive, block-level parallelization during End-of-Day (EOD) batch processing. The database persistence tier is built on Oracle Database 23ai Enterprise Edition running on an active-active, multi-node Oracle Exadata Database Service. This ensures a zero data-loss threshold—Recovery Point Objective (RPO = 0)—and near-instantaneous failover capability—Recovery Time Objective (RTO ≈ 0).


# MIT_8103_ADVANCED_DB
Individual Practical Database Portfolio for course MIT 8103. Hands-on technical portfolio demonstrating the practical design, implementation, optimization, and management of advanced database systems.

# 🏛️CASE STUDY: Enterprise Banking Oracle Database Design For JPmorgan Chase Nigeria

JPMorgan Chase & Co. is establishing a full-fledged commercial banking operation within the Federal Republic of Nigeria, targeting corporate banking, investment banking, asset management, and high-net-worth treasury operations. Operating under a Commercial Banking License with National/International Authorization issued by the Central Bank of Nigeria (CBN), the infrastructure must strictly comply with CBN regulatory frameworks, including the Guidelines on Cyber-Security Insurance for Banks and OFIs, the Nigerian Data Protection Act (NDPA), and the statutory requirements of the Financial Reporting Council of Nigeria (FRCN).

To support this operational footprint, JPMorgan Chase is deploying the Infosys Finacle Core Banking Solution v11. Finacle is a highly normalized, highly transactional (OLTP) engine that demands extreme write throughput during peak operational windows, combined with intensive, block-level parallelization during End-of-Day (EOD) batch processing. The database persistence tier is built on Oracle Database 23ai Enterprise Edition running on an active-active, multi-node Oracle Exadata Database Service. This ensures a zero data-loss threshold—Recovery Point Objective (RPO = 0)—and near-instantaneous failover capability—Recovery Time Objective (RTO ≈ 0).

# User Personas and Access 
The relational schema is built to isolate and serve discrete operational domains, maintaining structural data separation:
To protect data integrity from application-layer flaws or network dropouts, every core business rule is implemented directly within the database tier using declarative constraints, and atomic transaction scopes. To support the three distinct organizational personas safely, the database is architected into three dedicated domain schemas. This enforces strict security boundaries while allowing for specialized multi-currency, trading, and compliance workflows.

| Domain Owner | Schema | Primary Responsibilities | Core Data Entities |
| :--- | :--- | :--- | :--- |
| **Persona A: Corporate Clearing team** | `TRANSACT` | High-value payment processing, multi-currency corporate pooling, and external financial gateway integrations. | <ul><li>`clearing_accounts`</li><li>`wire_pool_transactions`</li></ul> |
| **Persona B: Financial control officers** | `TRANSACT` | General Ledger (GL) balancing, End-of-Day (EOD) closures, fee income collection, and correspondent bank matching. | <ul><li>`general_ledger_entries`</li><li>`nostro_vostro_reconciliation`</li></ul> |
| **Persona C: Risk, Compliance & Audit team** | `CUSTOMER` | Central Bank of Nigeria (CBN) regulatory, unalterable system forensic tracking, and real-time AML analysis. | <ul><li>`cbn_registry`</li><li>`aml_forensic_trail`</li></ul> |

### 🔒 Cross-Domain Security Design
1. **Isolation:** Each schema operates as an independent security boundary. Tables are wholly owned by their respective schema users.
2. **Access Control:** No direct cross-schema modifications are allowed. If the `CUSTOMER` engine needs to read data from `TRANSACT` for AML transaction spotting, explicit `GRANT SELECT` privileges must be mapped explicitly via database roles.
