# ProcessDump
ProcessDump is a Windows reverse-engineering static lib to dump malware memory components back to disk for analysis. Often malware files are packed and obfuscated before they are executed in order to avoid AV scanners, however when these files are executed they will often unpack or inject a clean version of the malware code in memory. A common task for malware researchers when analyzing malware is to dump this unpacked code back from memory to disk for scanning with AV products or for analysis with static analysis tools such as IDA.

Process Dump works for Windows 32 and 64 bit operating systems and can dump memory components from specific processes or from all processes currently running. 

# Compiling source code
This is designed for Visual Studio 2017 and works with the free Community edition. Just open the project file with VS2017 and compile, it should be that easy!

# Example Usage

Dump all modules and hidden code chunks from a specific process identifier:
* void ProcessDumpById(unsigned long pid, wchar_t* output_folder);

Dump all modules and hidden code chunk by process name:
* void ProcessDumpById(unsigned long pid, wchar_t* output_folder);
