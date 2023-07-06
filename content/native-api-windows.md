---
title: Pemrograman menggunakan Native API Windows
desc: Membahas sedikit tentang Windows Internals dan sesuatu dibalik Win32 API
author: KawaiiGhost
github: kawaii-ghost
twitter:
telegram: kawaiighost
date: 2023-07-06
cover: https://link/to/image (not really required, leave it empty by deleting this line)
categories:
    - reverse-engineering
    - tutorial
    - windows-internals
---

Windows adalah sistem operasi yang antimainstream dibandingkan dengan sistem operasi \*nix layaknya Linux dan MacOS.

Bagaimana tidak, Ia satu-satunya sistem operasi yang terkenal tapi menggunakan konsep ["everything is an object"](https://learn.microsoft.com/en-us/previous-versions/ms810501(v=msdn.10)?redirectedfrom=MSDN)

sementara Linux dan MacOS menggunakan konsep *NIX, ["everything is a file"](https://en.wikipedia.org/wiki/Everything_is_a_file).

Selain itu, dibandingkan dengan kedua OS di atas, Windows memiliki backward compability yang bagus.

Para programmer di Windows menggunakan Win32 API untuk mengembangkan aplikasi di Windows. Tetapi, itu semua tidaklah native atau menggunakan system call langsung yang tersedia di kernel NT.

`kernel32.dll` tidak menyediakan system call yang ada, dll tersebut hanya bertugas sebagai wrapper ke `ntdll.dll`, di mana semua native api windows yang bisa dipanggil dari usermode.

Native API di Windows yang biasa diterjemahkan oleh Win32 API (termasuk tapi tidak terbatas) memiliki awalan **Nt\*** atau **Rtl\***.

Variant **Nt\*** adalah system call yang tersedia di kernel sementara **Rtl\*** adalah wrapper khusus untuk 

Contohnya, `WriteFile` menjadi `NtWriteFile` dan `ExitProcess` menjadi `RtlExitUserProcess`.



