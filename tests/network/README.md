# Network Security Validation

## Test NS-01 - Public Routing

**Objective:**  
Verify that the public subnet is associated with a route table containing a default route to the Internet Gateway.

**Expected Result:**  
The public route table contains a `0.0.0.0/0` route targeting the Internet Gateway.

**Observed Result:**  
Pending validation.

**Status:** Pending

---

## Test NS-02 - Private Subnet Isolation

**Objective:**  
Verify that the private subnet does not have a direct route to the Internet Gateway.

**Expected Result:**  
The private route table contains only VPC-local routing and no Internet Gateway default route.

**Observed Result:**  
Pending validation.

**Status:** Pending

---

## Test NS-03 - Private Application Access Boundary

**Objective:**  
Verify that the private application security group permits application traffic only from the designated public web security group.

**Expected Result:**  
TCP port `8080` is permitted from the public web security group and is not exposed to `0.0.0.0/0`.

**Observed Result:**  
Pending validation.

**Status:** Pending