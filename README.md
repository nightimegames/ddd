[SIZE="6"][FONT="Franklin Gothic Medium"][B]CS:GO Cheat Making 101[/B][/FONT][/SIZE]
[B][I]
NOTE: This guide is still a HUGE work in progress. You can use the GitHub repo to push commits in order to modify and update this guide. Your help is important! [URL="https://github.com/DoubleHub/CSGOCheatMaking101/blob/master/Guide.txt"]*CLICK*[/URL][/I][/B]
 [B][I]Structure of the guide:[/I][/B] (prone to changes)
[B]Chapter 0[/B] ~ Welcome to CS:GO Cheat Making 101! The requirements
[B]Chapter 1[/B] ~ Explaining CS:GO
[I]Chapter 1.1[/I] ~ Brief introduction to the Source Engine
[I]Chapter 1.2[/I] ~ Different types of cheats
[I]Chapter 1.3[/I] ~ Talking about VAC: Ring0 and Ring3 (OPTIONAL)
[B]Chapter 2[/B] ~ External Cheats: The starting point
[I]Chapter 2.1[/I] ~ Brief introduction to WinAPI
[I]Chapter 2.2[/I] ~ Managing CS:GO memory: RPM and WPM
[I]Chapter 2.3[/I] ~ Getting CS:GO module info
[I]Chapter 2.4[/I] ~ Building a memory management class
[B]Chapter 3[/B] ~ Offsets
[I]Chapter 3.1[/I] ~ Using our class and the offsets to make our first bhop
[I]Chapter 3.2[/I] ~ Netvars
[I]Chapter 3.3[/I] ~ Getting offsets dynamically: Pattern Scanning
[I]Chapter 3.4[/I] ~ Getting netvars dynamically: Netvar Managers and recursion
[B]Chapter 4[/B] ~ Internal Cheats: The advantages
[I]Chapter 4.1[/I] ~ Calling exported module functions
[I]Chapter 4.2[/I] ~ CreateInterface: Getting those interfaces
[I]Chapter 4.3[/I] ~ Hooking methods: VMT hooking
[I]Chapter 4.4[/I] ~ A look at the Source SDK
[I]Chapter 4.5[/I] ~ Common functions to hook
[I]Chapter 4.6[/I] ~ A look at CreateMove: Making our first internal bhop
[I]Chapter 4.7[/I] ~ Drawing using ISurface
 [SIZE="5"][FONT="Franklin Gothic Medium"][B]Chapter 0[/B][/FONT][/SIZE]
[SIZE="4"][FONT="Franklin Gothic Medium"][B]Welcome to CS:GO Cheat Making 101! The requirements[/B][/FONT][/SIZE]
# CS:GO Cheat Making 101
 NOTE: This guide is still a HUGE work in progress. You can use the GitHub repo to push commits in order to modify and update this guide. Your help is important!
 ## Structure of the guide: (prone to changes)
