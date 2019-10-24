---
title: 'Como: criar assemblies Friend não assinados'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: d8fdc3061067d85498dc5bbed7bf324f99169a36
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774344"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Como: criar assemblies Friend não assinados

Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Criar um assembly e um assembly Friend

1. Abra um prompt de comando.

2. Crie um C# arquivo ou Visual Basic chamado *friend_unsigned_A* que contém o código a seguir. O código usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar *friend_unsigned_B* como um assembly Friend.

   ```csharp
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

3. Compile e assine o *friend_unsigned_A* usando o seguinte comando:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Crie um C# arquivo ou Visual Basic chamado *friend_unsigned_B* que contém o código a seguir. Como *friend_unsigned_A* especifica *friend_unsigned_B* como um assembly Friend, o código em *friend_unsigned_B* pode acessar tipos `internal`C#() ou `Friend` (Visual Basic) e membros de *friend_unsigned_A*.

   ```csharp
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

5. Compile o *friend_unsigned_B* usando o comando a seguir.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Você deve especificar explicitamente o nome do assembly de saída ( *. exe* ou *. dll*) usando a opção de compilador `-out`. Para obter mais informações, consulte [-outC# (opções do compilador)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. Execute o arquivo *friend_unsigned_B. exe* .

   O programa produz duas cadeias de caracteres: **Class1. Test** e **class2. Test**.

## <a name="net-security"></a>Segurança do .NET

Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode exigir permissões de segurança para executar uma determinada seção de código, enquanto o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla a visibilidade dos membros e tipos `internal` ou `Friend` (Visual Basic).

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Assemblies no .NET](index.md)
- [Assemblies Friend](friend.md)
- [Como criar assemblies Friend assinados](create-signed-friend.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
