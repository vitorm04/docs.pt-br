---
title: "Como: Criar Assemblies amigáveis assinados (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
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
ms.openlocfilehash: a8a7df331c8cd93de45d902cb9b6c67460952c6d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="6272e-102">Como: Criar Assemblies amigáveis assinados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6272e-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="6272e-103">Este exemplo mostra como usar assemblies amigáveis com assemblies com nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="6272e-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="6272e-104">Os dois assemblies devem ser nomeadas forte.</span><span class="sxs-lookup"><span data-stu-id="6272e-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="6272e-105">Embora os dois assemblies neste exemplo usam as mesmas chaves, você pode usar chaves diferentes para dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="6272e-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="6272e-106">Para criar um assembly assinado e um conjunto de módulos de amigo</span><span class="sxs-lookup"><span data-stu-id="6272e-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="6272e-107">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="6272e-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="6272e-108">Use a seguinte sequência de comandos com a ferramenta nome forte para gerar um arquivo de chaves e exibir sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="6272e-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="6272e-109">Para saber mais, veja [Sn.exe (Ferramenta de Nome Forte)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="6272e-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="6272e-110">Gerar uma chave de nome forte para este exemplo e armazená-lo no arquivo FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="6272e-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="6272e-111">Extrair a chave pública de FriendAssemblies.snk e colocá-lo em FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="6272e-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="6272e-112">Exiba a chave pública armazenada no arquivo FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="6272e-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="6272e-113">Crie um arquivo do Visual Basic chamado `friend_signed_A` que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6272e-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="6272e-114">O código usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo declarar friend_signed_B como um assembly autorizado.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="6272e-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="6272e-115">A ferramenta nome forte gera uma nova chave pública sempre que ele executa.</span><span class="sxs-lookup"><span data-stu-id="6272e-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="6272e-116">Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6272e-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  <span data-ttu-id="6272e-117">Compile e assinar friend_signed_A usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="6272e-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  <span data-ttu-id="6272e-118">Criar um arquivo do Visual Basic chamado `friend_signed_B` e contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6272e-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="6272e-119">Como friend_signed_A Especifica friend_signed_B como um assembly autorizado, pode acessar o código em friend_signed_B `Friend` tipos e membros do friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="6272e-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="6272e-120">O arquivo contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6272e-120">The file contains the following code.</span></span>  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="6272e-121">Compile e assinar friend_signed_B usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="6272e-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="6272e-122">O nome do assembly gerado pelo compilador deve corresponder o nome do assembly autorizado passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="6272e-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="6272e-123">Você pode definir explicitamente o assembly usando o `/out` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="6272e-123">You can explicitly set the assembly by using the `/out` compiler option.</span></span> <span data-ttu-id="6272e-124">Para obter mais informações, consulte [entrada/saída (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="6272e-124">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7.  <span data-ttu-id="6272e-125">Execute o arquivo friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="6272e-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="6272e-126">O programa imprime a cadeia de caracteres "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="6272e-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6272e-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6272e-127">.NET Framework Security</span></span>  
 <span data-ttu-id="6272e-128">Há semelhanças entre o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo e a <xref:System.Security.Permissions.StrongNameIdentityPermission>classe.</xref:System.Security.Permissions.StrongNameIdentityPermission> </xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="6272e-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="6272e-129">A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission>pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo controla a visibilidade de `Friend` tipos e membros.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="6272e-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6272e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6272e-130">See Also</span></span>  
 <span data-ttu-id="6272e-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="6272e-131"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
<span data-ttu-id="6272e-132"> [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="6272e-132"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="6272e-133"> [Assemblies amigáveis (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="6272e-133"> [Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md) </span></span>  
<span data-ttu-id="6272e-134"> [Como: Criar Assemblies amigáveis não assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="6272e-134"> [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="6272e-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="6272e-135"> [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="6272e-136"> [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="6272e-136"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="6272e-137"> [Criando e usando Assemblies de nome forte](https://msdn.microsoft.com/library/xwb8f617) </span><span class="sxs-lookup"><span data-stu-id="6272e-137"> [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) </span></span>  
<span data-ttu-id="6272e-138"> [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="6272e-138"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
