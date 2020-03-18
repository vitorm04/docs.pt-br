---
title: 'Como: Criar assembléias de amigos não assinados'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352430"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Como: Criar assembléias de amigos não assinados

Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Crie uma assembléia e uma reunião de amigos

1. Abra um prompt de comando.

2. Crie um arquivo C# ou Visual Basic chamado *friend_unsigned_A* que contenha o seguinte código. O código <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> usa o atributo para declarar *friend_unsigned_B* como uma assembléia de amigos.

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

3. Compilar e assinar *friend_unsigned_A* usando o seguinte comando:

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Crie um arquivo C# ou Visual Basic chamado *friend_unsigned_B* que contenha o seguinte código. Como *friend_unsigned_A* especifica *friend_unsigned_B* como uma reunião de amigos, o código em *friend_unsigned_B* pode `internal` acessar (C#) ou `Friend` (Visual Basic) tipos e membros a partir de *friend_unsigned_A*.

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

5. Compilar *friend_unsigned_B* usando o seguinte comando.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Você deve especificar explicitamente o nome do conjunto de saída ( `-out` *.exe* ou *.dll*) usando a opção compilador. Para obter mais informações, consulte [-out (opções de compilador C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. Execute o arquivo *friend_unsigned_B.exe.*

   O programa produz duas strings: **Class1.Test** e **Class2.Test**.

## <a name="net-security"></a>Segurança do .NET

Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. A principal diferença <xref:System.Security.Permissions.StrongNameIdentityPermission> é que pode exigir permissões de segurança <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para executar uma determinada `internal` `Friend` seção de código, enquanto o atributo controla a visibilidade de ou (Visual Basic) tipos e membros.

## <a name="see-also"></a>Confira também

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Assemblies no .NET](index.md)
- [Assemblies amigáveis](friend.md)
- [Como: Criar assembléias de amigos assinados](create-signed-friend.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
