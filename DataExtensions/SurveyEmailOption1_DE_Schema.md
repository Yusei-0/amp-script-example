# Survey Email Option 1 Data Extensions

## SurveyRespondents

Use this as the sendable Data Extension.

| Field | Type | Length | Required | Primary Key | Notes |
| --- | --- | ---: | --- | --- | --- |
| SubscriberKey | Text | 50 | Yes | Yes | Contact key / send relationship. |
| EmailAddress | EmailAddress | 254 | Yes | No | Send email address. |
| FirstName | Text | 80 | No | No | Used in the greeting. |
| LastName | Text | 80 | No | No | Demo support field. |
| AgeVerified | Boolean |  | Yes | No | Must be true for this alcohol brand message. |
| EventName | Text | 120 | No | No | Event/campaign name. |
| GiftCardId | Text | 50 | Yes | No | Lookup key into AmazonGiftCards. |
| SurveyCompletedDate | Date |  | No | No | Demo support field. |
| Locale | Text | 10 | No | No | Demo support field. |

## AmazonGiftCards

Use this as the gift-card inventory Data Extension.

| Field | Type | Length | Required | Primary Key | Notes |
| --- | --- | ---: | --- | --- | --- |
| GiftCardId | Text | 50 | Yes | Yes | Lookup key from SurveyRespondents. |
| GiftCardCode | Text | 50 | Yes | No | Personalized Amazon code shown in the email. |
| GiftCardValue | Number |  | Yes | No | Page 1 uses 5. |
| Currency | Text | 3 | Yes | No | USD for this demo. |
| Status | Text | 20 | Yes | No | Available, Assigned, Redeemed, or Void. |
| AssignedSubscriberKey | Text | 50 | No | No | Helps prevent reusing a code. |
| AssignedDate | Date |  | No | No | Assignment timestamp/date. |

## Lookup Logic

The email sends from `SurveyRespondents`, reads `GiftCardId`, then looks up `GiftCardCode` and `GiftCardValue` in `AmazonGiftCards`.
