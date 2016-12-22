---
title: "Como: Criar Assemblies amig&#225;veis n&#227;o assinados (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: Criar Assemblies amig&#225;veis n&#227;o assinados (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.  
  
### Para criar um assembly e um conjunto de módulos de amigo  
  
1.  Abra um prompt de comando.  
  
2.  Crie um arquivo c\# chamado `friend_signed_A.` que contém o código a seguir. O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo declarar friend\_signed\_B como um assembly autorizado.  
  
    ```c#  
    // friend_unsigned_A.cs  
    // Compile with:   
    // csc /target:library friend_unsigned_A.cs  
    using System.Runtime.CompilerServices;  
    using System;  
  
    [assembly: InternalsVisibleTo("friend_unsigned_B")]  
  
    // Type is internal by default.  
    class Class1  
    {  
        public void Test()  
        {  
            Console.WriteLine("Class1.Test");  
        }  
    }  
  
    // Public type with internal member.  
    public class Class2  
    {  
        internal void Test()  
        {  
            Console.WriteLine("Class2.Test");  
        }  
    }  
    ```  
  
3.  Compile e assinar friend\_signed\_A usando o comando a seguir.  
  
    ```c#  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  Crie um arquivo c\# chamado `friend_unsigned_B` que contém o código a seguir. Como friend\_unsigned\_A Especifica friend\_unsigned\_B como um assembly autorizado, pode acessar o código em friend\_unsigned\_B `internal` tipos e membros do friend\_unsigned\_A.  
  
    ```c#  
    // friend_unsigned_B.cs  
    // Compile with:   
    // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            // Access an internal type.  
            Class1 inst1 = new Class1();  
            inst1.Test();  
  
            Class2 inst2 = new Class2();  
            // Access an internal member of a public type.  
            inst2.Test();  
  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
5.  Compile friend\_signed\_B usando o comando a seguir.  
  
    ```c#  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder o nome do assembly autorizado que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo. Você deve especificar explicitamente o nome do assembly de saída \(.exe ou. dll\) usando o `/out` opção de compilador. Para obter mais informações, consulte [\/out \(Set Output File Name\)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
6.  Execute o arquivo friend\_signed\_B.exe.  
  
     O programa imprime duas cadeias de caracteres: "Class1.Test" e "Class2.Test".  
  
## Segurança do .NET Framework  
 Há semelhanças entre o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo e o <xref:System.Security.Permissions.StrongNameIdentityPermission> classe. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo controla a visibilidade de `internal` tipos e membros.  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblies e o Cache de Assembly Global \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/assemblies-and-the-global-assembly-cache.md)   
 [Assemblies amigáveis \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como: Criar Assemblies amigáveis assinados \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)