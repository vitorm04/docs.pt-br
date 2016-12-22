---
title: "Como: Criar Assemblies amig&#225;veis n&#227;o assinados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: Criar Assemblies amig&#225;veis n&#227;o assinados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.  
  
### Para criar um assembly e um conjunto de módulos de amigo  
  
1.  Abra um prompt de comando.  
  
2.  Crie um arquivo do Visual Basic chamado `friend_signed_A.` que contém o código a seguir. O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo declarar friend\_signed\_B como um assembly autorizado.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  Compile e assinar friend\_signed\_A usando o comando a seguir.  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  Crie um arquivo do Visual Basic chamado `friend_unsigned_B` que contém o código a seguir. Como friend\_unsigned\_A Especifica friend\_unsigned\_B como um assembly autorizado, pode acessar o código em friend\_unsigned\_B `Friend` tipos e membros do friend\_unsigned\_A.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  Compile friend\_signed\_B usando o comando a seguir.  
  
    ```vb#  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder o nome do assembly autorizado que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo. Você pode definir explicitamente o assembly usando o `/out` opção de compilador.  
  
6.  Execute o arquivo friend\_signed\_B.exe.  
  
     O programa imprime duas cadeias de caracteres: "Class1.Test" e "Class2.Test".  
  
## Segurança do .NET Framework  
 Há semelhanças entre o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo e o <xref:System.Security.Permissions.StrongNameIdentityPermission> classe. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo controla a visibilidade de `Friend` tipos e membros.  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblies e o Cache de Assembly Global \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Assemblies amigáveis \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como: Criar Assemblies amigáveis assinados \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)