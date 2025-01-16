### **1. ZRANK**

- **설명**: 지정된 멤버의 랭크(순위)를 반환합니다. 랭크는 **오름차순으로 정렬된 순서**를 나타내며, 0부터 시작합니다.
- **형식**:
    
    ```plaintext
    ZRANK key member
    ```
    
- **예시**:
    
    ```plaintext
    ZADD leaderboard 100 player1
    ZADD leaderboard 200 player2
    ZRANK leaderboard player1
    ```
    
    - 결과: `0` (player1은 첫 번째 순위)

---

### **2. ZADD**

- **설명**: Redis의 Sorted Set에 멤버를 추가합니다. 멤버와 함께 점수(score)를 지정하여 자동으로 정렬합니다.
    
- **형식**:
    
    ```plaintext
    ZADD key score member [score member ...]
    ```
    
- **옵션**:
    
    - `NX`: 이미 존재하는 멤버를 업데이트하지 않음.
    - `XX`: 이미 존재하는 멤버만 업데이트.
    - `CH`: 변경된 항목의 개수를 반환.
    - `INCR`: 지정한 멤버의 점수를 증가.
- **예시**:
    
    ```plaintext
    ZADD leaderboard 100 player1 200 player2
    ZADD leaderboard 150 player3
    ```
    
    - 결과: Sorted Set에 `player1`, `player2`, `player3`가 추가됨.

---

### **3. ZRANGEBYSCORE**

- **설명**: 지정된 점수 범위에 속하는 멤버를 반환합니다.
    
- **형식**:
    
    ```plaintext
    ZRANGEBYSCORE key min max [WITHSCORES] [LIMIT offset count]
    ```
    
    - `WITHSCORES`: 멤버와 함께 점수를 반환.
    - `LIMIT offset count`: 반환 결과를 제한.
- **예시**:
    
    ```plaintext
    ZRANGEBYSCORE leaderboard 100 200
    ZRANGEBYSCORE leaderboard -inf +inf WITHSCORES LIMIT 0 2
    ```
    
    - 결과: 점수가 100~200 사이인 멤버, 혹은 상위 2명의 멤버.

---

### **4. ZREM**

- **설명**: Sorted Set에서 하나 이상의 멤버를 제거합니다.
- **형식**:
    
    ```plaintext
    ZREM key member [member ...]
    ```
    
- **예시**:
    
    ```plaintext
    ZREM leaderboard player1
    ```
    
    - 결과: `player1`이 `leaderboard`에서 삭제됨.

---

### **5. HSET**

- **설명**: Redis의 Hash 자료구조에 **필드-값 쌍**을 설정합니다.
- **형식**:
    
    ```plaintext
    HSET key field value [field value ...]
    ```
    
- **예시**:
    
    ```plaintext
    HSET user:100 name "John" age "30"
    ```
    
    - 결과: `user:100` 해시에 `name: John`, `age: 30`이 저장됨.

---

### Redis 명령어 정리

- `ZRANK`: 멤버의 순위를 반환.
- `ZADD`: 점수와 함께 멤버를 추가.
- `ZRANGEBYSCORE`: 특정 점수 범위의 멤버를 조회.
- `ZREM`: 멤버를 삭제.
- `HSET`: Hash에 필드와 값을 설정.