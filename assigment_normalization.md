#  Assignment: Database Normalization

##Question

Normalize the following table into 1NF, 2NF, and 3NF:

| VendorCode | VendorName    | VendorPhone | ProductCode              | ProductDescription             | Price           | Grade     | Discount  |
|------------|--------------|-------------|--------------------------|--------------------------------|-----------------|-----------|-----------|
| vd001      | AtoZSupplier | 9090901010  | pd001, pd002, pd006      | Cement, Bricks, Cement         | 400, 80, 320    | A, B, C   | 4, 8, 10  |
| vd002      | Greatgravity | 9191912233  | pd003                   | Centrifugal pump               | 10000           | A         | 4         |
| vd003      | Powernet     | 8787871212  | pd004                   | 5G Internet                    | 850             | A         | 4         |
| vd004      | Gomobile     | 8686861313  | pd005, pd007            | Mobile phone, Feature phone    | 20000, 5000     | A, C      | 4, 10     |

---

## Step 1: First Normal Form (1NF)

Remove repeating groups and make values atomic.

| VendorCode | VendorName    | Phone      | ProductCode | ProductDesc        | Price | Grade | Discount |
|------------|--------------|------------|-------------|--------------------|-------|-------|----------|
| vd001      | AtoZSupplier | 9090901010 | pd001       | Cement             | 400   | A     | 4        |
| vd001      | AtoZSupplier | 9090901010 | pd002       | Bricks             | 80    | B     | 8        |
| vd001      | AtoZSupplier | 9090901010 | pd006       | Cement             | 320   | C     | 10       |
| vd002      | Greatgravity | 9191912233 | pd003       | Centrifugal pump   | 10000 | A     | 4        |
| vd003      | Powernet     | 8787871212 | pd004       | 5G Internet        | 850   | A     | 4        |
| vd004      | Gomobile     | 8686861313 | pd005       | Mobile phone       | 20000 | A     | 4        |
| vd004      | Gomobile     | 8686861313 | pd007       | Feature phone      | 5000  | C     | 10       |

**Primary Key:** (VendorCode, ProductCode)

---

## Step 2: Second Normal Form (2NF)

Remove partial dependency.

###  Vendor Table

| VendorCode | VendorName    | Phone      |
|------------|--------------|------------|
| vd001      | AtoZSupplier | 9090901010 |
| vd002      | Greatgravity | 9191912233 |
| vd003      | Powernet     | 8787871212 |
| vd004      | Gomobile     | 8686861313 |

---

###  Product Table

| ProductCode | ProductDesc        |
|-------------|--------------------|
| pd001       | Cement             |
| pd002       | Bricks             |
| pd003       | Centrifugal pump   |
| pd004       | 5G Internet        |
| pd005       | Mobile phone       |
| pd006       | Cement             |
| pd007       | Feature phone      |

---

###  Vendor_Product Table

| VendorCode | ProductCode | Price | Grade | Discount |
|------------|-------------|-------|-------|----------|
| vd001      | pd001       | 400   | A     | 4        |
| vd001      | pd002       | 80    | B     | 8        |
| vd001      | pd006       | 320   | C     | 10       |
| vd002      | pd003       | 10000 | A     | 4        |
| vd003      | pd004       | 850   | A     | 4        |
| vd004      | pd005       | 20000 | A     | 4        |
| vd004      | pd007       | 5000  | C     | 10       |

---

## Step 3: Third Normal Form (3NF)

Remove transitive dependency.

✔ No transitive dependency exists  
✔ All attributes depend only on primary keys  


## 🎯 Final Tables (3NF)

- Vendor(VendorCode, VendorName, Phone)  
- Product(ProductCode, ProductDesc)  
- Vendor_Product(VendorCode, ProductCode, Price, Grade, Discount)  

