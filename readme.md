### Class Diagram
```
┌──────────────┐       ┌──────────────┐       ┌──────────────┐
│    User      │       │    Inbox     │       │    Email     │
├──────────────┤       ├──────────────┤       ├──────────────┤
│ - name: str  │       │ - emails:    │       │ - sender     │
│ - inbox:     │◄──────│   List[Email]│       │ - receiver   │
│   Inbox      │       ├──────────────┤       │ - subject:str│
├──────────────┤       │ + __init__() │       │ - body: str  │
│ + __init__() │       │ + receive_   │       │ - timestamp  │
│ + send_email()│      │   email()    │       │ - read: bool │
│ + check_     │       │ + list_      │       ├──────────────┤
│   inbox()    │       │   emails()   │       │ + __init__() │
│ + read_email()│      │ + read_email()│      │ + mark_as_   │
│ + delete_    │       │ + delete_    │       │   read()     │
│   email()    │       │   email()    │       │ + display_   │
└──────────────┘       └──────────────┘       │   full_email()│
        │                     │                │ + __str__()  │
        │                     │                └──────────────┘
        │                     │                       ▲
        │                     └───────────────────────┘
        │            (aggregation: Inbox contains Emails)
        │
        └─────────────────────────────────────────────┘
          (composition: User has an Inbox)

```
### Key Relationships:
1. **Composition**: `User` has an `Inbox` (lifecycle bound together)
2. **Aggregation**: `Inbox` contains `Email` objects (independent lifecycle)
3. **Associations**: `Email` has associations with two `User` objects (sender and receiver)
