# CA_ADVANCED_DB_ASSESSMENT
Individual Practical Database Portfolio for course MIT 8103. Hands-on technical portfolio demonstrating the practical design, implementation, optimization, and management of advanced database systems.
NAME: FRANCIS COOKEY.
STUDENT ID: xxxx.
COURSE CODE: MIT 8103.

# CASE STUDY: Enterprise Banking Database Design For JPmorgan Chase Nigeria
JPMorgan Chase & Co. is establishing a full-fledged commercial banking operation within the Federal Republic of Nigeria, targeting corporate banking, investment banking, asset management, and high-net-worth treasury operations. Operating under a Commercial Banking License with National/International Authorization issued by the Central Bank of Nigeria (CBN), the infrastructure must strictly comply with CBN regulatory frameworks, including the Guidelines on Cyber-Security Insurance for Banks and OFIs, the Nigerian Data Protection Act (NDPA), and the statutory requirements of the Financial Reporting Council of Nigeria (FRCN).

To support this operational footprint, JPMorgan Chase is deploying the Infosys Finacle Core Banking Solution v11. Finacle is a heavily normalized, highly transactional (OLTP) engine that demands extreme write throughput during peak operational windows, combined with intensive, block-level parallelization during End-of-Day (EOD) batch processing. The database persistence tier is built on Oracle Database 23ai Enterprise Edition running on an active-active, multi-node Oracle Exadata Database Service. This ensures a zero data-loss threshold—Recovery Point Objective (RPO = 0)—and near-instantaneous failover capability—Recovery Time Objective (RTO ≈ 0).
