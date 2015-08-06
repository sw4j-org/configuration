# sw4j.org Findbugs Configuration

* [BC: Equals method should not assume anything about the type of its argument]()

## Bad practice

### BC: Equals method should not assume anything about the type of its argument

Bad Example:

```
    public boolean equals(Object o) {
        Sample casted = (Sample)o;
        ...
    }
```

In this example a ClassCastException would be thrown which is discouraged for
this method.

### BIT: Check for sign of bitwise operation


### CN: Class implements Cloneable but does not define or use clone method
### CN: clone method does not call super.clone()
### CN: Class defines clone() but doesn't implement Cloneable
### CNT: Rough value of known constant found
### Co: Abstract class defines covariant compareTo() method
### Co: compareTo()/compare() incorrectly handles float or double value
### Co: compareTo()/compare() returns Integer.MIN_VALUE
### Co: Covariant compareTo() method defined
### DE: Method might drop exception
### DE: Method might ignore exception
### DMI: Adding elements of an entry set may fail due to reuse of Entry objects
### DMI: Random object created and used only once
### DMI: Don't use removeAll to clear a collection
### Dm: Method invokes System.exit(...)
### Dm: Method invokes dangerous method runFinalizersOnExit
### ES: Comparison of String parameter using == or !=
### ES: Comparison of String objects using == or !=
### Eq: Abstract class defines covariant equals() method
### Eq: Equals checks for incompatible operand
### Eq: Class defines compareTo(...) and uses Object.equals()
### Eq: equals method fails for subtypes
### Eq: Covariant equals() method defined
### FI: Empty finalizer should be deleted
### FI: Explicit invocation of finalizer
### FI: Finalizer nulls fields
### FI: Finalizer only nulls fields
### FI: Finalizer does not call superclass finalizer
### FI: Finalizer nullifies superclass finalizer
### FI: Finalizer does nothing but call superclass finalizer
### FS: Format string should use %n rather than \n
### GC: Unchecked type in generic call
### HE: Class defines equals() but not hashCode()
### HE: Class defines equals() and uses Object.hashCode()
### HE: Class defines hashCode() but not equals()
### HE: Class defines hashCode() and uses Object.equals()
### HE: Class inherits equals() and uses Object.hashCode()
### IC: Superclass uses subclass during initialization
### IMSE: Dubious catching of IllegalMonitorStateException
### ISC: Needless instantiation of class that only supplies static methods
### It: Iterator next() method can't throw NoSuchElementException
### J2EE: Store of non serializable object into HttpSession
### JCIP: Fields of immutable classes should be final
### ME: Public enum method unconditionally sets its field
### ME: Enum field is public and mutable
### NP: Method with Boolean return type returns explicit null
### NP: Clone method may return null
### NP: equals() method does not check for null argument
### NP: toString method may return null
### Nm: Class names should start with an upper case letter
### Nm: Class is not derived from an Exception, even though it is named as such
### Nm: Confusing method names
### Nm: Field names should start with a lower case letter
### Nm: Use of identifier that is a keyword in later versions of Java
### Nm: Use of identifier that is a keyword in later versions of Java
### Nm: Method names should start with a lower case letter
### Nm: Class names shouldn't shadow simple name of implemented interface
### Nm: Class names shouldn't shadow simple name of superclass
### Nm: Very confusing method names (but perhaps intentional)
### Nm: Method doesn't override method in superclass due to wrong package for parameter
### ODR: Method may fail to close database resource
### ODR: Method may fail to close database resource on exception
### OS: Method may fail to close stream
### OS: Method may fail to close stream on exception
### PZ: Don't reuse entry objects in iterators
### RC: Suspicious reference comparison to constant
### RC: Suspicious reference comparison of Boolean values
### RR: Method ignores results of InputStream.read()
### RR: Method ignores results of InputStream.skip()
### RV: Negating the result of compareTo()/compare()
### RV: Method ignores exceptional return value
### SI: Static initializer creates instance before all static final fields assigned
### SW: Certain swing methods needs to be invoked in Swing thread
### Se: Non-transient non-serializable instance field in serializable class
### Se: Non-serializable class has a serializable inner class
### Se: Non-serializable value stored into instance field of a serializable class
### Se: Comparator doesn't implement Serializable
### Se: Serializable inner class
### Se: serialVersionUID isn't final
### Se: serialVersionUID isn't long
### Se: serialVersionUID isn't static
### Se: Class is Serializable but its superclass doesn't define a void constructor
### Se: Class is Externalizable but doesn't define a void constructor
### Se: The readResolve method must be declared with a return type of Object
### Se: Transient field that isn't set by deserialization
### SnVI: Class is Serializable, but doesn't define serialVersionUID
### UI: Usage of GetResource may be unsafe if class is extended
