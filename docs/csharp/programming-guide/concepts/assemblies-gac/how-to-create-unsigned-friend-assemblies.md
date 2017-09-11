---
title: "Como criar assemblies amigáveis não assinados (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 967436204ab0824a510c12dc4c6e288d91d7dfa0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-c"></a><span data-ttu-id="2e608-102">Como criar assemblies amigáveis não assinados (C#)</span><span class="sxs-lookup"><span data-stu-id="2e608-102">How to: Create Unsigned Friend Assemblies (C#)</span></span>
<span data-ttu-id="2e608-103">Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.</span><span class="sxs-lookup"><span data-stu-id="2e608-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="2e608-104">Para criar um assembly e um assembly amigável</span><span class="sxs-lookup"><span data-stu-id="2e608-104">To create an assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="2e608-105">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2e608-105">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="2e608-106">Crie um arquivo do C# chamado `friend_signed_A.` que contenha o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="2e608-106">Create a C# file named `friend_signed_A.` that contains the following code.</span></span> <span data-ttu-id="2e608-107">O código usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar friend_signed_B como um assembly autorizado.</span><span class="sxs-lookup"><span data-stu-id="2e608-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
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
  
3.  <span data-ttu-id="2e608-108">Compile e assine o friend_signed_A usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="2e608-108">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library friend_unsigned_A.cs  
    ```  
  
4.  <span data-ttu-id="2e608-109">Crie um arquivo do C# chamado `friend_unsigned_B` que contenha o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="2e608-109">Create a C# file named `friend_unsigned_B` that contains the following code.</span></span> <span data-ttu-id="2e608-110">Como friend_unsigned_A especifica friend_unsigned_B como um assembly amigável, o código em friend_unsigned_B pode acessar tipos `internal` e membros de friend_unsigned_A.</span><span class="sxs-lookup"><span data-stu-id="2e608-110">Because friend_unsigned_A specifies friend_unsigned_B as a friend assembly, the code in friend_unsigned_B can access `internal` types and members from friend_unsigned_A.</span></span>  
  
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
  
5.  <span data-ttu-id="2e608-111">Compile friend_signed_B usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e608-111">Compile friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs  
    ```  
  
     <span data-ttu-id="2e608-112">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2e608-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="2e608-113">Você deve especificar explicitamente o nome do assembly de saída (.exe ou .dll) usando a opção do compilador `/out`.</span><span class="sxs-lookup"><span data-stu-id="2e608-113">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span> <span data-ttu-id="2e608-114">Para obter mais informações, consulte [/out (opções do compilador C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2e608-114">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
6.  <span data-ttu-id="2e608-115">Execute o arquivo friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="2e608-115">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="2e608-116">O programa imprime duas cadeias de caracteres: "Class1.Test" e "Class2.Test".</span><span class="sxs-lookup"><span data-stu-id="2e608-116">The program prints two strings: "Class1.Test" and "Class2.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2e608-117">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e608-117">.NET Framework Security</span></span>  
 <span data-ttu-id="2e608-118">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="2e608-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="2e608-119">A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla a visibilidade de membros e tipos de `internal`.</span><span class="sxs-lookup"><span data-stu-id="2e608-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e608-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e608-120">See Also</span></span>  
 <span data-ttu-id="2e608-121"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="2e608-121"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
 <span data-ttu-id="2e608-122">[Assemblies e o Cache de Assembly Global (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="2e608-122">[Assemblies and the Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
 <span data-ttu-id="2e608-123">[Assemblies amigáveis (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="2e608-123">[Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span></span>  
 <span data-ttu-id="2e608-124">[Como criar assemblies amigáveis assinados (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="2e608-124">[How to: Create Signed Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span></span>  
 [<span data-ttu-id="2e608-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2e608-125">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)