- [Chapter 0 ~ Welcome to CS:GO Cheat Making 101! The requirements](#chapter-0)
- [Chapter 1 ~ Explaining CS:GO](#chapter-1)
  - [Chapter 1.1 ~ Brief introduction to the Source Engine](#brief-introduction-to-the-source-engine)
  - [Chapter 1.2 ~ Different types of cheats](#different-types-of-cheats)
  - [Chapter 1.3 ~ Talking about VAC: Ring0 and Ring3 (OPTIONAL)](#talking-about-vac-ring0-and-ring3-optional)
- [Chapter 2 ~ External Cheats: The starting point](#chapter-2)
  - [Chapter 2.1 ~ Brief introduction to the WinAPI](#brief-introduction-to-the-winapi)
  - [Chapter 2.2 ~ Managing CS:GO memory: RPM and WPM](#managing-cs-go-memory-rpm-and-wpm)
  - [Chapter 2.3 ~ Getting CS:GO module infos](#getting-cs-go-module-infos)
  - [Chapter 2.4 ~ Building a memory management class](#building-a-memory-management-class)
- [Chapter 3 ~ Offsets](#chapter-3)
  - [Chapter 3.1 ~ Using our class and the offsets to make our first bhop](#using-our-class-and-the-offsets-to-make-our-first-bhop)
  - [Chapter 3.2 ~ Netvars](#netvars)
  - [Chapter 3.3 ~ Getting offsets dynamically: Pattern Scanning](#getting-offsets-dynamically-pattern-scanning)
  - [Chapter 3.4 ~ Getting netvars dynamically: Netvar Managers and recursion](#getting-netvars-dynamically-netvar-managers-and-recursion)
- Chapter 4 ~ Internal Cheats: The advantages
  - Chapter 4.1 ~ Calling exported module functions
  - Chapter 4.2 ~ CreateInterface: Getting those interfaces
  - Chapter 4.3 ~ Hooking methods: VMT hooking
  - Chapter 4.4 ~ A look at the Source SDK
  - Chapter 4.5 ~ Common functions to hook
  - Chapter 4.6 ~ A look at CreateMove: Making our first internal bhop
  - Chapter 4.7 ~ Drawing using ISurface
 ## [Chapter 0](#chapter-0)
### Welcome to CS:GO Cheat Making 101! The requirements
 Hi and welcome to CS:GO Cheat Making 101, a "all-in-one" guide for CS:GO cheat making! Please notice that this guide is still a huge work in progress and it is prone to changes. Since I'm not really pro when it comes to CS:GO cheat making, I'd like you guys to help me building this guide and expanding it as large as possible. I'll cover a lot (but not all) of aspects of CS:GO cheats and I'll try to be as clear as possible.
 @@ -37,20 +37,25 @@ Some people here even learnt a programming language by making CS:GO cheats, stil
 I'm not writing this guide with the purpose of showing my (near to no) knownledge about this stuff. I'm writing this guide as a starting point to many ppl out there trying to start in this sector. As I said some months ago, all I needed when I started here was a really solid base to learn from. In order to make this guide the best and the most complete guide about CS:GO cheat making, I need your help. The help of people with a real huge experience in this sector, that would be really great and you'll sort of help this community. :asskiss:
 [SIZE="5"][FONT="Franklin Gothic Medium"][B]Chapter 1[/B][/FONT][/SIZE]
[SIZE="4"][FONT="Franklin Gothic Medium"][B]Explaining CS:GO[/B][/FONT][/SIZE]
## [Chapter 1](#chapter-1)
### Explaining CS:GO
 [B]C[/B]ounter [B]S[/B]trike: [B]G[/B]lobal [B]O[/B]ffensive (aka CS:GO), as many of you know, is a first person shooter game with a lot of focus on the competitive aspect. The game requires a certain set of skills and ability to pwn your enemies, and when it comes to skill we all know that... we'll come to cheats! CS:GO is probably one of the most (if not the most) full of cheaters paid game, and the creators (Valve + Hidden Path Entertainment) can't do anything for it. Throughout the various updates of the game, they've released several ways and workarounds to trying stopping cheaters (always failing), but in the end we all know that they won't stop cheaters, for obvious money reasons. Getting a cheap CS:GO copy is really easy, as it is really easy to cheat. There are near to no protections compared to other paid games (well, don't take me wrong, there are some cheap protections like untrusted checks but...) and the community itself is full of cheaters. Just for example, this section of UC is probably one of the most visited and active UC sections (mods, get ready to prove the opposite).
**C**ounter **S**trike: **G**lobal **O**ffensive (aka CS:GO), as many of you know, is a first person shooter game with a lot of focus on the competitive aspect. The game requires a certain set of skills and ability to pwn your enemies, and when it comes to skill we all know that... we'll come to cheats! CS:GO is probably one of the most (if not the most) full of cheaters paid game, and the creators (Valve + Hidden Path Entertainment) can't do anything for it. Throughout the various updates of the game, they've released several ways and workarounds to trying stopping cheaters (always failing), but in the end we all know that they won't stop cheaters, for obvious money reasons. Getting a cheap CS:GO copy is really easy, as it is really easy to cheat. There are near to no protections compared to other paid games (well, don't take me wrong, there are some cheap protections like untrusted checks but...) and the community itself is full of cheaters. Just for example, this section of UC is probably one of the most visited and active UC sections (mods, get ready to prove the opposite).
 But we are not here to talk about how full of cheaters CS:GO is, we are here to learn about making a cheat! This forum is full of references, tutorials, sources about how to make certain stuff for CS:GO, infact I'll put at the end of each chapter a little list of reference links which I really recommend to read to get deeper on the concept explained in the chapter.
 Reference links for this section:
[url]http://www.unknowncheats.me/wiki/Counter-Strike:_Global_Offensive[/url]
[url]https://en.wikipedia.org/wiki/Counter-Strike:_Global_Offensive[/url]
[url]https://en.wikipedia.org/wiki/Valve_Corporation[/url]
[url]https://en.wikipedia.org/wiki/Hidden_Path_Entertainment[/url]
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Brief introduction to the Source Engine[/B][/I][/FONT][/SIZE]
http://www.unknowncheats.me/wiki/Counter-Strike:_Global_Offensive
 https://en.wikipedia.org/wiki/Counter-Strike:_Global_Offensive
 https://en.wikipedia.org/wiki/Valve_Corporation
 https://en.wikipedia.org/wiki/Hidden_Path_Entertainment
 #### [Brief introduction to the Source Engine](#brief-introduction-to-the-source-engine)
 CS:GO runs on the Source Engine, a really famous game engine used to make a lot of games that we all know and love (a prime example is Half Life or Left 4 Dead).
The Source is well known for his great physics system (that we saw in action in HL) but in general it is a great engine to make games on. Another great advantage is his flexibility, which makes the life of modders way easier.
@@ -59,22 +64,27 @@ It is greatly documented on internet and here, and it's (only in part) open sour
Since CS:GO is built upon the Source Engine, a large part of what we'll do to modify the game (to get an advantage) is related to it, especially when we are going internal.
 Reference links for this section:
[url]http://www.unknowncheats.me/wiki/Source_Engine[/url]
[url]https://en.wikipedia.org/wiki/Source_(game_engine)[/url]
[url]https://developer.valvesoftware.com/wiki/SDK_Docs[/url]
[url]https://github.com/ValveSoftware/source-sdk-2013[/url]
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Different types of cheats[/B][/I][/FONT][/SIZE]
http://www.unknowncheats.me/wiki/Source_Engine
 https://en.wikipedia.org/wiki/Source_(game_engine)
 https://developer.valvesoftware.com/wiki/SDK_Docs
 https://github.com/ValveSoftware/source-sdk-2013
 #### [Different types of cheats](#different-types-of-cheats)
 Before getting into cheat making, it's important to know what are we going to do.
Usually (not only for CS:GO) there are 2 types of cheats: Internals and Externals.
The difference between those two types is huge:
 An [B]EXTERNAL[/B] cheat is an [B]EXE[/B] which is able, through an HANDLE (think it like a bridge) to CS:GO process, to read and write memory. By reading and writing certain areas of memory we are able to make our cheats.
An **EXTERNAL** cheat is an **EXE** which is able, through an HANDLE (think it like a bridge) to CS:GO process, to read and write memory. By reading and writing certain areas of memory we are able to make our cheats.
The main disadvantage of externals is the fact that we are not in sync with the game's thread, which can lead to "unexpected" results (a prime example are external skinchangers, since they are not in sync with the game's thread you won't achieve consistency especially when trying to change the knife model).
We are also forced to read and write through specific functions (we'll see later) that are heavy to call.
 An [B]INTERNAL[/B] cheat is a [B]DLL[/B] which is injected directly into CS:GO and it is able to directly read and write CS:GO memory, through raw pointers. Internally, we can also get interfaces and call virtual functions, which makes our lives way easier. We can also hook some functions to kind of "redirect" them and make them doing what we want.
An **INTERNAL** cheat is a **DLL** which is injected directly into CS:GO and it is able to directly read and write CS:GO memory, through raw pointers. Internally, we can also get interfaces and call virtual functions, which makes our lives way easier. We can also hook some functions to kind of "redirect" them and make them doing what we want.
 There is still an open discussion about what type of cheat is the most detectable.
 @@ -83,30 +93,37 @@ There is another type of cheat, called "Internal/External", which is basically a
We'll start with external, which are easier to learn but hard to master, while internal cheats are hard to learn... but easy to master!
 Reference links for this section:
[URL="http://www.unknowncheats.me/forum/counterstrike-global-offensive/151797-ezfrags-cs-multihack-public-rage-legit.html"]An example of an external cheat (EZFrags)[/URL]
[URL="http://www.unknowncheats.me/forum/counterstrike-global-offensive/183376-fx-cs-public-release.html"]An example of an internal cheat (FX)[/URL]
[URL="http://www.unknowncheats.me/forum/counterstrike-global-offensive/159299-internal-external-customizable-multi-hack.html"]An example of an internal/external cheat[/URL]
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Talking about VAC: Ring0 and Ring3 (OPTIONAL)[/B][/I][/FONT][/SIZE]
[I]
You can skip this chapter without any kind of problem.
[An example of an external cheat (EZFrags)](http://www.unknowncheats.me/forum/counterstrike-global-offensive/151797-ezfrags-cs-multihack-public-rage-legit.html)
 [An example of an internal cheat (FX)](http://www.unknowncheats.me/forum/counterstrike-global-offensive/183376-fx-cs-public-release.html)
 [An example of an internal/external cheat](http://www.unknowncheats.me/forum/counterstrike-global-offensive/159299-internal-external-customizable-multi-hack.html)
 (NOTE: I may say something wrong or bullshit in this specific section. VAC experts and kernel mode experts, help me! <3)[/I]
#### [Talking about VAC: Ring0 and Ring3 (OPTIONAL)](#talking-about-vac-ring0-and-ring3-optional)
_You can skip this chapter without any kind of problem._
 The main anticheat that CS:GO is using is the [B]V[/B]alve [B]A[/B]nti-[B]C[/B]heat (aka VAC), which is supposed to block cheaters but we all know that it fails miserably. Basically, the VAC is a joke. You don't need to be too much afraid of it since it won't bust you if you aren't using a public cheat. The VAC is using signature scanning in order to detect cheats. When a cheat becomes detected by VAC it means that the VAC detected his signature (which is an unique identifier for something) and stored it in his database. When you are using a cheat with a detected signature, you are fucked (flagged).
_(NOTE: I may say something wrong or bullshit in this specific section. VAC experts and kernel mode experts, help me! :heart:)_
 The main anticheat that CS:GO is using is the **V**alve **A**nti-**C**heat (aka VAC), which is supposed to block cheaters but we all know that it fails miserably. Basically, the VAC is a joke. You don't need to be too much afraid of it since it won't bust you if you aren't using a public cheat. The VAC is using signature scanning in order to detect cheats. When a cheat becomes detected by VAC it means that the VAC detected his signature (which is an unique identifier for something) and stored it in his database. When you are using a cheat with a detected signature, you are fucked (flagged).
VAC bans are completely automatic and can take a lot of time to ban you, because it needs to know 100% that you are cheating, in order to avoid false positives.
 You have to know about Ring0 and Ring3 to get a feeling about how VAC is a real joke. Basically, Intel processors (x86 but also others) to protect critical resources like IO, memory, ports, etc provide some privilege levels (0 being most privilege and 3 being last) aka UserMode and KernelMode.
So, the OS runs kernel code in Ring0, and user code in Ring3.
VAC operates in Ring3. Basically, if you make a Ring0 cheat you are good to go. But if you are capable of making a Ring0 cheat then all of this stuff should be a piece of cake at your eyes, you can leave.
 Reference links for this section:
[url]https://en.wikipedia.org/wiki/Valve_Anti-Cheat[/url]
[url]http://duartes.org/gustavo/blog/post/cpu-rings-privilege-and-protection/[/url]
[url]https://en.wikipedia.org/wiki/Protection_ring[/url]
 [SIZE="5"][FONT="Franklin Gothic Medium"][B]Chapter 2[/B][/FONT][/SIZE]
[SIZE="4"][FONT="Franklin Gothic Medium"][B]External Cheats: The starting point[/B][/FONT][/SIZE]
https://en.wikipedia.org/wiki/Valve_Anti-Cheat
 http://duartes.org/gustavo/blog/post/cpu-rings-privilege-and-protection/
 https://en.wikipedia.org/wiki/Protection_ring
 ## [Chapter 2](#chapter-2)
### External Cheats: The starting point
 We'll focus, for now, on external cheats, which you now know what they do (ref: 1.2 Different types of cheats)
Writing external cheats serves as a really good starting point in this sector because externals are way more documented than internals and they are way easier to code and understand.
@@ -117,47 +134,61 @@ An external cheat, however, isn't forced to manage CS:GO memory. For example, yo
In the end, it's all a matter of consistency.
 Reference links for this section:
[URL="http://www.unknowncheats.me/forum/counterstrike-global-offensive/147103-peans-ahk-triggerbot-aka-colorbot-extension.html"]An example of color triggerbot, not interacting with CS:GO memory[/URL]
[URL="http://www.unknowncheats.me/forum/counterstrike-global-offensive/168179-simple-bunny-hop-script.html"]An example of a really basic bhop, interacting with CS:GO memory (by me)[/URL]
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Brief introduction to the WinAPI[/B][/I][/FONT][/SIZE]
[An example of color triggerbot, not interacting with CS:GO memory](http://www.unknowncheats.me/forum/counterstrike-global-offensive/147103-peans-ahk-triggerbot-aka-colorbot-extension.html)
 [An example of a really basic bhop, interacting with CS:GO memory (by me)](http://www.unknowncheats.me/forum/counterstrike-global-offensive/168179-simple-bunny-hop-script.html)
 I've stated multiple times that we need to manage CS:GO memory in order to achieve certain results with our external cheats. But how? The answer has got a name: The [B]Win[/B]dows [B]A[/B]pplication [B]P[/B]rogramming [B]I[/B]nterface! (aka WinAPI)
#### [Brief introduction to the WinAPI](#brief-introduction-to-the-winapi)
 The Windows OS allows us to use the WinAPI, which (basically speaking) is a set of C functions and structs implemented in [B]D[/B]ynamic [B]L[/B]ink [B]L[/B]ibraries (aka DLL). Don't get me wrong, you can still mix your C++ code style with the usage of WinAPI.
There are, as you may know, three main groups of API: Kernel, [B]G[/B]raphics [B]D[/B]evice [B]I[/B]nterface (aka GDI) and User. You can find more infos about those 3 types on the reference links I'm going to provide, if you want to get deeper.
I've stated multiple times that we need to manage CS:GO memory in order to achieve certain results with our external cheats. But how? The answer has got a name: The **Win**dows **A**pplication **P**rogramming **I**nterface! (aka WinAPI)
 The Windows OS allows us to use the WinAPI, which (basically speaking) is a set of C functions and structs implemented in **D**ynamic **L**ink **L**ibraries (aka DLL). Don't get me wrong, you can still mix your C++ code style with the usage of WinAPI.
There are, as you may know, three main groups of API: Kernel, **G**raphics **D**evice **I**nterface (aka GDI) and User. You can find more infos about those 3 types on the reference links I'm going to provide, if you want to get deeper.
 Now that we know what we are going to mainly use in our externals, we can start talking about practically managing the CS:GO memory!
 Reference links for this section:
[url]https://en.wikipedia.org/wiki/Windows_API[/url]
[url]https://msdn.microsoft.com/en-us/library/cc433218(VS.85).aspx[/url]
[url]http://www.infernodevelopment.com/c-win32-api-tutorial[/url]
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Managing CS:GO memory: RPM and WPM[/B][/I][/FONT][/SIZE]
https://en.wikipedia.org/wiki/Windows_API
 https://msdn.microsoft.com/en-us/library/cc433218(VS.85).aspx
 http://www.infernodevelopment.com/c-win32-api-tutorial
 #### <a href="#managing-cs-go-memory-rpm-and-wpm" name="managing-cs-go-memory-rpm-and-wpm">Managing CS:GO memory: RPM and WPM</a>
 We're going to use a lot of stuff from the WinAPI to get the results we want, and for sure the functions that we are going to use the most are the actual functions to read and write process memory.
Those two functions are [B]R[/B]ead[B]P[/B]rocess[B]M[/B]emory and [B]W[/B]rite[B]P[/B]rocess[B]M[/B]emory (aka RPM and WPM).
Those two functions are **R**ead**P**rocess**M**emory and **W**rite**P**rocess**M**emory (aka RPM and WPM).
Let's see how we work with these two functions, I'll start with ReadProcessMemory.
Based on the MSDN page of RPM, the function prototype is:
 [CODE]
````cpp
BOOL WINAPI ReadProcessMemory(
  _In_  HANDLE  hProcess,
  _In_  LPCVOID lpBaseAddress,
  _Out_ LPVOID  lpBuffer,
  _In_  SIZE_T  nSize,
  _Out_ SIZE_T  *lpNumberOfBytesRead
    _In_  HANDLE  hProcess,
    _In_  LPCVOID lpBaseAddress,
    _Out_ LPVOID  lpBuffer,
    _In_  SIZE_T  nSize,
    _Out_ SIZE_T  *lpNumberOfBytesRead
);
[/CODE]
````
 [I]"_In_  HANDLE  hProcess"[/I]
_"\_In\_  HANDLE  hProcess"_
 The first argument, the hProcess, is the actual [URL="https://msdn.microsoft.com/en-us/library/windows/desktop/ms724176(v=vs.85).aspx"]HANDLE[/URL] to the process we need to read memory from. Remember what I said in 1.2? In external cheats we use an HANDLE (like a bridge) to read and write memory.
The first argument, the hProcess, is the actual [HANDLE](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724176(v=vs.85).aspx)
 to the process we need to read memory from. Remember what I said in 1.2? In external cheats we use an HANDLE (like a bridge) to read and write memory.
In order to get this HANDLE you've got several ways. 
The most used way is to loop through all the process through [URL="https://msdn.microsoft.com/en-us/library/windows/desktop/ms684836(v=vs.85).aspx"]Process32Next[/URL] (and [URL="https://msdn.microsoft.com/en-us/library/windows/desktop/ms684834(v=vs.85).aspx"]Process32First[/URL]), using the helper struct [URL="https://msdn.microsoft.com/en-us/library/windows/desktop/ms684839(v=vs.85).aspx"]PROCESSENTRY32[/URL], then in the loop comparing the current process name with the process name we are searching for, if the names are the same then we use the WinAPI function [URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms684320(v=vs.85).aspx"]OpenProcess[/URL] to open an handle to this process. Notice that, in order to be able to read and write, we will put the flag [URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms684880(v=vs.85).aspx"]PROCESS_ALL_ACCESS[/URL] in order to gain full privileges.
The most used way is to loop through all the process through [Process32Next](https://msdn.microsoft.com/en-us/library/windows/desktop/ms684836(v=vs.85).aspx)
 (and [Process32First](https://msdn.microsoft.com/en-us/library/windows/desktop/ms684834(v=vs.85).aspx)
), using the helper struct [PROCESSENTRY32](https://msdn.microsoft.com/en-us/library/windows/desktop/ms684839(v=vs.85).aspx)
, then in the loop comparing the current process name with the process name we are searching for, if the names are the same then we use the WinAPI function [OpenProcess](https://msdn.microsoft.com/it-it/library/windows/desktop/ms684320(v=vs.85).aspx)
 to open an handle to this process. Notice that, in order to be able to read and write, we will put the flag [PROCESS_ALL_ACCESS](https://msdn.microsoft.com/it-it/library/windows/desktop/ms684880(v=vs.85).aspx)
 in order to gain full privileges.
 [B]REMEMBER! An HANDLE must always be closed through [URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms724211(v=vs.85).aspx"]CloseHandle[/URL] once it's not used anymore![/B]
**REMEMBER! An HANDLE must always be closed through [CloseHandle](https://msdn.microsoft.com/it-it/library/windows/desktop/ms724211(v=vs.85).aspx)
 once it's not used anymore!**
 This, however, is not the only way, of course. For example, if we are using managed languages like C# or VB.NET, there are way easier ways. However, I've explained the most common one.
 @@ -168,24 +199,35 @@ WPM has got the same arguments, the only difference is that the third argument i
RPM and WPM are not the only way to read and write process memory, it's just the most common one, since it's well documented and already implemented by the WinAPI itself. CS:GO doesn't detect WPM and RPM since a lot of legit processes use them constantly, and the anticheat (as I already stated) wants to avoid false positives.
 Reference links for this section:
[URL="http://pastebin.com/Bd6t5tcP"]Commented example of a common function to open an handle to a process (using WinAPI)[/URL]
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Getting CS:GO module infos[/B][/I][/FONT][/SIZE]
[Commented example of a common function to open an handle to a process (using WinAPI)](http://pastebin.com/Bd6t5tcP)
 One of the most useful things we can do in CS:GO memory is grabbing infos about a specific module (a DLL, like client.dll or engine.dll, but also others). When we'll get into offsets, you'll see how important is to know some stuff about different CS:GO modules. But how can we grab this useful info?
As always, there are several methods, one is really similar to the method that I've explained previously about opening the process handle. The only difference is that instead of using [URL="https://msdn.microsoft.com/en-us/library/windows/desktop/ms684839(v=vs.85).aspx"]PROCESSENTRY32[/URL] and related funcs like [URL="https://msdn.microsoft.com/en-us/library/windows/desktop/ms684834(v=vs.85).aspx"]Process32First[/URL] and [URL="https://msdn.microsoft.com/en-us/library/windows/desktop/ms684836(v=vs.85).aspx"]Process32Next[/URL], you have to use [URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms684225(v=vs.85).aspx"]MODULEENTRY32[/URL] to store info and [URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms684218(v=vs.85).aspx"]Module32First[/URL]/[URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms684221(v=vs.85).aspx"]Next[/URL] to loop through the module list.
 Another way is to use the [URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms684229(v=vs.85).aspx"]MODULEINFO[/URL] structure and [URL="https://msdn.microsoft.com/it-it/library/windows/desktop/ms683201(v=vs.85).aspx"]GetModuleInformation[/URL] function, really handy when it comes to this kind of stuff.
#### <a href="#getting-cs-go-module-infos" name="getting-cs-go-module-infos">Getting CS:GO module infos</a>
 One of the most useful things we can do in CS:GO memory is grabbing infos about a specific module (a DLL, like client.dll or engine.dll, but also others). When we'll get into offsets, you'll see how important is to know some stuff about different CS:GO modules. But how can we grab this useful info?
As always, there are several methods, one is really similar to the method that I've explained previously about opening the process handle. The only difference is that instead of using [PROCESSENTRY32](https://msdn.microsoft.com/en-us/library/windows/desktop/ms684839(v=vs.85).aspx)
 and related funcs like [Process32First](https://msdn.microsoft.com/en-us/library/windows/desktop/ms684834(v=vs.85).aspx)
 and [Process32Next](https://msdn.microsoft.com/en-us/library/windows/desktop/ms684836(v=vs.85).aspx)
, you have to use [MODULEENTRY32](https://msdn.microsoft.com/it-it/library/windows/desktop/ms684225(v=vs.85).aspx)
 to store info and [Module32First](https://msdn.microsoft.com/it-it/library/windows/desktop/ms684218(v=vs.85).aspx)
/[Next](https://msdn.microsoft.com/it-it/library/windows/desktop/ms684221(v=vs.85).aspx)
 to loop through the module list.
 Another way is to use the [MODULEINFO](https://msdn.microsoft.com/it-it/library/windows/desktop/ms684229(v=vs.85).aspx)
 structure and [GetModuleInformation](https://msdn.microsoft.com/it-it/library/windows/desktop/ms683201(v=vs.85).aspx)
 function, really handy when it comes to this kind of stuff.
 Now that we got the info that we want, we can use the base address of the module to access specific things (using offsets) in that module (we'll see, for example, grabbing the local player, or the local player health value).
Another useful thing to know is the module size, we'll see his importance when we'll talk about pattern scanning.
 Reference links for this section:
[URL="http://pastebin.com/GC9kTHcJ"]Commented example of a common function to get module info (using WinAPI)[/URL]
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Building a memory management class[/B][/I][/FONT][/SIZE]
[I]
(NOTE: This section is going to get really practical, with a lot of commented pieces of C++ source code. But no problems, it's optional! You can skip this if you really want it <3)[/I]
[Commented example of a common function to get module info (using WinAPI)](http://pastebin.com/GC9kTHcJ)
 #### [Building a memory management class](#building-a-memory-management-class)
_(NOTE: This section is going to get really practical, with a lot of commented pieces of C++ source code. But no problems, it's optional! You can skip this if you really want it :heart:)_
 Now that you know what we need to do in order to have fun within CS:GO memory, you can take it a step further and start to code an actual class to make everything easier to do. Our goal is to make a memory management class (aka MMC) that allows us to attach to a specific process and grab modules. It's also going to contain some useful template wrappers to WPM and RPM so everything is going to be easier.
 @@ -194,238 +236,267 @@ In this guide I'm going to use C++ as an example language, but that's not a prob
 So, let's go ahead, this class is going to contain some members, ofc!
 [CODE]
````cpp
class CMemoryManager
{
private: // Private members: We are going to setup some getters later on!
	HANDLE m_hProcess; // The HANDLE to the process to attach
	DWORD m_dwProcessId; // The Process Id of the process to attach
	std::vector<MODULEENTRY32> m_Modules; // std::vector containing all the modules we grab from the process
[/CODE]
private:                                   // Private members: We are going to setup some getters later on!
    HANDLE m_hProcess;                     // The HANDLE to the process to attach
    DWORD m_dwProcessId;                   // The Process Id of the process to attach
    std::vector<MODULEENTRY32> m_Modules;  // std::vector containing all the modules we grab from the process
````
 As you can see we've got [I]m_hProcess[/I] which is basically the HANDLE to the process to attach, [I]m_dwProcessId[/I] which is the process id of the process to attach and a basic std::vector of MODULEENTRY32 structs which is going to contain all the modules we grab from the attached process. We use an std::vector so it's easier to push back new elements (modules) without worrying too much about fixed sizes.
As you can see we've got _m_hProcess_ which is basically the HANDLE to the process to attach, _m_dwProcessId_ which is the process id of the process to attach and a basic std::vector of MODULEENTRY32 structs which is going to contain all the modules we grab from the attached process. We use an std::vector so it's easier to push back new elements (modules) without worrying too much about fixed sizes.
Now, let's make the public functions:
 [CODE]
        // Attach to a process based on strProcessName
	// Returns true on success, false on failure
	bool Attach(const std::string& strProcessName)
	{
	    // First of all we create a snapshot handle specific for processes
	    // (notice the usage of TH32CS_SNAPPROCESS) so we are able to call Process32First/Next
	    // Remeber to close it when you don't use it anymore!
	    HANDLE hSnapshot = CreateToolhelp32Snapshot(TH32CS_SNAPPROCESS, NULL);
	    // Check if the snapshot created is valid
	    if (hSnapshot == INVALID_HANDLE_VALUE) return false;
	   
	    // Create the helper struct that will contain all the infos about the current process
	    // while we loop through all the running processes
	    PROCESSENTRY32 ProcEntry;
	    // Remember to set the dwSize member of ProcEntry to sizeof(PROCESSENTRY32)
	    ProcEntry.dwSize = sizeof(PROCESSENTRY32);
	   
	    // Call Process32First
	    if (Process32First(hSnapshot, &ProcEntry))
	    {
	        // Notice that you have to enable Multi-Byte character set in order
	        // to avoid converting everything.
	        // strcmp is not the only way to compare 2 strings ofc, work with your imagination
	        if (!strcmp(ProcEntry.szExeFile, strProcessName.c_str()))
	        {
	            // If we are here it means that the process has been found, we can
	            // open an handle to it and return it
	            // But first of all we have to close the snapshot handle!
	            CloseHandle(hSnapshot);
	            // Open an handle and set the m_hProcess member using OpenProcess
	            // (Notice the usage of PROCESS_ALL_ACCESS flag in order to grant read/write privileges)
	            m_hProcess = OpenProcess(PROCESS_ALL_ACCESS, FALSE, ProcEntry.th32ProcessID);
	            // Store the process id into m_dwProcessId
	            m_dwProcessId = ProcEntry.th32ProcessID);
	            // Return true meaning success
	            return true;
	        }
	    }
	    else
	    {
	        // If the Process32First call failed, it means that there is no
	        // process running in the first place, we can return directly.
	        CloseHandle(hSnapshot);
	        return false;
	    }
	   
	    // If we are here it means that the Process32First call returned TRUE, but the first process
	    // wasn't the process that we were searching for. Now we can loop through the processes
	    // using Process32Next
            while (Process32Next(hSnapshot, &ProcEntry))
            {
	        // We do the same check we did for Process32First
	        if (!strcmp(ProcEntry.szExeFile, strProcessName.c_str()))
	        {
	            // If we are here it means that the process has been found, we can
	            // open an handle to it and set the m_hProcess member using OpenProcess
	            // (Notice the usage of PROCESS_ALL_ACCESS flag in order to grant read/write privileges)
	            m_hProcess = OpenProcess(PROCESS_ALL_ACCESS, FALSE, ProcEntry.th32ProcessID);
	            // Store the process id into m_dwProcessId
	            m_dwProcessId = ProcEntry.th32ProcessID);
	            // Return true meaning success
	            return true;
	        }
	    }
	    // Continue loop while the Process32Next call returns TRUE meaning that there are still processes to check
	   
	    // If we are here it means that the process has not been found or that there are no processes to scan for anymore.
	    // We can close the snapshot handle and return false.
	    CloseHandle(hSnapshot);
	    return false;
	}
[/CODE]
````cpp
// Attach to a process based on strProcessName
// Returns true on success, false on failure
bool Attach(const std::string& strProcessName)
{
    // First of all we create a snapshot handle specific for processes
    //  (notice the usage of TH32CS_SNAPPROCESS) so we are able to call Process32First/Next
    // Remeber to close it when you don't use it anymore!
    HANDLE hSnapshot = CreateToolhelp32Snapshot(TH32CS_SNAPPROCESS, NULL);
     // Check if the snapshot created is valid
    if (hSnapshot == INVALID_HANDLE_VALUE) return false;
   
    // Create the helper struct that will contain all the infos about the current process
    //  while we loop through all the running processes
    PROCESSENTRY32 ProcEntry;
     // Remember to set the dwSize member of ProcEntry to sizeof(PROCESSENTRY32)
    ProcEntry.dwSize = sizeof(PROCESSENTRY32);
   
    // Call Process32First
    if (Process32First(hSnapshot, &ProcEntry))
    {
        // Notice that you have to enable Multi-Byte character set in order
        //  to avoid converting everything.
        // strcmp is not the only way to compare 2 strings ofc, work with your imagination
        if (!strcmp(ProcEntry.szExeFile, strProcessName.c_str()))
        {
            // If we are here it means that the process has been found, we can
            //  open an handle to it and return it but first of all we have to
            //   close the snapshot handle!
            CloseHandle(hSnapshot);
             // Open an handle and set the m_hProcess member using OpenProcess
            //  (Notice the usage of PROCESS_ALL_ACCESS flag in order to grant read/write privileges)
            m_hProcess = OpenProcess(PROCESS_ALL_ACCESS, FALSE, ProcEntry.th32ProcessID);
             // Store the process id into m_dwProcessId
            m_dwProcessId = ProcEntry.th32ProcessID);
             // Return true meaning success
            return true;
        }
    }
    else
    {
        // If the Process32First call failed, it means that there is no
        //  process running in the first place, we can return directly.
        CloseHandle(hSnapshot);
         return false;
    }
   
    // If we are here it means that the Process32First call returned TRUE, but the first process
    //  wasn't the process that we were searching for. Now we can loop through the processes
    //   using Process32Next
    while (Process32Next(hSnapshot, &ProcEntry))
    {
        // We do the same check we did for Process32First
        if (!strcmp(ProcEntry.szExeFile, strProcessName.c_str()))
        {
            // If we are here it means that the process has been found, we can
            //  open an handle to it and set the m_hProcess member using OpenProcess
            //   (Notice the usage of PROCESS_ALL_ACCESS flag in order to grant read/write privileges)
            m_hProcess = OpenProcess(PROCESS_ALL_ACCESS, FALSE, ProcEntry.th32ProcessID);
             // Store the process id into m_dwProcessId
            m_dwProcessId = ProcEntry.th32ProcessID);
             // Return true meaning success
            return true;
        }
    }
    // Continue loop while the Process32Next call returns TRUE meaning that
    //  there are still processes to check
   
    // If we are here it means that the process has not been found or that
    //   there are no processes to scan for anymore.
    // We can close the snapshot handle and return false.
    CloseHandle(hSnapshot);
     return false;
}
````
 Since I'm using C++ and WinAPI, I'm using the exact same algorithm showed on the previous sections with some little modifies to the return values and comments.
The same thing can be done with the function to grab a new module from the process:
 [CODE]
````cpp
// Grabs a module and adds it to m_Modules if found based on strModuleName
	// Returns true on success, false on failure
	bool GrabModule(const std::string& strModuleName)
	{
	    // First of all we create a snapshot handle specific for modules
	    // (notice the usage of TH32CS_SNAPMODULE) so we are able to call Module32First/Next
	    // Remeber to close it when you don't use it anymore!
	    HANDLE hSnapshot = CreateToolhelp32Snapshot(TH32CS_SNAPMODULE, m_dwProcessId);
	    // Check if the snapshot created is valid
	    if (hSnapshot == INVALID_HANDLE_VALUE) return false;
	   
	    // Create the helper struct that will contain all the infos about the current module
	    // while we loop through all the loaded modules
	    MODULEENTRY32 ModEntry;
	    // Remember to set the dwSize member of ModEntry to sizeof(MODULEENTRY32)
	    ModEntry.dwSize = sizeof(MODULEENTRY32);
	   
	    // Call Module32First
	    if (Module32First(hSnapshot, &ModEntry))
	    {
	        // Notice that you have to enable Multi-Byte character set in order
	        // to avoid converting everything.
	        // strcmp is not the only way to compare 2 strings ofc, work with your imagination
	        if (!strcmp(ModEntry.szModule, strModuleName.c_str()))
	        {
	            // If we are here it means that the module has been found, we can add the module to the vector
	            // But first of all we have to close the snapshot handle!
	            CloseHandle(hSnapshot);
	            // Add ModEntry to the m_Modules vector
	            m_Modules.push_back(ModEntry); // You can add a check here to see if the module is already there ;)
	            // Return true meaning success
	            return true;
	        }
	    }
	    else
	    {
	        // If the Process32First call failed, it means that there is no
	        // process running in the first place, we can return directly.
	        CloseHandle(hSnapshot);
	        return false;
	    }
	   
	    // If we are here it means that the Module32First call returned TRUE, but the first module
	    // wasn't the module that we were searching for. Now we can loop through the modules
	    // using Module32Next
            while (Module32Next(hSnapshot, &ModEntry))
	    {
	        // We do the same check we did for Module32First
	        if (!strcmp(ModEntry.szModule, strModuleName.c_str()))
	        {
	            // If we are here it means that the module has been found, we can add the module to the vector
	            // But first of all we have to close the snapshot handle!
	            CloseHandle(hSnapshot);
	            // Add ModEntry to the m_Modules vector
	            m_Modules.push_back(ModEntry); // You can add a check here to see if the module is already there ;)
	            // Return true meaning success
	            return true;
	        }
	    }
	    // Continue loop while the Module32Next call returns TRUE meaning that there are still modules to check
	   
	    // If we are here it means that the module has not been found or that there are no modules to scan for anymore.
	    // We can close the snapshot handle and return false.
	    CloseHandle(hSnapshot);
	    return false;
	}
[/CODE]
// Returns true on success, false on failure
bool GrabModule(const std::string& strModuleName)
{
    // First of all we create a snapshot handle specific for modules
    //  (notice the usage of TH32CS_SNAPMODULE) so we are able to call Module32First/Next
    // Remeber to close it when you don't use it anymore!
    HANDLE hSnapshot = CreateToolhelp32Snapshot(TH32CS_SNAPMODULE, m_dwProcessId);
     // Check if the snapshot created is valid
    if (hSnapshot == INVALID_HANDLE_VALUE) return false;
   
    // Create the helper struct that will contain all the infos about the current module
    //  while we loop through all the loaded modules
    MODULEENTRY32 ModEntry;
     // Remember to set the dwSize member of ModEntry to sizeof(MODULEENTRY32)
    ModEntry.dwSize = sizeof(MODULEENTRY32);
   
    // Call Module32First
    if (Module32First(hSnapshot, &ModEntry))
    {
        // Notice that you have to enable Multi-Byte character set in order
        //  to avoid converting everything.
        // strcmp is not the only way to compare 2 strings ofc, work with your imagination
        if (!strcmp(ModEntry.szModule, strModuleName.c_str()))
        {
            // If we are here it means that the module has been found, we can add the module
            //  to the vector but first of all we have to close the snapshot handle!
            CloseHandle(hSnapshot);
             // Add ModEntry to the m_Modules vector
            m_Modules.push_back(ModEntry); // You can add a check here to see if the module
            //  is already there ;)
             // Return true meaning success
            return true;
        }
    }
    else
    {
        // If the Process32First call failed, it means that there is no
        //  process running in the first place, we can return directly.
        CloseHandle(hSnapshot);
         return false;
    }
   
    // If we are here it means that the Module32First call returned TRUE, but the first module
    //  wasn't the module that we were searching for. Now we can loop through the modules
    //   using Module32Next
    while (Module32Next(hSnapshot, &ModEntry))
    {
        // We do the same check we did for Module32First
        if (!strcmp(ModEntry.szModule, strModuleName.c_str()))
        {
            // If we are here it means that the module has been found, we can add the module
            //  to the vector but first of all we have to close the snapshot handle!
            CloseHandle(hSnapshot);
             // Add ModEntry to the m_Modules vector
            m_Modules.push_back(ModEntry); // You can add a check here to see if the module
            //  is already there ;)
             // Return true meaning success
            return true;
        }
    }
    // Continue loop while the Module32Next call returns TRUE meaning that
    //  there are still modules to check
   
    // If we are here it means that the module has not been found or that there are
    //  no modules to scan for anymore.
    // We can close the snapshot handle and return false.
    CloseHandle(hSnapshot);
     return false;
}
````
 As you can see it's the exact same algorithm with some little modifications! Again, this isn't the only way to do this, depending on what you are using.
 Now that we've got the core functions that will perform the algorithms we need, we can build our constructor which will initialize the class. As always everything is pretty straight forward and commented.
 [CODE]
        // Default constructor: won't attach to any process
	CMemoryManager()
	{
		// Init members
		m_hProcess = INVALID_HANDLE_VALUE;
		m_dwProcessId = 0;
		// Just for safety, I clear out the modules vector
		m_Modules.clear();
	}
	// This constructor will attach to a specific process (default CS:GO)
	CMemoryManager(const std::string& strProcessName = "csgo.exe")
	{
		// Init members
		m_hProcess = INVALID_HANDLE_VALUE;
		m_dwProcessId = 0;
		// Just for safety, I clear out the modules vector
		m_Modules.clear();
		// Attach and throw if the function failed so we can manage the fail
		if (!Attach(strProcessName))
			throw;
	}
[/CODE]
````cpp
// Default constructor: won't attach to any process
CMemoryManager()
{
    // Init members
    m_hProcess = INVALID_HANDLE_VALUE;
    m_dwProcessId = 0;
     // Just for safety, I clear out the modules vector
    m_Modules.clear();
}
 // This constructor will attach to a specific process (default CS:GO)
CMemoryManager(const std::string& strProcessName = "csgo.exe")
{
    // Init members
    m_hProcess = INVALID_HANDLE_VALUE;
    m_dwProcessId = 0;
     // Just for safety, I clear out the modules vector
    m_Modules.clear();
     // Attach and throw if the function failed so we can manage the fail
    if (!Attach(strProcessName))
        throw;
}
````
 Now we can start writing our RPM/WPM wrappers, I'll stay simple for now but you can get further by adding things like reading a fixed size of memory, reading an array and returning a pointer to it, and so on... just use your imagination! :)
 [CODE]
````cpp
// RPM/WPM wrappers
	
	// Read a value from memory and put it in Value
	// Returns true on success, false on failure
	template <class T>
	inline bool Read(DWORD dwAddress, T& Value)
	{
		return ReadProcessMemory(m_hProcess, reinterpret_cast<LPVOID>(dwAddress), Value, sizeof(T), NULL) == TRUE;
	}
	// Write a Value in memory
	// Returns true on success, false on failure
	template <class T>
	inline bool Write(DWORD dwAddress, const T& Value)
	{
		return WriteProcessMemory(m_hProcess, reinterpret_cast<LPVOID>(dwAddress), Value, sizeof(T), NULL) == TRUE;
	}
[/CODE]
// Read a value from memory and put it in Value
// Returns true on success, false on failure
template <class T>
inline bool Read(DWORD dwAddress, T& Value)
{
    return ReadProcessMemory(m_hProcess, reinterpret_cast<LPVOID>(dwAddress), Value, sizeof(T), NULL) == TRUE;
}
 // Write a Value in memory
// Returns true on success, false on failure
template <class T>
inline bool Write(DWORD dwAddress, const T& Value)
{
    return WriteProcessMemory(m_hProcess, reinterpret_cast<LPVOID>(dwAddress), Value, sizeof(T), NULL) == TRUE;
}
````
 Nothing really special here, as you can see these are just functions that wraps RPM and WPM using templates.
Finally, we can put some getters to conclude the class.
 [CODE]
````cpp
// Getters
HANDLE GetHandle() { return m_hProcess; }
DWORD GetProcId() { return m_dwProcessId; }
std::vector<MODULEENTRY32> GetModules() { return m_Modules; }
[/CODE]
````
 Do I really need comments here?
Remember to implement this class (if using C++) following the classic .h/.cpp separation convention.
 Reference links for this section:
[URL="http://pastebin.com/cfF01nEZ"]Commented MMC on pastebin[/URL]
 [SIZE="5"][FONT="Franklin Gothic Medium"][B]Chapter 3[/B][/FONT][/SIZE]
[SIZE="4"][FONT="Franklin Gothic Medium"][B]Offsets[/B][/FONT][/SIZE]
[Commented MMC on pastebin](http://pastebin.com/cfF01nEZ)
 ## [Chapter 3](#chapter-3)
### Offsets
 One of the most important topics to know while learning about memory hacking is the purpose of an offset. In these chapters, I'll try to explain what an offset is and how to use them to access our values in memory. I'll then move into explaining netvars and then I'll talk about how to grab offsets and netvars dynamically.
But first, what is an offset?
 An offset is a value that describes how many bytes we should move to reach a certain area of memory. Refer to this basic image to understand the concept:
 [IMG]http://i.imgur.com/8ZeSlWE.png[/IMG]
![Offsets](http://i.imgur.com/8ZeSlWE.png "Offsets")
 As you can see, we've got a base address located at 0x0000, a local player's pointer located at 0x004C and the local player's health which is located at 0x007E. Our objective is to read out the health value of the local player.
 @@ -434,13 +505,12 @@ Now, to reach the local player's pointer we need to move 0x004C away from the ba
So, for example, specifically for CS:GO, the current offset for the local player is 0xA323E4, while the module base of client.dll will be dynamic, so we can't give a certain value for it (that's why we use that algorithm showed on previous sections).
By doing RPM(base address + 0xA323E4) we get the local player. 0xA323E4 is an offset, it tells us how many bytes we must move if we want to reach something in memory. Other examples of offsets are entity list (0x4A4FCA4), force jump (0x4EE5114) and many others.
 [B]Be careful![/B] The current offsets are static values which means that if there is a little change to the code the addresses set will modify, modifying the values of the offsets. On each update, the offsets will be most likely outdated. You have to re-grab them using an offset dumper, or just implement pattern scanning (we'll cover that later on).
**Be careful!** The current offsets are static values which means that if there is a little change to the code the addresses set will modify, modifying the values of the offsets. On each update, the offsets will be most likely outdated. You have to re-grab them using an offset dumper, or just implement pattern scanning (we'll cover that later on).
 Is m_iHealth (0xFC) an offset? Kinda yes, because we use it like the normal offsets, but it's more specifically a netvar. We'll cover them, also.
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Using our class and the offsets to make our first bhop[/B][/I][/FONT][/SIZE]
[I]
(NOTE: This section is going to get really practical, with a lot of commented pieces of C++ source code. But no problems, it's optional! You can skip this if you really want it <3)[/I]
#### [Using our class and the offsets to make our first bhop](#using-our-class-and-the-offsets-to-make-our-first-bhop)
_(NOTE: This section is going to get really practical, with a lot of commented pieces of C++ source code. But no problems, it's optional! You can skip this if you really want it :heart:)_
 Well, after a little bit of summer VACation, I'm back on track writing this piece of ""guide"" (?). We are back again with another practical lesson, which will involve commented sauce which you can test and try on your own (no anti-pasta included, just read that comments ok? :( ).
 @@ -451,197 +521,246 @@ Before going practical, we need to fully understand what we want to achieve and
So, how shall we proceed to make a program that does the "heavy lifting" of bhopping for us, allowing to gain speed easily without practicing like a nerd?
You may think, at a first glance: "What if I just make a program that spams the space key while you are pressing it". I'd say that you can make a macro for that without making a whole software, but in the end of the day this method is quite shit and not precise, you won't gain any velocity in most of the cases, especially in server running at 128 ticks.
 Thinking logical, what is the most difficult part of bhopping? Timing the jumping. [I]When we are on ground, we have to jump immediately to gain velocity.[/I]. See this sentence, we can translate this logic into actual C++ source code. All we need to know is exactly when we are on ground. How can we do this? Simple: we'll use a special bitflag (stored in CS:GO memory) that holds all kinds of player states: on ground, crouching, zooming, etc. We need to check for ground, so yeah, quite straight-forward. We can start writing sauce!
Thinking logical, what is the most difficult part of bhopping? Timing the jumping. _When we are on ground, we have to jump immediately to gain velocity.[/I]. See this sentence, we can translate this logic into actual C++ source code. All we need to know is exactly when we are on ground. How can we do this? Simple: we'll use a special bitflag (stored in CS:GO memory) that holds all kinds of player states: on ground, crouching, zooming, etc. We need to check for ground, so yeah, quite straight-forward. We can start writing sauce!
 [CODE]
// First of all, include your Memory Management Class. I won't include anything else other than basic C++ i/o because MMC header already includes WinAPI
````cpp
// First of all, include your Memory Management Class. I won't include anything
//  else other than basic C++ i/o because MMC header already includes WinAPI
#include "MemoryManager.h"
#include <iostream> // For STL i/o
#include <ctime> // For std::chrono
#include <thread> // For std::this_thread
#include <iostream>  // For STL i/o
#include <ctime>     // For std::chrono
#include <thread>    // For std::this_thread
 int main()
{
    // Main entry point of the program
    return 0;
}
[/CODE]
````
 Depending on your implementation of MMC, the approach will be different. In this example, I'll use the MMC written on the previous section of the guide.
 [CODE]
````cpp
try {
    CMemoryManager* MemoryManager = new CMemoryManager("csgo.exe");
} catch (...) {
    // Process not found or invalid snap handle, manage the failure safely
    std::cout << "CS:GO not found!" << std::endl;
    std::this_thread::sleep_for(std::chrono::milliseconds(1500)); // Sleep for 1500 secs so the user can see the error
    return 0; // Quit the program
     // Sleep for 1500 secs so the user can see the error
    std::this_thread::sleep_for(std::chrono::milliseconds(1500));
     // Quit the program
    return 0;
}
[/CODE]
````
 Now we have got our MemoryManager instance ready to go. We will operate on client.dll only since all the offsets we need are there.
 [CODE]
````cpp
if (!MemoryManager->GrabModule("client.dll"))
{
    // Client module not found, manage the failure
    std::cout << "Client module not found!" << std::endl;
    std::this_thread::sleep_for(std::chrono::milliseconds(1500)); // Sleep for 1500 secs so the user can see the error
    return 0; // Quit the program
     // Sleep for 1500 secs so the user can see the error
    std::this_thread::sleep_for(std::chrono::milliseconds(1500));
     // Quit the program
    return 0;
}
[/CODE]
````
 Now, following my implementation, we've added client.dll module infos to the m_Modules private member of the MMC. We need the client base address to grab the local player, I'll do smth like this
 [CODE]
DWORD dwClientBase = 0; // This will hold the client base address
for (auto m : MemoryManager->GetModules()) // Loop through the modules grabbed
````cpp
// This will hold the client base address
DWORD dwClientBase = 0;
 // Loop through the modules grabbed
for (auto m : MemoryManager->GetModules())
{
    if (!strcmp(m.szModule, "client.dll"))
    {
        dwClientBase = reinterpret_cast<DWORD>(m.modBaseAddr);
        break;
    }
}
[/CODE]
````
 Even if we've got only one module so far, this implementation will allow us to work with many modules in an easy way. Sorry for the mixture of C++11 practices like enhanced for and reinterpret_cast and C stuff like strcmp and DWORD but yeah this is just demonstrative (worst excuse ever lol)
 Well, now we've got our client base address. Cool, huh? Using the MMC and the local player offset (grabbed from the so-loved [URL="http://www.unknowncheats.me/forum/counterstrike-global-offensive/103220-global-offensive-structs-offsets-277.html"]offsets thread[/URL]), we are able to retrieve our local player for our needs.
Well, now we've got our client base address. Cool, huh? Using the MMC and the local player offset (grabbed from the so-loved [offsets thread](http://www.unknowncheats.me/forum/counterstrike-global-offensive/103220-global-offensive-structs-offsets-277.html)
), we are able to retrieve our local player for our needs.
 ````cpp
// This will hold our local player base address
DWORD dwLocalPlayer = 0;
 [CODE]
DWORD dwLocalPlayer = 0; // This will hold our local player base address
MemoryManager->Read<DWORD>(dwClientBase + 0x00A3A43C, dwLocalPlayer); // Dereference the pointer to the local player from process memory and grab the base address value
[/CODE]
// Dereference the pointer to the local player from process memory and grab the base address value
MemoryManager->Read<DWORD>(dwClientBase + 0x00A3A43C, dwLocalPlayer);
````
 Now, how we can check if the local player is on ground or not? Each entity has got a member called m_fFlags, which is a bitfield located at base + 0x100 (256). We can operate on this member quite easily using our bitfield knownledge (because you've got bitfield knownledge, right?) We can compare stuff using the & operator (bitwise and), and other cool stuff. Read more about bitfields/masks see [URL="http://www.learncpp.com/cpp-tutorial/3-8a-bit-flags-and-bit-masks/"]here[/URL].
Now, how we can check if the local player is on ground or not? Each entity has got a member called m_fFlags, which is a bitfield located at base + 0x100 (256). We can operate on this member quite easily using our bitfield knownledge (because you've got bitfield knownledge, right?) We can compare stuff using the & operator (bitwise and), and other cool stuff. Read more about bitfields/masks see [here](http://www.learncpp.com/cpp-tutorial/3-8a-bit-flags-and-bit-masks/)
.
 From the SDK, we know that the flag value to check if on ground is [I](1<<0)[/I] ([URL="https://github.com/ValveSoftware/source-sdk-2013/blob/master/mp/src/public/const.h#L110"]FL_ONGROUND[/URL]) so we can stick on it.
From the SDK, we know that the flag value to check if on ground is _(1<<0)_ ([FL_ONGROUND](https://github.com/ValveSoftware/source-sdk-2013/blob/master/mp/src/public/const.h#L110)
) so we can stick on it.
 [CODE]
````cpp
// We'll put everything into a while(true) loop later on
// Read m_fFlags out of memory
BYTE fFlags = 0; // This will hold the bitfield
 // This will hold the bitfield
BYTE fFlags = 0;
 MemoryManager->Read<BYTE>(dwLocalPlayer + 0x100, fFlags);
 // Continue only if the user is holding space
if (GetAsyncKeyState(VK_SPACE) & 0x8000)
{
    if (fFlags & (1<<0)) // Check for FL_ONGROUND
    // Check for FL_ONGROUND
    if (fFlags & (1<<0)) 
    {
        // Continue...
    }
}
[/CODE]
````
 Now we can choose 2 ways. One way will involve using a WPM call to force a jump directly from memory, the other way will involve using the WinAPI to simulate a mouse scroll, but the user will have to bind +jump to mouse scroll in game, so yeah not completely portable. In this example I'll just stick to memory writing, because paranoias in these cases is reall (really) useless (CS:GO will just pretend you are not there).
 So, there is an offset that will work perfectly: m_dwForceJump. Basically, based on the value that m_dwForceJump have got, the game will either jump, not jump, or jump for one tick. This is just what we need! We write 4 to it to reset jump, 5 to jump, 6 to jump for one tick. In order to reduce WPM/RPM calls to minimal, writing 6 will be as perfect as writing 5 then 4 after a small sleep.
 [CODE]
MemoryManager->Write(dwClientBase + 0x02E97EC4, 6); // Will force jump for 1 tick only
[/CODE]
````cpp
// Will force jump for 1 tick only
MemoryManager->Write(dwClientBase + 0x02E97EC4, 6);
````
 With this method we can achieve near to perfect hops with the minimal effort.
The final code snippet will look something along the lines of this (remember that you'll have to adapt the source based on your MMC implementation!):
 [CODE]
// First of all, include your Memory Management Class. I won't include anything else other than basic C++ i/o because MMC header already includes WinAPI
````cpp
// First of all, include your Memory Management Class. I won't include
//  anything else other than basic C++ i/o because MMC header already includes WinAPI
#include "MemoryManager.h"
#include <iostream> // For STL i/o
#include <ctime> // For std::chrono
#include <thread> // For std::this_thread
#include <iostream>   // For STL i/o
#include <ctime>      // For std::chrono
#include <thread>     // For std::this_thread
 int main()
{
    // Main entry point of the program
	
	try {
		CMemoryManager* MemoryManager = new CMemoryManager("csgo.exe");
	} catch (...) {
		// Process not found or invalid snap handle, manage the failure safely
		std::cout << "CS:GO not found!" << std::endl;
		std::this_thread::sleep_for(std::chrono::milliseconds(1500)); // Sleep for 1500 secs so the user can see the error
		return 0; // Quit the program
	}
	
	if (!MemoryManager->GrabModule("client.dll"))
	{
		// Client module not found, manage the failure
		std::cout << "Client module not found!" << std::endl;
		std::this_thread::sleep_for(std::chrono::milliseconds(1500)); // Sleep for 1500 secs so the user can see the error
		return 0; // Quit the program
	}
	
	DWORD dwClientBase = 0; // This will hold the client base address
	for (auto m : MemoryManager->GetModules()) // Loop through the modules grabbed
	{
		if (!strcmp(m.szModule, "client.dll"))
		{
			dwClientBase = reinterpret_cast<DWORD>(m.modBaseAddr);
			break;
		}
	}
	// TODO:: Add check to see if we didn't find a valid client base ;)
	
	while (true)
	{
		DWORD dwLocalPlayer = 0; // This will hold our local player base address
		MemoryManager->Read<DWORD>(dwClientBase + 0x00A3A43C, dwLocalPlayer); // Dereference the pointer to the local player from process memory and grab the base address value
		
		// TODO:: Add checks to control RPM/WPM failures!
		
		// We'll put everything into a while(true) loop later on
		// Read m_fFlags out of memory
		BYTE fFlags = 0; // This will hold the bitfield
		MemoryManager->Read<BYTE>(dwLocalPlayer + 0x100, fFlags);
 		// Continue only if the user is holding space
		if (GetAsyncKeyState(VK_SPACE) & 0x8000)
		{
			if (fFlags & (1<<0)) // Check for FL_ONGROUND
			{
				MemoryManager->Write(dwClientBase + 0x02E97EC4, 6); // Will force jump for 1 tick only
			}
		}
		
		// Sleep 10 ms to save CPU
		std::this_thread::sleep_for(std::chrono::milliseconds(10));
	}
	
    
    try {
        CMemoryManager* MemoryManager = new CMemoryManager("csgo.exe");
    } catch (...) {
        // Process not found or invalid snap handle, manage the failure safely
         std::cout << "CS:GO not found!" << std::endl;
         // Sleep for 1500 secs so the user can see the error
        std::this_thread::sleep_for(std::chrono::milliseconds(1500));
         // Quit the program
        return 0;
    }
    
    if (!MemoryManager->GrabModule("client.dll"))
    {
        // Client module not found, manage the failure
         std::cout << "Client module not found!" << std::endl;
         // Sleep for 1500 secs so the user can see the error
        std::this_thread::sleep_for(std::chrono::milliseconds(1500));
         // Quit the program
        return 0;
    }
    
    // This will hold the client base address
    DWORD dwClientBase = 0;
     // Loop through the modules grabbed
    for (auto m : MemoryManager->GetModules())
    {
        if (!strcmp(m.szModule, "client.dll"))
        {
            dwClientBase = reinterpret_cast<DWORD>(m.modBaseAddr);
            break;
        }
    }
     // TODO:: Add check to see if we didn't find a valid client base ;)
    
    while (true)
    {
        // This will hold our local player base address
        DWORD dwLocalPlayer = 0;
         // Dereference the pointer to the local player from process memory
        //  and grab the base address value
        MemoryManager->Read<DWORD>(dwClientBase + 0x00A3A43C, dwLocalPlayer);
        
        // TODO:: Add checks to control RPM/WPM failures!
        
        // We'll put everything into a while(true) loop later on
        // Read m_fFlags out of memory
         // This will hold the bitfield
        BYTE fFlags = 0;
         MemoryManager->Read<BYTE>(dwLocalPlayer + 0x100, fFlags);
         // Continue only if the user is holding space
        if (GetAsyncKeyState(VK_SPACE) & 0x8000)
        {
            // Check for FL_ONGROUND
            if (fFlags & (1<<0))
            {
                // Will force jump for 1 tick only
                MemoryManager->Write(dwClientBase + 0x02E97EC4, 6);
            }
        }
        
        // Sleep 10 ms to save CPU
        std::this_thread::sleep_for(std::chrono::milliseconds(10));
    }
    
    return 0;
}
[/CODE]
````
 I've added comments with TODO in sauce that will serve as a little "homework" to you to improve this snippet.
The other homework you have is to make it so it doesn't jump while the chat is open. There are many ways to achieve this, just choose one. Search around and you'll always find what you need ;) (in most cases).
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Netvars[/B][/I][/FONT][/SIZE]
#### [Netvars](#netvars)
 Before jumping into pattern scanning, I'd like to talk about netvars. A [B]Net[/B]worked [B]Var[/B]iable (aka a netvar) is, as the name may suggest, a variable which is networked. A first example of a netvar would be m_iHealth (0xFC) or m_iTeamNum (0xF0) which are variables that ofc need to be networked in order to make the whole multiplayer thing to work you know. 
Before jumping into pattern scanning, I'd like to talk about netvars. A **Net**worked **Var**iable (aka a netvar) is, as the name may suggest, a variable which is networked. A first example of a netvar would be m_iHealth (0xFC) or m_iTeamNum (0xF0) which are variables that ofc need to be networked in order to make the whole multiplayer thing to work you know. 
 These special variables are used exactly like any other offset: for example, m_iHealth is a member of DT_BasePlayer (DT stands for [B]D[/B]ata [B]T[/B]able, notice the m_i hungarian notation prefix which Valve uses a lot). There are many data tables like DT_CSPlayer, DT_BaseViewModel, etc...
These special variables are used exactly like any other offset: for example, m_iHealth is a member of DT_BasePlayer (DT stands for **D**ata **T**able, notice the m_i hungarian notation prefix which Valve uses a lot). There are many data tables like DT_CSPlayer, DT_BaseViewModel, etc...
 So, let's say we want to grab the amount of matchmaking wins of a certain player on the server. The first thing that would come in our mind if we don't know anything would be "There must be a netvar that holds this value!" and that's true, it's called m_iCompetitiveWins, it's an integer value as the convention suggests and yes it's exactly what we want. You try to do smth like RPM(entity base address + m_iCompetitiveWins offset) BUT the result is really fucked up and not exactly what we want. That's because you didn't notice that m_iCompetitiveWins isn't a member of DT_CSPlayer or BasePlayer! Hence why we can't read it as we do with other netvars which are members of that data table. Rewatch the netvar dump carefully and you'll notice that m_iCompetitiveWins is a member of DT_CSPlayerResource! So we need to read it differently from what we usually do. So since it's CSPlayerResource it will hold 64 values for each client connected to server, meaning that we need the entity index of the player we want to read the wins from. We'll do smth like RPM(player resource base + m_iCompetitiveWins + i * sizeof(int)) where i is the index of our entity, and since each member of the array is an integer, we do i * sizeof(int) (we could just do i * 4 but ayyyy).
 Basically, if we want to grab something from a certain player or the local player itself, remember that there will most likely always be a netvar that holds the value we are looking for. Really, there are a shitton of netvars so just take the right time to search through the dump and you'll find what you want in most cases. See how a really basic netvar dump can be really really useful? In the next section we'll cover pattern scanning, then we will cover how these dumps are made, involving recursion... will be really cool stuff indeed! :D
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Getting offsets dynamically: Pattern Scanning[/B][/I][/FONT][/SIZE]
#### [Getting offsets dynamically: Pattern Scanning](#getting-offsets-dynamically-pattern-scanning)
 Started from the bottom now we are here: we are going to talk about pattern scanning. This is an important step to take if you want to take your externals to the next levels, simply because [B]the only purpose of pattern scanning is to completely eliminate the hassle of updating offsets on each update on the game.[/B]
Started from the bottom now we are here: we are going to talk about pattern scanning. This is an important step to take if you want to take your externals to the next levels, simply because **the only purpose of pattern scanning is to completely eliminate the hassle of updating offsets on each update on the game.**
For example: the offsets I've used previously in the example codenz some weeks ago are already outdated now, because of CS:GO updates. In order to make your external more consistent and reduce the work you have to put on it to mantain it, you can implement the infamous pattern scanning.
 Still this guide is aimed to completely noobish ppl I don't really want to get any kind of deeper in pattern scanning ([URL="http://www.unknowncheats.me/forum/programming-for-beginners/171994-understanding-pattern-scanning-concept.html"]like WasserEsser did in his awesome guide, which I recommend reading after you grasp the concept[/URL]). I just want you to understand how it works and how to implement it in your fantastic ez external cheaterino.
Still this guide is aimed to completely noobish ppl I don't really want to get any kind of deeper in pattern scanning ([like WasserEsser did in his awesome guide](http://www.unknowncheats.me/forum/programming-for-beginners/171994-understanding-pattern-scanning-concept.html), which I recommend reading after you grasp the concept
). I just want you to understand how it works and how to implement it in your fantastic ez external cheaterino.
 So, the concept behind pattern scanning (basically speaking) is to "build the offset" we are going to use later on in the cheat code. Each CS:GO module (like client.dll or engine.dll) is composed of bytes (raw bytes) which can be seen when reversing a module in OllyDbg or any other reversing tool. The offset we need is of course lying through these bytes, because the game itself uses offsets internally to access certain areas of memory (like we do with our externals!). We just have to grab it without forcing it, but how? The answer is quite simple: we use the sorrounding bytes of the offsets. See this image taken from WasserEsser guide:
 [IMG]http://i.imgur.com/HDlH0AK.png[/IMG]
![Offsets](http://i.imgur.com/HDlH0AK.png "Offsets")
 FC 00 00 00 is m_iHealth (stored in little endian system), a common netvar we know to grab the health of an entity. In the image, the sorrounding bytes of the offset are highlighted in gray (so you can see them). These bytes are going to compose our pattern. Using OllyDbg specifically, we can simply use the SigMaker plugin, or if you are really brave you can make the sig on your own just by looking at the bytes (SigMaker just simplifies the process).
 In this specific case, the signature is "\x75\x09\x83\xB9[B]\xFC\x00\x00\x00\x00\[/B]x7F\x2D". We see that the current offset is lying in the pattern, and we don't want it to be there so we nullify it (by just modifying the xFC to x00 in this specific case). Now, we have got the pattern we need. The mask is just derived from the pattern: it's a string describing which byte is known and which byte isn't known. In this case:
In this specific case, the signature is `\x75\x09\x83\xB9**\xFC\x00\x00\x00\x00\**x7F\x2D`. We see that the current offset is lying in the pattern, and we don't want it to be there so we nullify it (by just modifying the xFC to x00 in this specific case). Now, we have got the pattern we need. The mask is just derived from the pattern: it's a string describing which byte is known and which byte isn't known. In this case:
 ````cpp
x75\ -> x
x09\ -> x
x83\ -> x
@@ -653,29 +772,31 @@ x00\ -> ?
x00\ -> ?
x7F\ -> x
x2D\ -> x
````
 So the final mask is "xxxx?????xx". Simple, huh? With the pattern and the mask in our hands, we can proceed to make our pattern scanning implementantion in C++ code.
To understand how the algorithm is going to work, just look at this picture:
 [IMG]http://i.imgur.com/OWAG2k2.png[/IMG]
![Offsets](http://i.imgur.com/OWAG2k2.png "Offsets")
 This horrific thing made on paint in 2 mins represents how the pattern scanning is going to work with module bytes. Basically, in the image we have got 4 possible places to place our pattern. We loop through all of the possible places until we find the only one that fits our pattern (the third one obviously). Now, you may ask "What if I encounter a fitting place but it's not where my offset is lying?". That can happen (but it's really not that likely...) and that's what we want to make patterns as unique as possible. Also, we don't want them to be too long or too short, because a too long pattern will get outdated in less time than a good sized pattern. In the end, it's way better than hardcoding offsets.
That's also how the offsets dumper we commonly use to grab offsets work, each one with a different kind of implementation. Just like with MMC (Memory Management Class, remember?), the code style possibilities are really wide, so my commented implementation will be just a small example to let you understand, nothing more.
 In order to do pattern scanning, I commonly use a class...
[CODE]
 ````cpp
// This is the skeleton of the class
class CScanner
{
protected:
	HANDLE m_hProcess; 						// A valid handle (to CS:GO ofc)
	DWORD 	m_dwModuleBase; 				// Base of the module we want to scan
	DWORD 	m_dwModuleSize;				// Size of the module we want to scan
	std::unique_ptr<BYTE[]> m_pModuleBytes;	// Bytes of the module
    HANDLE m_hProcess;                         // A valid handle (to CS:GO ofc)
    DWORD     m_dwModuleBase;                  // Base of the module we want to scan
    DWORD     m_dwModuleSize;                  // Size of the module we want to scan
    std::unique_ptr<BYTE[]> m_pModuleBytes;    // Bytes of the module
public:
	// Here I'm going to define the scanning functions
    // Here I'm going to define the scanning functions
};
[/CODE]
````
 The members of the class are quite obvious and that's all we need. The first step is to dump the module bytes, which means storing the whole module into a byte array. Yeah, that sounds crazy. It is, actually, considering that a module is really really heavy (just log the module size of client.dll or engine.dll). This means that we need to take care of memory leaks because if we leak this huge amount of memory, that's not a good thing. At all. That's why I'm using the STL type std::unique_ptr. It's a C++11 thing that allows me to make a smart pointer, which will delete itself when it gets out of scope (when we delete a class instance, in this case). Kinda handy, huh? It will take care of avoiding memory leaks, hopefully, but you can do whatever you want honestly.
 @@ -684,7 +805,8 @@ Ofc, we must setup a constructor where we pass the handle, the module base addre
 Then, we need a function to dump our module bytes to the huge byte array.
The function will look like this:
[CODE]
 ````cpp
bool CScanner::Dump()
{
    if (m_pModuleBytes != nullptr)
@@ -694,55 +816,60 @@ bool CScanner::Dump()
    }
    else return false;
}
[/CODE]
````
 The function is really simple: if m_pModuleBytes (the byte array containing every single byte in the module) is nullptr (points to nowhere, still not allocated), then we can allocate the memory we need, which is exactly the m_dwModuleSize. So we allocated [I]m_dwModuleSize[/I] bytes in the heap, using the special C++14 function std::make_unique, to setup the unique_ptr. This memory is now "managed": it will be cleaned up upon object destruction.
The function is really simple: if m_pModuleBytes (the byte array containing every single byte in the module) is nullptr (points to nowhere, still not allocated), then we can allocate the memory we need, which is exactly the m_dwModuleSize. So we allocated _m_dwModuleSize_ bytes in the heap, using the special C++14 function std::make_unique, to setup the unique_ptr. This memory is now "managed": it will be cleaned up upon object destruction.
This is basically C++ attempt at garbage collecting.
 Now that we allocated enough memory, we can just fill up this memory with ReadProcessMemory using our handle to CS:GO. We just read the entire module by passing its base address as the starting point, and the size of the module as the size of the reading. Cool, huh? We simply return bool (converted from BOOL through !!) indicating if the RPM call has been successful.
 The other function we need is, ofc, the function to scan memory for a pattern.
There are several algorithms out there in order to do this, and there is even a thread which contains the fastest methods, especially the one from learn_more that nearly everyone uses in their internals.
The thread can be found by clicking here: [URL="https://www.unknowncheats.me/forum/c-and-c/125497-findpattern-benchmark.html"]*CLICK*[/URL]
The thread can be found by clicking here: [*CLICK*](https://www.unknowncheats.me/forum/c-and-c/125497-findpattern-benchmark.html)
 If you are interested, you can glance around in the thread so you can get inspired and write your own or just copy or improve other's methods.
The implementation I'm currently using in my externals is ofc not the best or fastest one, but it works kinda good.
 [CODE]
````cpp
// First of all, I setup a quick lambda function to check against the mask.
// This is the most important function as it makes a really important check.
// You can move it outside the function scope but idk it depends on you.
auto mask_check = [&](int start_offset) -> bool
{
	// Loop through the mask
	for (unsigned int i = 0; i < mask.length(); i++)
	{
		// If the current char in the mask is a '?', just carry on looping
		if (mask[i] == '?') continue;
		// If the current char is a 'x', AND the current byte in the pattern at i is DIFFERENT from the byte
		// located at start_offset + position in the mask (i)
		if (mask[i] == 'x' && pattern[i] != module_bytes[start_offset + i])
			return false; // RETURN FALSE MEANING THAT THE BYTES AND THE PATTERN DO NOT MATCH!
	}
	return true; // If the code reaches here without returning false, the patterns and the bytes DO MATCH.
	// 'i' is the right offset to look for (hopefully)
    // Loop through the mask
    for (unsigned int i = 0; i < mask.length(); i++)
    {
        // If the current char in the mask is a '?', just carry on looping
        if (mask[i] == '?') continue;
         // If the current char is a 'x', AND the current byte in the pattern at i is DIFFERENT from the byte
        //  located at start_offset + position in the mask (i)
        if (mask[i] == 'x' && pattern[i] != module_bytes[start_offset + i])
            return false; // RETURN FALSE MEANING THAT THE BYTES AND THE PATTERN DO NOT MATCH!
    }
     // If the code reaches here without returning false, the patterns and the bytes DO MATCH.
    return true;
     // 'i' is the right offset to look for (hopefully)
};
[/CODE]
````
 Ok. This can be a really though one to understand. Look at it slowly and you will notice that it makes sense. Now we just need to use this function:
 [CODE]
````cpp
DWORD CScanner::Search(std::vector<BYTE> pattern, const std::string& mask)
{
	// lambda definition here!
    // lambda definition here!
 	for (DWORD i = 0; i < m_dwModuleBase + m_dwModuleSize; i++)
	{
		if (mask_check(i))
			return m_dwModuleBase + i;
	}
    for (DWORD i = 0; i < m_dwModuleBase + m_dwModuleSize; i++)
    {
        if (mask_check(i))
            return m_dwModuleBase + i;
    }
}
[/CODE]
````
 The Search function will just use mask_check while looping through the whole module bytes. When the index is the right one (mask_check returns true), we can just assume that this is the right offset and return module_base + this offset.
 @@ -751,7 +878,7 @@ So little homework: Modify the function so you can pass the most commonly used s
 Remember that you will need to dereference the address found and add some "offset bytes" to it in order to land on the right offset.
 [SIZE="3"][FONT="Franklin Gothic Medium"][I][B]Getting netvars dynamically: Netvar Managers and recursion[/B][/I][/FONT][/SIZE]
#### [Getting netvars dynamically: Netvar Managers and recursion](#getting-netvars-dynamically-netvar-managers-and-recursion)
 Some could argue that since every single offset can be sig-scanned, netvar offsets can be sig-scanned too, and that would be more than true, but there is a way better and cleaner way to grab netvar offsets specifically: setting up a netvar manager!
 @@ -760,7 +887,8 @@ We already spoke about what netvars are and how the game uses them itself, remem
 We already know what netvars are, but how do these work exactly inside the engine?
Let's look at the structure of a ClientClass inside the Source Engine
[CODE]
 ````cpp
class ClientClass;
 typedef IClientNetworkable*(*CreateClientClassFn)(int iEntNum, int iSerialNum);
@@ -769,114 +897,119 @@ typedef IClientNetworkable*(*CreateEventFn)();
class ClientClass
{
public:
	CreateClientClassFn		m_pCreateFn;
	CreateEventFn			m_pCreateEventFn;
	char*				m_pNetworkName;
	RecvTable*			m_pRecvTable;
	ClientClass*			m_pNext;
	int				m_ClassID;
    CreateClientClassFn        m_pCreateFn;
    CreateEventFn              m_pCreateEventFn;
    char*                      m_pNetworkName;
    RecvTable*                 m_pRecvTable;
    ClientClass*               m_pNext;
    int                        m_ClassID;
};
[/CODE]
````
 [I]m_pCreateFn [/I] is a pointer to the function that gets called whenever we create a new entity of a certain class. 
_m_pCreateFn_ is a pointer to the function that gets called whenever we create a new entity of a certain class. 
For example, some code needs to be run whenever the creates a new instance of class "CC4", or "CAK47".
[I]m_pNetworkName[/I] is ofc the name of the class, specifically. It can be "CCSPlayer", "CCSPlayerResource" or even "CChicken". Notice the prefix '[B]C[/B]' that stands for [B]c[/B]lass.
[I]m_pRecvTable[/I] we will get to it in a moment, this is what we really need to accomplish our netvar manager.
[I]m_pNext[/I] is a pointer to the next ClientClass in the list. We can now understand that there is in the game a linked list of clientclasses and we can access it both externally and internally.
_m_pNetworkName_ is ofc the name of the class, specifically. It can be "CCSPlayer", "CCSPlayerResource" or even "CChicken". Notice the prefix '**C**' that stands for **c**lass.
_m_pRecvTable_ we will get to it in a moment, this is what we really need to accomplish our netvar manager.
_m_pNext_ is a pointer to the next ClientClass in the list. We can now understand that there is in the game a linked list of clientclasses and we can access it both externally and internally.
 Externally, this is done by sig-scanning the offset for ClientClassHead, which is the head of the list. Using the head of the list, we can walk the whole list until we reach nullptr.
[URL="https://github.com/frk1/hazedumper/blob/master/config.json#L396"]HazeDumper[/URL] already gives us all we need, basically:
[CODE]
[HazeDumper](https://github.com/frk1/hazedumper/blob/master/config.json#L396)
 already gives us all we need, basically:
 ````json
"dwGetAllClasses": {
      "extra": 1,
      "mode_read": true,
      "extra":         1,
      "mode_read":     true,
      "mode_subtract": true,
      "module": "client.dll",
      "offset": 0,
      "pattern": "A1 ? ? ? ? C3 CC CC CC CC CC CC CC CC CC CC A1 ? ? ? ? B9"
      "module":        "client.dll",
      "offset":        0,
      "pattern":       "A1 ? ? ? ? C3 CC CC CC CC CC CC CC CC CC CC A1 ? ? ? ? B9"
}
[/CODE]
````
 Or we can use the static offset which is *atm* 0x4F89EBC but it's due to changes in future patches.
 Internally, it's even easier. We can just grab the base client interface and call the function GetAllClasses() directly. GetAllClasses() returns a pointer to the head of the linked list of clientclasses, which comes really handy. Externally, we need to grab the pointer returned by this function.
 [I]m_ClassID[/I] should be obvious: it's the numerical class id to identify the class.
_m_ClassID_ should be obvious: it's the numerical class id to identify the class.
Simply by walking through the linked list of classes, we can easily dump and format every single class id, which is exactly how those class id enum dumps are done.
 Returning to [I]m_pRecvTable[/I]:
Returning to _m_pRecvTable_:
 [CODE]
````cpp
class RecvTable
{
public:
	RecvProp*                m_pProps;
	int                      m_nProps;
	void*                    m_pDecoder;
	char*                    m_pNetTableName;
	bool                     m_bInitialized;
	bool                     m_bInMainList;
    RecvProp*       m_pProps;
    int             m_nProps;
    void*           m_pDecoder;
    char*           m_pNetTableName;
    bool            m_bInitialized;
    bool            m_bInMainList;
};
[/CODE]
````
 From this struct, we are really interested in only a few of these elements.
 [I]m_pProps[/I] points to the beginning of an array of properties.
_m_pProps_ points to the beginning of an array of properties.
An example of property is m_iHealth or m_iTeamNum.
 [I]m_nProps[/I] contains the number of elements in the array of props. It is useful when we want to loop over all the props.
_m_nProps_ contains the number of elements in the array of props. It is useful when we want to loop over all the props.
 [I]m_pNetTableName[/I] this is the name of the table. Remember the name of the class? "CC4" or "CCSPlayer"? Here, the name is just the same but with "DT_" as prefix.
_m_pNetTableName_ this is the name of the table. Remember the name of the class? "CC4" or "CCSPlayer"? Here, the name is just the same but with "DT_" as prefix.
"CC4" -> "DT_C4"
"CCSPlayer" -> "DT_CSPlayer", where DT stands for [B]D[/B]ata [B]T[/B]able, ofc.
"CCSPlayer" -> "DT_CSPlayer", where DT stands for **D**ata **T**able, ofc.
 Now let's take a look at the struct that describes a property "RecvProp":
 [CODE]
````cpp
class RecvProp
{
public:
	char*                    m_pVarName;
	SendPropType             m_RecvType;
	int                      m_Flags;
	int                      m_StringBufferSize;
	bool                     m_bInsideArray;
	const void*              m_pExtraData;
	RecvProp*                m_pArrayProp;
	void*                    m_ArrayLengthProxy;
	RecvVarProxyFn           m_ProxyFn;
	void*                    m_DataTableProxyFn;
	RecvTable*               m_pDataTable;
	int                      m_Offset;
	int                      m_ElementStride;
	int                      m_nElements;
	const char*              m_pParentArrayPropName;
    char*                    m_pVarName;
    SendPropType             m_RecvType;
    int                      m_Flags;
    int                      m_StringBufferSize;
    bool                     m_bInsideArray;
    const void*              m_pExtraData;
    RecvProp*                m_pArrayProp;
    void*                    m_ArrayLengthProxy;
    RecvVarProxyFn           m_ProxyFn;
    void*                    m_DataTableProxyFn;
    RecvTable*               m_pDataTable;
    int                      m_Offset;
    int                      m_ElementStride;
    int                      m_nElements;
    const char*              m_pParentArrayPropName;
};
[/CODE]
````
 Damn, that's a lot of elements! Let's analyze them a bit.
 [I]m_pVarName[/I] is kinda obvious. It's a C-style string containing the name of the property. For example "m_iHealth" or "m_iTeamNum".
_m_pVarName_ is kinda obvious. It's a C-style string containing the name of the property. For example "m_iHealth" or "m_iTeamNum".
 _m_RecvType_ is the type of the property. It can be:
 [I]m_RecvType[/I] is the type of the property. It can be:
[CODE]
````cpp
enum class SendPropType
{
	DPT_Int = 0,
	DPT_Float,
	DPT_Vector,
	DPT_VectorXY,	// Only encodes the XY of a vector, ignores Z
	DPT_String,
	DPT_Array,		// An array of the base types (can't be of datatables).
	DPT_DataTable,
	DPT_Int64,
	DPT_NUMSendPropTypes
    DPT_Int = 0,
    DPT_Float,
    DPT_Vector,
    DPT_VectorXY,     // Only encodes the XY of a vector, ignores Z
    DPT_String,
    DPT_Array,        // An array of the base types (can't be of datatables).
    DPT_DataTable,
    DPT_Int64,
    DPT_NUMSendPropTypes
};
[/CODE]
````
 [I]m_StringBufferSize[/I] is the maximum size of the string buffer in case the property is a string. To give a clear example, think about the property "m_szLastPlaceName" from DT_BasePlayer. It is a string that contains the name of the last map place visited by a certain player, for example "Long", "Pit", "Tunnel", you know. It can be max 18 chars long, so m_StringBufferSize = 18.
_m_StringBufferSize_ is the maximum size of the string buffer in case the property is a string. To give a clear example, think about the property "m_szLastPlaceName" from DT_BasePlayer. It is a string that contains the name of the last map place visited by a certain player, for example "Long", "Pit", "Tunnel", you know. It can be max 18 chars long, so m_StringBufferSize = 18.
 ......
 [B][I]...WORK IN PROGRESS...[/I][/B]
**_...WORK IN PROGRESS..._**
 This guide, as I already said, is not complete and needs a lot of work. I'll update it with new sections and chapters throughout these days. You can help me updating/correcting/getting better this guide using his [URL="https://github.com/DoubleHub/CSGOCheatMaking101/blob/master/Guide.txt"]GitHub repo[/URL].
This guide, as I already said, is not complete and needs a lot of work. I'll update it with new sections and chapters throughout these days.
You can help me updating/correcting/getting better this guide using his [GitHub repo](https://github.com/DoubleHub/CSGOCheatMaking101/blob/master/Guide.txt).
