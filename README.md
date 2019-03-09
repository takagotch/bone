### bone
---
https://github.com/go-zoo/bone

```go
import (
  "net/http"
  
  "github.com/go-zoo/bone"
)

func main() {
  mux := bone.New()
  
  mux.RegisterValidatorFunc("isNum", func(s string) bool {
    if _, err := strconv.Atoi(s); err == nil {
      return true
    }
    return false
  })
  
  mux.Get("/home/:id|isNum", http.HandlerFunc(HomeHandler))
  mux.Get("/profile/:id/:var", http.HandlerFunc(ProfileHandler))
  mux.Post("/data", http.HandlerFunc(DataHandler))
  
  mux.Get("/index/#id^[0-9]$", http.HandlerFunc(IndexHandler))
  
  mux.Handle("/", http.HandlerFunc(RootHandler))
  
  mux.GetFunc("/test", Handler)
  
  http.ListenAndServe(":8080", mux)
}

func Handler(rw http.ResponseWriter, req *http.Request) {
  val := bone.GetValue(req, "id")
  
  rw.Write([]byte(val))
}

```

```
```

```
```


