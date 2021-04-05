# Test-backend

## Set Up DB Variable
- Set up the DB Username and Password in `/flip-test/app/config/config.php`
- Create a blank DB called "flip_test" in phpmyadmin.

## Migration
Run migration by entering `flip-test` folder in terminal, then type `php app/migration/migration.php` in your terminal. The migration script will create:
1. Schema named `flip_test`
2. Table named `Account` and `Disbursement`
3. Row in `Account` table with attributes `account_number="123456789"`, `bank_code="bni"`, and `balance=10000`

## How to use Program
First, enter the `Test-backend` folder in your terminal.

==========================================================================================================


### If you want to run create disbursement service:
`php app/run.php create_disbursement 123456789 bni 10000 <remark>`

### Response

```json
Status 200
Content-Type: application/json

{
    "id": 5535152564,
    "amount": 10000,
    "status": "PENDING",
    "timestamp": "2021-04-05 09:12:42",
    "bank_code": "bni",
    "account_number": "123456789",
    "beneficiary_name": "PT FLIP",
    "remark": "sample remark",
    "receipt": null,
    "time_served": "0000-00-00 00:00:00",
    "fee": 4000
}
```


============================================================================================================


### If you want to run update disbursement service:
`php app/run.php update_disbursement <disbursement id>`

### Response

```json
Status 200
Content-Type: application/json

{
    "id": {disbursement id},
    "amount": 10000,
    "status": "SUCCESS",
    "timestamp": "2021-04-05 09:17:11",
    "bank_code": "bni",
    "account_number": "123456789",
    "beneficiary_name": "PT FLIP",
    "remark": "sample remark",
    "receipt": "https://flip-receipt.oss-ap-southeast-5.aliyuncs.com/debit_receipt/126316_3d07f9fef9612c7275b3c36f7e1e5762.jpg",
    "time_served": "2021-04-05 09:26:11",
    "fee": 4000
}
```


*note : you can get the {disbursment id} from table "disbursement".
