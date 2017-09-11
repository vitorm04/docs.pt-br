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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d184b5d6f8334df46351d3f2974f1fb91e54a492
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a><span data-ttu-id="db6d6-102">Como: Criar Assemblies amigáveis não assinados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db6d6-102">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="db6d6-103">Este exemplo mostra como usar assemblies amigáveis com assemblies não assinados.</span><span class="sxs-lookup"><span data-stu-id="db6d6-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="db6d6-104">Para criar um assembly e um conjunto de módulos de amigo</span><span class="sxs-lookup"><span data-stu-id="db6d6-104">To create an assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="db6d6-105">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="db6d6-105">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="db6d6-106">Crie um arquivo do Visual Basic chamado `friend_signed_A.` que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="db6d6-106">Create a Visual Basic file named `friend_signed_A.` that contains the following code.</span></span> <span data-ttu-id="db6d6-107">O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo declarar friend_signed_B como um assembly autorizado.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="db6d6-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
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
  
3.  <span data-ttu-id="db6d6-108">Compile e assinar friend_signed_A usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="db6d6-108">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  <span data-ttu-id="db6d6-109">Crie um arquivo do Visual Basic chamado `friend_unsigned_B` que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="db6d6-109">Create a Visual Basic file named `friend_unsigned_B` that contains the following code.</span></span> <span data-ttu-id="db6d6-110">Como friend_unsigned_A Especifica friend_unsigned_B como um assembly autorizado, pode acessar o código em friend_unsigned_B `Friend` tipos e membros do friend_unsigned_A.</span><span class="sxs-lookup"><span data-stu-id="db6d6-110">Because friend_unsigned_A specifies friend_unsigned_B as a friend assembly, the code in friend_unsigned_B can access `Friend` types and members from friend_unsigned_A.</span></span>  
  
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
  
5.  <span data-ttu-id="db6d6-111">Compile friend_signed_B usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="db6d6-111">Compile friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     <span data-ttu-id="db6d6-112">O nome do assembly gerado pelo compilador deve corresponder o nome do assembly autorizado que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="db6d6-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="db6d6-113">Você pode definir explicitamente o assembly usando o `/out` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="db6d6-113">You can explicitly set the assembly by using the `/out` compiler option.</span></span>  
  
6.  <span data-ttu-id="db6d6-114">Execute o arquivo friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="db6d6-114">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="db6d6-115">O programa imprime duas cadeias de caracteres: "Class1.Test" e "Class2.Test".</span><span class="sxs-lookup"><span data-stu-id="db6d6-115">The program prints two strings: "Class1.Test" and "Class2.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="db6d6-116">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db6d6-116">.NET Framework Security</span></span>  
 <span data-ttu-id="db6d6-117">Há semelhanças entre o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo e a <xref:System.Security.Permissions.StrongNameIdentityPermission>classe.</xref:System.Security.Permissions.StrongNameIdentityPermission> </xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="db6d6-117">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="db6d6-118">A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission>pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo controla a visibilidade de `Friend` tipos e membros.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="db6d6-118">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6d6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db6d6-119">See Also</span></span>  
 <span data-ttu-id="db6d6-120"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="db6d6-120"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
<span data-ttu-id="db6d6-121"> [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="db6d6-121"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="db6d6-122"> [Assemblies amigáveis (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="db6d6-122"> [Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span></span>  
<span data-ttu-id="db6d6-123"> [Como: Criar Assemblies amigáveis assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="db6d6-123"> [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span></span>  
<span data-ttu-id="db6d6-124"> [Conceitos do guia de programação](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="db6d6-124"> [Programming Guide Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
