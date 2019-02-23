---
title: 'Como: Criar Assemblies amigáveis não assinados (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
ms.openlocfilehash: 8c1d5fb24d0032e88b951eefa1bd7a3a8c6ccb88
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748122"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Como: Criar Assemblies amigáveis não assinados (Visual Basic)
Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Para criar um assembly e um assembly amigável  
  
1.  Abra um prompt de comando.  
  
2.  Crie um arquivo de Visual Basic chamado `friend_signed_A.` que contém o código a seguir. O código usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar friend_signed_B como um assembly autorizado.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
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
  
3.  Compile e assine o friend_signed_A usando o seguinte comando.  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Crie um arquivo de Visual Basic chamado `friend_unsigned_B` que contém o código a seguir. Como friend_unsigned_A especifica friend_unsigned_B como um assembly amigável, o código em friend_unsigned_B pode acessar tipos `Friend` e membros de friend_unsigned_A.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
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
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Você pode definir explicitamente o assembly usando o `/out` opção de compilador.  
  
6.  Execute o arquivo friend_signed_B.exe.  
  
     O programa exibe duas cadeias de caracteres: "Class1.Test" e "Class2.Test".  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla a visibilidade de membros e tipos de `Friend`.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Assemblies no .NET](../../../../standard/assembly/index.md)
- [Assemblies amigáveis (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)
- [Como: Criar Assemblies amigáveis assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Conceitos do guia de programação](../../../../visual-basic/programming-guide/concepts/index.md)
