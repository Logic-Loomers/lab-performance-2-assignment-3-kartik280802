#include <iostream>
#include <vector>
using namespace std;

class Employee {
private:
    string name;
    int id;
    double hourlyRate;
    double hoursWorked;

public:
    Employee(string n, int i, double hR) : name(n), id(i), hourlyRate(hR), hoursWorked(0) {}
    string getName() { return name; }
    int getId() { return id; }
    double getHourlyRate() { return hourlyRate; }
    double getHoursWorked() { return hoursWorked; }
    void setHoursWorked(double h) { hoursWorked = h; }
    double calculateGrossPay() { return hourlyRate * hoursWorked; }
};

class Payroll {
private:
    vector<Employee> employees;

public:
    void addEmployee(Employee e) {
        employees.push_back(e);
    }
    double calculatePayroll() {
        double totalPayroll = 0.0;
        for (Employee e : employees) {
            totalPayroll += e.calculateGrossPay();
        }
        return totalPayroll;
    }
    void setEmployeeHoursWorked(int index, double hours) {
        if (index >= 0 && index < employees.size()) {
            employees[index].setHoursWorked(hours);
        }
    }
    void generatePayrollReport() {
        cout << "Employee Payroll Report\n";
        for (Employee e : employees) {
            cout << "Name: " << e.getName() << "\n";
            cout << "ID: " << e.getId() << "\n";
            cout << "Hourly Rate: " << e.getHourlyRate() << "\n";
            cout << "Hours Worked: " << e.getHoursWorked() << "\n";
            cout << "Gross Pay: " << e.calculateGrossPay() << "\n\n";
        }
        cout << "Total Payroll: " << calculatePayroll() << "\n";
    }
};

int main() {
    Employee e1("Kartik", 123, 45.5);
    Employee e2("Vishesh", 456, 72.0);
    Payroll payroll;
    payroll.addEmployee(e1);
    payroll.addEmployee(e2);
    payroll.setEmployeeHoursWorked(0, 40);
    payroll.setEmployeeHoursWorked(1, 37.5);
    payroll.generatePayrollReport();
    return 0;
}
