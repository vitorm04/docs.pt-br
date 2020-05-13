---
title: 'Como: criar assemblies Friend não assinados'
description: Este artigo mostra como usar os assemblies Friend com assemblies que não são assinados. Ele inclui informações sobre a segurança do .NET.
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 8d3e13669c36048759fedeb3df1bfb59fd476317
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378965"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="2df07-104">Como: criar assemblies Friend não assinados</span><span class="sxs-lookup"><span data-stu-id="2df07-104">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="2df07-105">Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.</span><span class="sxs-lookup"><span data-stu-id="2df07-105">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="2df07-106">Criar um assembly e um assembly Friend</span><span class="sxs-lookup"><span data-stu-id="2df07-106">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="2df07-107">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2df07-107">Open a command prompt.</span></span>

2. <span data-ttu-id="2df07-108">Crie um arquivo em C# ou Visual Basic chamado *friend_unsigned_A* que contenha o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2df07-108">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="2df07-109">O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo para declarar *friend_unsigned_B* como um assembly Friend.</span><span class="sxs-lookup"><span data-stu-id="2df07-109">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="2df07-110">Compile e assine *friend_unsigned_A* usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2df07-110">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="2df07-111">Crie um arquivo em C# ou Visual Basic chamado *friend_unsigned_B* que contenha o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2df07-111">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="2df07-112">Como *friend_unsigned_A* especifica *friend_unsigned_B* como um assembly Friend, o código em *friend_unsigned_B* pode acessar `internal` `Friend` os tipos e os membros do (C#) ou (Visual Basic) de *friend_unsigned_A*.</span><span class="sxs-lookup"><span data-stu-id="2df07-112">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="2df07-113">Compile *friend_unsigned_B* usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2df07-113">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="2df07-114">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2df07-114">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="2df07-115">Você deve especificar explicitamente o nome do assembly de saída (*. exe* ou *. dll*) usando a `-out` opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="2df07-115">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="2df07-116">Para obter mais informações, consulte [-out (opções do compilador C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="2df07-116">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="2df07-117">Execute o arquivo *friend_unsigned_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="2df07-117">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="2df07-118">O programa produz duas cadeias de caracteres: **Class1. Test** e **class2. Test**.</span><span class="sxs-lookup"><span data-stu-id="2df07-118">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="2df07-119">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="2df07-119">.NET security</span></span>

<span data-ttu-id="2df07-120">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="2df07-120">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="2df07-121">A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> o pode exigir que as permissões de segurança executem uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo controla a visibilidade dos `internal` `Friend` tipos e dos membros de ou (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2df07-121">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="2df07-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="2df07-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="2df07-123">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="2df07-123">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="2df07-124">Assemblies amigáveis</span><span class="sxs-lookup"><span data-stu-id="2df07-124">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="2df07-125">Como criar assemblies Friend assinados</span><span class="sxs-lookup"><span data-stu-id="2df07-125">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="2df07-126">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="2df07-126">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2df07-127">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2df07-127">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
