---
description: Jasurbek Xasanboyev
---

# IEnumerable va IQuerable



```csharp
static void Main(string[] args)
{
    List<Employee> employees = new List<Employee>()
    {
        new Employee() { id = 1, name = "Jasurbek" },
        new Employee() { id = 2, name = "Muhammadkarim"}
    };
    IEnumerable<Employee> query = from emp in employees
                                  where emp.id == 1
                                  select emp;
    foreach(var item in query)
    {
        Console.WriteLine($"Id = {item.id} Name: {item.name}");
    }
}
class Employee
{
    public int id { get; set; }
    public string name { get; set; }
}

```

IQuerable ham  interfeys bo\`lib u System.Linq  namespace da joylashgan. IQuerable interfeysi IEnumerable interfeysidan olingan vorisdir. IQuerable Provayderlik hususiyatiga ega bo\`lib u IQueryProvider interfeysidir. U LinqProviders dan foydalanadi. IQuerable boshqa provayderlar bilan ishlash jarayonida eng yaxshi tanlovdir\( LINQ to Entites ga o\`xshash\).

```csharp
static void Main(string[] args)
{
    List<Employee> employees = new List<Employee>()
    {
        new Employee() { id = 1, name = "Jasurbek" },
        new Employee() { id = 2, name = "Muhammadkarim"}
    };

    IQueryable<Employee> query = employees.AsQueryable().Where(x => x.id == 1);

    foreach(var item in query)
    {
        Console.WriteLine($"Id = {item.id} Name: {item.name}");
    }
}
class Employee
{
    public int id { get; set; }
    public string name { get; set; }
}
```
