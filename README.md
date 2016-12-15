# Dromedary

```
{
  "predicate": "$date > '2017-01-01'",
  "data": "{\"date\":\"2017-01-01\"}"
}
```

```
Message {
  
  payload = "I am unlocked"
  queue = arn
  
  tumbler = [(message) -> {message.id == "uuid"},
              (message) -> {message.id == "uuid2"},
              () -> {date.now > "2017-01-01"}]
              
  
  consumeNewMessage = (message) -> {
    tumbler.each((pin) -> {if pin(message) tumbler.remove(pin)}
    if tumbler.empty queue.post(payload)
  }
```
