# DynamoDB設計
## 概要
- 本ページでは、DynamoDBのテーブル設計を記す
- ユースケース項にて記されているすべてのユースケースを満たすように設計する。
- ただし、全てのユースケースにおいて、ユーザIDと紐づいていることが前提となる。
- 逆に、ユーザIDに紐づかないデータは取得しないように設計する。

## ユースケース
- ユーザ情報を取得する
- タスク一覧を取得する
- ある一定期間に紐づく作業一覧の取得
- タスク名/期限に紐づくタスク情報の取得
- タスクIDに紐づくタスク情報の取得
- タスクIDに紐づく作業一覧の取得

## テーブル設計
| ID(PK) | DataType(SK) | DataValue(LSI) | EndTime(Attr) | UserInfo | TaskInfo |
| :---: | :---: | :---: | :---: | :---: | :---: |
| {user_id} | {task_id}_name | {name} | - | - | - |
| {user_id} | {task_id}_deadline | {deadline} | - | - | - |
| {user_id}_event | {start_time} | {task_id} | {end_time} | - | - |
| {user_id} | user | - | - | {USER_INFO} | - |
| {user_id}_task | {task_id} | - | - | - | {TASK_INFO} |

## スキーマ定義補足
### deadline
#### 型
string (YYYY-MM-DD)
#### データ例
2020-12-01
### start_time, end_time
#### 型
string (ISO8601フォーマット)
#### データ例
2018-12-31T05:00:30.001000
### USER_INFO
#### 型
object
#### データ例
```json
{
    "name": "ユーザ1",
    "password": "P@ssw0rd",
    "isGoogleLinked": true,
    "googleConfig": {
        "calendar": {
        "id": "1",
        "name": "pomodoro-timer@gmail.com"
        },
        "taskList": {
        "id": "1",
        "name": "timer作成"
        }
    },
    "defaultLength": {
        "work": 25,
        "rest": 5
    }
}
```
### TASK_INFO
#### 型
object
#### データ例
```json
{
    "name": "タスク1",
    "parentTaskId": "1",
    "finishedMinutes": 30,
    "estimatedMinutes": 150,
    "deadline": "2022-03-29",
    "notes": "備考を記載"
}
```