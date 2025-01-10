# 🎨 Redis CLI Commands Cheat Sheet

Redis CLI is a powerful command-line interface for interacting with Redis. Below is a structured guide to important Redis commands, categorized by their functionality, with examples and simple explanations.

---

## 📌 **Key Management Commands**

### **1. Check if a key exists**
```redis
EXISTS key
```
- **Purpose:** Check if a key exists in the Redis database.
- **Returns:**
  - `1` if the key exists.
  - `0` if the key does not exist.
- **Example:**
  ```redis
  EXISTS "user:1"
  ```

### **2. Delete a key**
```redis
DEL key
```
- **Purpose:** Remove a key and its value.
- **Returns:** The number of keys deleted.
- **Example:**
  ```redis
  DEL "user:1"
  ```

### **3. Get the type of a key**
```redis
TYPE key
```
- **Purpose:** Check the type of value stored at a key.
- **Possible Types:** `string`, `list`, `set`, `zset`, `hash`, `none`.
- **Example:**
  ```redis
  TYPE "user:1"
  ```

### **4. Set a key to expire**
```redis
EXPIRE key seconds
```
- **Purpose:** Assign a time-to-live (TTL) to a key. After the TTL expires, the key is deleted automatically.
- **Example:**
  ```redis
  EXPIRE "session:123" 3600
  ```

### **5. Get the remaining TTL of a key**
```redis
TTL key
```
- **Purpose:** Check how many seconds remain before a key expires.
- **Returns:**
  - Remaining seconds.
  - `-1` if no expiration is set.
  - `-2` if the key does not exist.
- **Example:**
  ```redis
  TTL "session:123"
  ```

---

## 🧵 **String Commands**

### **1. Set a string value**
```redis
SET key value
```
- **Purpose:** Store a value as a string.
- **Example:**
  ```redis
  SET "name" "Alice"
  ```

### **2. Get a string value**
```redis
GET key
```
- **Purpose:** Retrieve the value of a string key.
- **Example:**
  ```redis
  GET "name"
  ```

### **3. Increment a numeric value**
```redis
INCR key
```
- **Purpose:** Increase the numeric value of a key by 1.
- **Example:**
  ```redis
  SET "counter" 10
  INCR "counter"  # Result: 11
  ```

### **4. Append to a string value**
```redis
APPEND key value
```
- **Purpose:** Add a string to the end of an existing value.
- **Example:**
  ```redis
  SET "greeting" "Hello"
  APPEND "greeting" ", World!"
  ```

---

## 🔑 **Hash Commands**

### **1. Set a field in a hash**
```redis
HSET key field value
```
- **Purpose:** Store a field-value pair in a hash.
- **Example:**
  ```redis
  HSET "user:1" "name" "Alice"
  ```

### **2. Get a field value from a hash**
```redis
HGET key field
```
- **Purpose:** Retrieve the value of a specific field in a hash.
- **Example:**
  ```redis
  HGET "user:1" "name"
  ```

### **3. Get all fields and values from a hash**
```redis
HGETALL key
```
- **Purpose:** Retrieve all fields and values in a hash.
- **Example:**
  ```redis
  HGETALL "user:1"
  ```

---

## 📜 **List Commands**

### **1. Add elements to a list (left)**
```redis
LPUSH key value1 value2 ...
```
- **Purpose:** Insert elements at the head (left) of a list.
- **Example:**
  ```redis
  LPUSH "tasks" "task1" "task2"
  ```

### **2. Get elements from a list**
```redis
LRANGE key start stop
```
- **Purpose:** Retrieve a range of elements from a list.
- **Example:**
  ```redis
  LRANGE "tasks" 0 -1
  ```

### **3. Remove an element from a list (left)**
```redis
LPOP key
```
- **Purpose:** Remove and return the first element of the list.
- **Example:**
  ```redis
  LPOP "tasks"
  ```

---

## 🔗 **Set Commands**

### **1. Add members to a set**
```redis
SADD key member1 member2 ...
```
- **Purpose:** Add one or more members to a set.
- **Example:**
  ```redis
  SADD "colors" "red" "blue"
  ```

### **2. Get all members of a set**
```redis
SMEMBERS key
```
- **Purpose:** Retrieve all members of a set.
- **Example:**
  ```redis
  SMEMBERS "colors"
  ```

### **3. Check if a member exists in a set**
```redis
SISMEMBER key member
```
- **Purpose:** Verify if a specific member exists in a set.
- **Returns:**
  - `1` if the member exists.
  - `0` otherwise.
- **Example:**
  ```redis
  SISMEMBER "colors" "red"
  ```

---

## 📊 **Sorted Set Commands**

### **1. Add members with scores**
```redis
ZADD key score1 member1 score2 member2 ...
```
- **Purpose:** Add members to a sorted set with associated scores.
- **Example:**
  ```redis
  ZADD "scores" 10 "Alice" 20 "Bob"
  ```

### **2. Get members by score range**
```redis
ZRANGEBYSCORE key min max
```
- **Purpose:** Retrieve members within a specific score range.
- **Example:**
  ```redis
  ZRANGEBYSCORE "scores" 10 20
  ```

---

## 🖥️ **Server Commands**

### **1. Monitor all commands**
```redis
MONITOR
```
- **Purpose:** Display all commands processed by the Redis server in real-time.
- **Example:**
  ```redis
  MONITOR
  ```

### **2. Get server information**
```redis
INFO
```
- **Purpose:** Retrieve detailed information about the Redis server.
- **Example:**
  ```redis
  INFO
  ```

### **3. List all keys**
```redis
KEYS pattern
```
- **Purpose:** Fetch keys matching a specific pattern.
- **Example:**
  ```redis
  KEYS "user:*"
  ```

---

🎉 **Happy Redis-ing!** 😊
