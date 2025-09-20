import java.util.*;

class Employee {
    private int id;
    private String name;
    private double basicSalary;
    private double hra;
    private double da;
    private double deductions;

    public Employee(int id, String name, double basicSalary, double hra, double da, double deductions) {
        this.id = id;
        this.name = name;
        this.basicSalary = basicSalary;
        this.hra = hra;
        this.da = da;
        this.deductions = deductions;
    }

    public double calculateGrossSalary() {
        return basicSalary + hra + da;
    }

    public double calculateNetSalary() {
        return calculateGrossSalary() - deductions;
    }

    public void displayDetails() {
        System.out.println("====================================");
        System.out.println("Employee ID: " + id);
        System.out.println("Name       : " + name);
        System.out.println("Basic Pay  : " + basicSalary);
        System.out.println("HRA        : " + hra);
        System.out.println("DA         : " + da);
        System.out.println("Deductions : " + deductions);
        System.out.println("Gross Pay  : " + calculateGrossSalary());
        System.out.println("Net Salary : " + calculateNetSalary());
        System.out.println("====================================");
    }
}

public class PayrollManagement {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        List<Employee> employees = new ArrayList<>();

        System.out.print("Enter number of employees: ");
        int n = sc.nextInt();

        for (int i = 0; i < n; i++) {
            System.out.println("\nEnter details for employee " + (i+1) + ":");
            System.out.print("ID: ");
            int id = sc.nextInt();
            sc.nextLine(); // consume newline
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Basic Salary: ");
            double basic = sc.nextDouble();
            System.out.print("HRA: ");
            double hra = sc.nextDouble();
            System.out.print("DA: ");
            double da = sc.nextDouble();
            System.out.print("Deductions: ");
            double deductions = sc.nextDouble();

            employees.add(new Employee(id, name, basic, hra, da, deductions));
        }

        System.out.println("\n--- Payroll Details ---");
        for (Employee emp : employees) {
            emp.displayDetails();
        }
    }
}
