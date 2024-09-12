```csharp
// Andrew Engle
// HoursAndMinutes

/*

Requirements: 

Write a program named HoursAndMinutes that declares a minutes variable to represent minutes worked on a job, and assign a value to it.
Display the value in hours and minutes. For example, if 98 is assigned to the minutes variable, the output would be: 98 minutes is 1 hours and 38 minutes.
Note: For final submission assign 197 to the minutes variable

*/

/*
 Improved it to take user input instead of hard coded values. 
*/

// The other using directives are hidden by Visual Studio
/*
    global using global::System;
    global using global::System.Collections.Generic;
    global using global::System.IO;
    global using global::System.Linq;
    global using global::System.Net.Http;
    global using global::System.Threading;
    global using global::System.Threading.Tasks;
 */
using static System.Console;

namespace HoursAndMinutes {
    internal class Program {
        static void Main(string[] args) {
            const int MINUTES_PER_HOUR = 60; // Define conversion constant.

            int minutes; // Store ref to minutes in upper scope.
            int hours; // Store ref to hours in upper scope.
            double minutesLeftOver; // Store minutesLeftOver in upper scope.

            do { // Do while to guarntee excution of at lease 1 cycle. However we could have used a while(true) do instead since the conditional is not used.
                WriteLine("Enter time in minutes (-1 to Exit): "); // Prompt the user.
                if (int.TryParse(ReadLine(), out minutes)) { // TryParse is similar to parse but handles null/invalid input. Returns a bool indicating success or failure. 
                    // the out keyword which we have not gotten to yet, forces pass by reference.
                    // Instead of passing the value of minutes we are passing the memory reference of minutes to TryParse.
                    // TryParse will then set the value of this reference to the int value it pulled from the userinput string.

                    // Terminate the loop if exit statement encountered
                    if (minutes == -1) { 
                        break;
                    }

                    // Calculate hours from minutes (as an int).
                    hours = minutes / MINUTES_PER_HOUR;

                    // Calculate the remainder (as an int).
                    minutesLeftOver = minutes % MINUTES_PER_HOUR;

                    // Display output.
                    WriteLine($"{minutes} is {hours} hours and {minutesLeftOver} minutes");
                } else {
                    // Prompt the user to try again because TryParse failed to extract an int.
                    WriteLine("Could not parse input, please try again!");
                }
            } while (true);
            // Always true, loop will continue, we use break to terminate if needed.
        }
    }
}

```
