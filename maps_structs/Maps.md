# Maps

## Topics

- [What are Maps?](#what-are-maps?)
- [Creating Maps](#creating-maps)
- [Manipulation](#manipulation)

Collections of value types accessed by keys  
Created By: Literals and Make Functions  
Access: myMap["key"] = "value"  
Check for presence with ["value, ok"](#manipulation)  
Multiple "assignments" refer to same underlying data

### [What Are Maps?](#topics)

Maps are data types that lets you map **_one key type_** to **_one value type_**  
Defining Map - `map[key]value`

Keys have to able to be tested for **_equality_**.
The value can be **any** type

**Important Note**: keys must be the of the same _type_ and values must be of the same _type_ within a map  
(ie. map[string]float64)

**Equality Types**: [booleans, numerics, strings, pointers, interfaces, channels, structs, and arrays]  
**Non-Equality Types**: [slices, maps, and other functions]

### [Creating Maps](#topics)

Literal Syntax

```Go
func main(){
statePopulations := map[string]int{
    "California":       39250017,
    "Texas":            27862596,
    "Florida":          20614239,
    "New York":         19745289,
    "Pennsylvania":     12802503,
    "Illinois":         12801539,
    "Ohio":             11614373,
}
fmt.Println(statePopulations)
}

Output:
map[California:39250017 Texas:27862596 Florida:20614239 New York:19745289 Pennsylvania:12802503 Illinois:12801539 Ohio:11614373]
```

Make Function

```Go
func main(){
    statePopulations := make(map[string]int)
    statePopulations = map[string]int{
    "California":       39250017,
    "Texas":            27862596,
    "Florida":          20614239,
    "New York":         19745289,
    "Pennsylvania":     12802503,
    "Illinois":         12801539,
    "Ohio":             11614373,
}
fmt.Println(statePopulations)
}

Output:
map[California:39250017 Texas:27862596 Florida:20614239 New York:19745289 Pennsylvania:12802503 Illinois:12801539 Ohio:11614373]
```

### [Manipulation](#topics)

```Go
func main(){
    statePopulations := make(map[string]int)
    statePopulations = map[string]int{
    "California":       39250017,
    "Texas":            27862596,
    "Florida":          20614239,
    "New York":         19745289,
    "Pennsylvania":     12802503,
    "Illinois":         12801539,
    "Ohio":             11614373,
}
statePopulations["Georgia"] = 10310371
fmt.Println(statePopulations["Ohio"])
fmt.Println(statePopulations["Georgia"])
fmt.Println(statePopulations)
delete(statePopulations, "Georgia")

_, ok := statePopulations["oho"] //check whether key exist or not
fmt.Println(ok)
}

Output:
11614373
10310371
map[Ohio:11614373 Georgia:10310371 California:39250017 Texas:27862596 Florida:20614239 New York:19745289 Pennsylvania:12802503 Illinois:12801539 ]
map[Ohio:11614373 California:39250017 Texas:27862596 Florida:20614239 New York:19745289 Pennsylvania:12802503 Illinois:12801539]
false
```

```Go
func main(){
    statePopulations := make(map[string]int)
    statePopulations = map[string]int{
    "California":       39250017,
    "Texas":            27862596,
    "Florida":          20614239,
    "New York":         19745289,
    "Pennsylvania":     12802503,
    "Illinois":         12801539,
    "Ohio":             11614373,
}
    fmt.Println(len(statePopulations))
    sp := statePopulations
    delete(sp, "Ohio")
    fmt.Println(sp)
    fmt.Println(statePopulations)
}
Output:
7
map[California:39250017 Texas:27862596 Florida:20614239 New York:19745289 Pennsylvania:12802503 Illinois:12801539]
map[Florida:20614239 New York:19745289 California:39250017 Illinois:12801539 Texas:27862596   Pennsylvania:12802503 ]
```
