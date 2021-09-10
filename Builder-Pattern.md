**Builder Pattern**

A builder pattern is used when you want to create complex objects  with many optional parameters and it provides immutability.  

In the below class we have four parameters to create a user but while creating objects at run time you might have phone number or age or both where first name and last name are required parameters. For this to implement you might be creating too many constructors which does not scale when you have more parameters coming.  

```
public class Main
{
	public static void main(String[] args) {
		System.out.println("Hello World");
		
		User user = new User.UserBuilder("Arihant", "Sai")
		            .age(10)
		            .phone("123455")
		            .build();
		            
		System.out.println(user.getString());
	}
}

class User {
    
    private final String fName; // required
    private final String lName; // required
    private final int age; // optional
    private final String phone; // optional
    
    public User(UserBuilder build) {
        
        this.fName = build.fName;
        this.lName = build.lName;
        this.age = build.age;
        this.phone = build.phone;
    }
    
    public String getString() {
        return this.fName + "," + this.lName + "," + this.age + "," + this.phone;
    }
    
     static class UserBuilder {
    
        private final String fName; // required
        private final String lName; // required
        private int age; // optional
        private String phone; // optional
        
        public UserBuilder(String fName,String lName) {
            this.fName = fName;
            this.lName = lName;
        }
        
        public UserBuilder age(int age) {
           this.age = age;
            return this;
        }
        
        public UserBuilder phone(String phone) {
            this.phone = phone;
            return this;
        }
        
        public User build() {
            User user = new User(this);
            return user;
        }
    }
    
}
```

More info:
https://howtodoinjava.com/design-patterns/creational/builder-pattern-in-java/
