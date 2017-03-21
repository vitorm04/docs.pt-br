---
title: "Como: Criar Assemblies amigáveis não assinados (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ceddb35c306f72c8927deda326d9fcca6c75d786
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Como: Criar Assemblies amigáveis não assinados (Visual Basic)
Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Para criar um assembly e um conjunto de módulos de amigo  
  
1.  Abra um prompt de comando.  
  
2.  Crie um arquivo do Visual Basic chamado `friend_signed_A.` que contém o código a seguir. O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo declarar friend_signed_B como um assembly autorizado.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
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
  
3.  Compile e assinar friend_signed_A usando o comando a seguir.  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  Crie um arquivo do Visual Basic chamado `friend_unsigned_B` que contém o código a seguir. Como friend_unsigned_A Especifica friend_unsigned_B como um assembly autorizado, pode acessar o código em friend_unsigned_B `Friend` tipos e membros do friend_unsigned_A.  
  
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
  
5.  Compile friend_signed_B usando o comando a seguir.  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder o nome do assembly autorizado que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Você pode definir explicitamente o assembly usando o `/out` opção de compilador.  
  
6.  Execute o arquivo friend_signed_B.exe.  
  
     O programa imprime duas cadeias de caracteres: "Class1.Test" e "Class2.Test".  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Há semelhanças entre o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo e a <xref:System.Security.Permissions.StrongNameIdentityPermission>classe.</xref:System.Security.Permissions.StrongNameIdentityPermission> </xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission>pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo controla a visibilidade de `Friend` tipos e membros.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Assemblies amigáveis (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Como: Criar Assemblies amigáveis assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Conceitos do guia de programação](../../../../visual-basic/programming-guide/concepts/index.md)
