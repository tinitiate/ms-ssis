![tinitiate ssis](/images/tiniaitessis.png)
# Data Warehouse data model for Invoicing
* Schema DDL for invoicing_dw.
* Table DDL for customer_dim, product_dim, time_dim and invoice_fact.
```sql
CREATE SCHEMA invoicing_dw AUTHORIZATION dbo;

CREATE  Table invoicing_dw.customer_dim(
    cust_id INT NOT NULL,
    cust_name           VARCHAR(100),
    membership_details  VARCHAR(25),

);
-- Primary Key
ALTER TABLE invoicing_dw.customer_dim
ADD CONSTRAINT pk_cust_id PRIMARY KEY (cust_id);


CREATE  Table invoicing_dw.product_dim(
    product_id          INT NOT NULL,
    product_category    VARCHAR(100),
    product_name        VARCHAR(25),
    product_unit_price  DECIMAL(12,2),
    price_effective_from DATE,
    price_effective_to   DATE
);
-- Primary Key
ALTER TABLE invoicing_dw.product_dim
ADD CONSTRAINT product_id PRIMARY KEY (product_id);

CREATE  Table invoicing_dw.time_dim(
time_id             INT NOT NULL,
invoice_date        DATE,
invoice_month       VARCHAR(25),
invoice_quarter     VARCHAR(25),
invoice_year        INT
);
-- Primary Key
ALTER TABLE invoicing_dw.time_dim
ADD CONSTRAINT time_id PRIMARY KEY (time_id);

-- Invoice Fact Table
CREATE TABLE invoicing_dw.invoice_fact (
    invoice_id          INT NOT NULL,
    store_id            INT NOT NULL,
    cust_id             INT NOT NULL,    
    time_id             INT NOT NULL,
    product_id          INT NOT NULL,
    --
    invoice_total       DECIMAL(12,2),
    discount            DECIMAL(12,2),
    invoice_price       DECIMAL(12,2),
    quantity            DECIMAL(12,2),
    invoice_item_price  DECIMAL(12,2)
);

alter table invoicing_dw.invoice_fact add constraint fk_invoice_cust_id foreign key(cust_id) references invoicing_dw.customer_dim(cust_id);
alter table invoicing_dw.invoice_fact add constraint fk_invoice_time_id foreign key(time_id) references invoicing_dw.time_dim(time_id);
alter table invoicing_dw.invoice_fact add constraint fk_invoice_product_id foreign key(product_id) references invoicing_dw.product_dim(product_id);
```
![star schema](/images/star_schema.png)
