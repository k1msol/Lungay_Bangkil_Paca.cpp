# Lungay_Bangkil_Paca.cpp
#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

// ===== Function Prototypes =====
float calculateAverage(float g1, float g2, float g3, float g4, float g5);
float findHighest(float g1, float g2, float g3, float g4, float g5);
float findLowest(float g1, float g2, float g3, float g4, float g5);
float getGrade(float average);
int countPassing(float g1, float g2, float g3, float g4, float g5);

// Advanced Features
float convertGWA(float average);
bool isDirectorsList(float gwa);
float inputGrade(string subject);

// ====== MAIN ======
int main() {
    // Student Profile
    string studentName, studentID;
    int age, gradeLevel;

    cout << "========================================\n";
    cout << "        STUDENT GRADE CALCULATOR\n";
    cout << "========================================\n";

    cout << "\n=== STUDENT PROFILE SETUP ===\n";
    cout << "Enter student name: ";
    getline(cin, studentName);
    cout << "Enter student ID: ";
    cin >> studentID;
    cout << "Enter student age: ";
    cin >> age;
    cout << "Enter grade level: ";
    cin >> gradeLevel;

    int birthYear = 2025 - age; // Assume current year is 2025

    cout << "\nProfile created successfully!\n";

    // === Grade Entry ===
    cout << "\n=== GRADE ENTRY ===\n";
    float mathGrade = inputGrade("Math");
    float scienceGrade = inputGrade("Science");
    float englishGrade = inputGrade("English");
    float historyGrade = inputGrade("History");
    float artGrade = inputGrade("Art");

    cout << "\nGrades recorded successfully!\n";

    // === Calculations ===
    float average = calculateAverage(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    float highest = findHighest(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    float lowest = findLowest(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    int passingCount = countPassing(mathGrade, scienceGrade, englishGrade, historyGrade, artGrade);
    float gwa = convertGWA(average);
    bool dlStatus = isDirectorsList(gwa);

    // === Report Card Output ===
    cout << "\n========================================\n";
    cout << "           STUDENT REPORT CARD\n";
    cout << "========================================\n\n";

    cout << "STUDENT INFORMATION:\n";
    cout << "Name: " << studentName << endl;
    cout << "ID: " << studentID << endl;
    cout << "Age: " << age << " years old\n";
    cout << "Grade Level: " << gradeLevel << "th Grade\n";
    cout << "Birth Year: " << birthYear << endl;

    cout << "\nSUBJECT GRADES:\n";
    cout << "Math: " << mathGrade << "%\n";
    cout << "Science: " << scienceGrade << "%\n";
    cout << "English: " << englishGrade << "%\n";
    cout << "History: " << historyGrade << "%\n";
    cout << "Art: " << artGrade << "%\n";

    cout << fixed << setprecision(2);

    cout << "\nGRADE STATISTICS:\n";
    cout << "Average Grade: " << average << "%\n";
    cout << "Grade Equivalent: " << getGrade(average) << endl;
    cout << "Highest Grade: " << highest << "%\n";
    cout << "Lowest Grade: " << lowest << "%\n";
    cout << "Subjects Passing: " << passingCount << " out of 5\n";

    cout << "\nGWA: " << gwa << endl;
    cout << "Director's List Status: " 
         << (dlStatus ? "YES (Congratulations!)" : "NO") 
         << endl;

    return 0;
}

// ===== FUNCTION DEFINITIONS =====

// Average
float calculateAverage(float g1, float g2, float g3, float g4, float g5) {
    return (g1 + g2 + g3 + g4 + g5) / 5.0;
}

// Highest
float findHighest(float g1, float g2, float g3, float g4, float g5) {
    float highest = g1;
    if (g2 > highest) highest = g2;
    if (g3 > highest) highest = g3;
    if (g4 > highest) highest = g4;
    if (g5 > highest) highest = g5;
    return highest;
}

// Lowest
float findLowest(float g1, float g2, float g3, float g4, float g5) {
    float lowest = g1;
    if (g2 < lowest) lowest = g2;
    if (g3 < lowest) lowest = g3;
    if (g4 < lowest) lowest = g4;
    if (g5 < lowest) lowest = g5;
    return lowest;
}

// Grade Equivalent (1.0 - 5.0 scale)
float getGrade(float average) {
    if (average >= 96) return 1.0;
    else if (average >= 94) return 1.25;
    else if (average >= 92) return 1.5;
    else if (average >= 90) return 1.75;
    else if (average >= 88) return 2.0;
    else if (average >= 86) return 2.25;
    else if (average >= 84) return 2.5;
    else if (average >= 82) return 2.75;
    else if (average >= 80) return 3.0;
    else return 5.0;
}

// Passing Subjects
int countPassing(float g1, float g2, float g3, float g4, float g5) {
    int count = 0;
    if (g1 >= 60) count++;
    if (g2 >= 60) count++;
    if (g3 >= 60) count++;
    if (g4 >= 60) count++;
    if (g5 >= 60) count++;
    return count;
}

// GPA Converter (GWA)
float convertGWA(float average) {
    return getGrade(average);
}

// Director’s List Check
bool isDirectorsList(float gwa) {
    return (gwa <= 1.5);
}

// Input Validation
float inputGrade(string subject) {
    float grade;
    do {
        cout << "Enter " << subject << " grade (0-100): ";
        cin >> grade;
        if (grade < 0 || grade > 100) {
            cout << "Invalid input! Please enter a value between 0 and 100.\n";
        }
    } while (grade < 0 || grade > 100);
    return grade;
}

Comments:
1.	GPA Converter – This feature converts the student’s average grade percentage into the Grade Weighted Average (GWA) using the 1.0–5.0 scale based on the conversion chart.
2.	Director’s List Check – This feature checks if the student’s GWA qualifies for the Director’s List (GWA ≤ 1.5). If the requirement is met, the program displays a congratulatory message.
3.	Input Validation – This feature ensures that all entered grades are valid by requiring values between 0 and 100. If the input is invalid, the program keeps asking until the user enters a correct grade.
