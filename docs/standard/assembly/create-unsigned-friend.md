---
title: 'Como: Criar assemblies Friend não assinados'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9d5699f772dba994b10408d15422faa3c5931f45
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991690"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="1e689-102">Como: Criar assemblies Friend não assinados</span><span class="sxs-lookup"><span data-stu-id="1e689-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="1e689-103">Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.</span><span class="sxs-lookup"><span data-stu-id="1e689-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="1e689-104">Criar um assembly e um assembly Friend</span><span class="sxs-lookup"><span data-stu-id="1e689-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="1e689-105">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="1e689-105">Open a command prompt.</span></span>

2. <span data-ttu-id="1e689-106">Crie um C# arquivo ou Visual Basic chamado *friend_unsigned_A* que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1e689-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="1e689-107">O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo para declarar *friend_unsigned_B* como um assembly Friend.</span><span class="sxs-lookup"><span data-stu-id="1e689-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

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

3. <span data-ttu-id="1e689-108">Compile e assine o *friend_unsigned_A* usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="1e689-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="1e689-109">Crie um C# arquivo ou Visual Basic chamado *friend_unsigned_B* que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1e689-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="1e689-110">Como *friend_unsigned_A* especifica *friend_unsigned_B* como um assembly Friend, o código em *friend_unsigned_B* pode acessar `internal` osC#tipos e `Friend` Membros () ou (Visual Basic) de *friend_unsigned_A* .</span><span class="sxs-lookup"><span data-stu-id="1e689-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

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

5. <span data-ttu-id="1e689-111">Compile o *friend_unsigned_B* usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="1e689-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="1e689-112">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1e689-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="1e689-113">Você deve especificar explicitamente o nome do assembly de saída ( *. exe* ou *. dll*) usando a opção `/out` do compilador.</span><span class="sxs-lookup"><span data-stu-id="1e689-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="1e689-114">Para obter mais informações, consulte [/outC# (opções do compilador)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="1e689-114">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="1e689-115">Execute o arquivo *friend_unsigned_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="1e689-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="1e689-116">O programa gera duas cadeias de caracteres: **Class1. Test** e **class2. Test**.</span><span class="sxs-lookup"><span data-stu-id="1e689-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="1e689-117">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="1e689-117">.NET security</span></span>

<span data-ttu-id="1e689-118">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="1e689-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="1e689-119">A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> o pode exigir que as permissões de segurança executem uma determinada seção de <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> código, enquanto o atributo `internal` controla `Friend` a visibilidade dos tipos e dos membros de ou (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1e689-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e689-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e689-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="1e689-121">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="1e689-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="1e689-122">Assemblies Friend</span><span class="sxs-lookup"><span data-stu-id="1e689-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="1e689-123">Como: Criar assemblies Friend assinados</span><span class="sxs-lookup"><span data-stu-id="1e689-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="1e689-124">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="1e689-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1e689-125">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e689-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
