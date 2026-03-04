# OOP-Group7
Pushing an Encapsulation code for MotorPH.

// Concept Code: Encapsulation in MotorPH Payroll System
public class Employee {
    // Private fields (hidden from outside classes)
    private String employeeId;
    private String name;
    private double basicSalary;
    private double hourlyRate;
    private double hoursWorked;
    private double deductions;

    // Constructor
    public Employee(String employeeId, String name, double basicSalary, double hourlyRate) {
        this.employeeId = employeeId;
        this.name = name;
        setBasicSalary(basicSalary);   // validation applied
        setHourlyRate(hourlyRate);     // validation applied
        this.hoursWorked = 0;
        this.deductions = 0;
    }

    // Encapsulated Getters and Setters with Validation
    public double getBasicSalary() {
        return basicSalary;
    }

    public void setBasicSalary(double salary) {
        if (salary >= 0) {
            this.basicSalary = salary;
        } else {
            throw new IllegalArgumentException("Salary must be >= 0");
        }
    }

    public double getHourlyRate() {
        return hourlyRate;
    }

    public void setHourlyRate(double rate) {
        if (rate > 0) {
            this.hourlyRate = rate;
        } else {
            throw new IllegalArgumentException("Hourly rate must be > 0");
        }
    }

    public void addHoursWorked(double hours) {
        if (hours >= 0) {
            this.hoursWorked += hours;
        } else {
            throw new IllegalArgumentException("Hours worked cannot be negative");
        }
    }

    public void setDeductions(double deductions) {
        if (deductions >= 0) {
            this.deductions = deductions;
        } else {
            throw new IllegalArgumentException("Deductions cannot be negative");
        }
    }

    // Business Logic Methods
    public double calculateGrossSalary() {
        return basicSalary + (hourlyRate * hoursWorked);
    }

    public double calculateNetSalary() {
        double gross = calculateGrossSalary();
        if (deductions <= gross) {
            return gross - deductions;
        } else {
            throw new IllegalArgumentException("Deductions cannot exceed gross salary");
        }
    }

    // Controlled access to employee profile
    public String viewProfile() {
        return "Employee ID: " + employeeId + "\nName: " + name +
               "\nGross Salary: " + calculateGrossSalary() +
               "\nNet Salary: " + calculateNetSalary();
    }
}


