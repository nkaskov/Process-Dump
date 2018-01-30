# Process Dump
Process Dump is a Windows reverse-engineering command-line tool to dump malware memory components back to disk for analysis. Often malware files are packed and obfuscated before they are executed in order to avoid AV scanners, however when these files are executed they will often unpack or inject a clean version of the malware code in memory. A common task for malware researchers when analyzing malware is to dump this unpacked code back from memory to disk for scanning with AV products or for analysis with static analysis tools such as IDA.

Process Dump works for Windows 32 and 64 bit operating systems and can dump memory components from specific processes or from all processes currently running. Process Dump supports creation and use of a clean-hash database, so that dumping of all the clean files such as kernel32.dll can be skipped. It's main features include:
* Dumps code from a specific process or all processes.
* Finds and dumps hidden modules that are not properly loaded in processes.
* Finds and dumps loose code chunks even if they aren't associated with a PE file. It builds a PE header and import table for the chunks.
* Reconstructs imports using an aggressive approach.
* Can run in close dump monitor mode ('-closemon'), where processes will be paused and dumped just before they terminate.
* Multi-threaded, so when you are dumping all running processes it will go pretty quickly.
* Can generate a clean hash database. Generate this before a machine is infected with malware so Process Dump will only dump the new malicious malware components.

I'm maintaining an official compiled release on my website here:
  http://split-code.com/processdump.html

# Compiling source code
This is designed for Visual Studio 2017 and works with the free Community edition. Just open the project file with VS2017 and compile, it should be that easy!

# Example Usage

Dump all modules and hidden code chunks from a specific process identifier:
* void ProcessDumpById(unsigned long pid, wchar_t* output_folder);

Dump all modules and hidden code chunk by process name:
* void ProcessDumpById(unsigned long pid, wchar_t* output_folder);



# Help Page
Process Dump v2.1
  Copyright ® 2017, Geoff McDonald
  http://www.split-code.com/

Process Dump (pd.exe) is a tool used to dump both 32 and 64 bit executable modules back to disk from memory within a process address space. This tool is able to find and dump hidden modules as well as loose executable code chunks, and it uses a clean hash database to exclude dumping of known clean files. This tool uses an aggressive import reconstruction approach that links all DWORD/QWORDs that point to an export in the process to the corresponding export function. Process dump can be used to dump all unknown code from memory ('-system' flag), dump specific processes, or run in a monitoring mode that dumps all processes just before they terminate.
