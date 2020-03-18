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
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="46ac0-102">Como: Criar assembléias de amigos não assinados</span><span class="sxs-lookup"><span data-stu-id="46ac0-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="46ac0-103">Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.</span><span class="sxs-lookup"><span data-stu-id="46ac0-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="46ac0-104">Crie uma assembléia e uma reunião de amigos</span><span class="sxs-lookup"><span data-stu-id="46ac0-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="46ac0-105">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="46ac0-105">Open a command prompt.</span></span>

2. <span data-ttu-id="46ac0-106">Crie um arquivo C# ou Visual Basic chamado *friend_unsigned_A* que contenha o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="46ac0-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="46ac0-107">O código <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> usa o atributo para declarar *friend_unsigned_B* como uma assembléia de amigos.</span><span class="sxs-lookup"><span data-stu-id="46ac0-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="46ac0-108">Compilar e assinar *friend_unsigned_A* usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="46ac0-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="46ac0-109">Crie um arquivo C# ou Visual Basic chamado *friend_unsigned_B* que contenha o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="46ac0-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="46ac0-110">Como *friend_unsigned_A* especifica *friend_unsigned_B* como uma reunião de amigos, o código em *friend_unsigned_B* pode `internal` acessar (C#) ou `Friend` (Visual Basic) tipos e membros a partir de *friend_unsigned_A*.</span><span class="sxs-lookup"><span data-stu-id="46ac0-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="46ac0-111">Compilar *friend_unsigned_B* usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="46ac0-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="46ac0-112">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="46ac0-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="46ac0-113">Você deve especificar explicitamente o nome do conjunto de saída ( `-out` *.exe* ou *.dll*) usando a opção compilador.</span><span class="sxs-lookup"><span data-stu-id="46ac0-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="46ac0-114">Para obter mais informações, consulte [-out (opções de compilador C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="46ac0-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="46ac0-115">Execute o arquivo *friend_unsigned_B.exe.*</span><span class="sxs-lookup"><span data-stu-id="46ac0-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="46ac0-116">O programa produz duas strings: **Class1.Test** e **Class2.Test**.</span><span class="sxs-lookup"><span data-stu-id="46ac0-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="46ac0-117">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="46ac0-117">.NET security</span></span>

<span data-ttu-id="46ac0-118">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="46ac0-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="46ac0-119">A principal diferença <xref:System.Security.Permissions.StrongNameIdentityPermission> é que pode exigir permissões de segurança <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para executar uma determinada `internal` `Friend` seção de código, enquanto o atributo controla a visibilidade de ou (Visual Basic) tipos e membros.</span><span class="sxs-lookup"><span data-stu-id="46ac0-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="46ac0-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="46ac0-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="46ac0-121">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="46ac0-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="46ac0-122">Assemblies amigáveis</span><span class="sxs-lookup"><span data-stu-id="46ac0-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="46ac0-123">Como: Criar assembléias de amigos assinados</span><span class="sxs-lookup"><span data-stu-id="46ac0-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="46ac0-124">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="46ac0-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="46ac0-125">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46ac0-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
