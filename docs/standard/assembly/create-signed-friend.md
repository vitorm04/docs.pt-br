---
title: 'Como: Criar assembléias de amigos assinados'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159488"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="607e3-102">Como: Criar assembléias de amigos assinados</span><span class="sxs-lookup"><span data-stu-id="607e3-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="607e3-103">Este exemplo mostra como usar assemblies amigáveis com assemblies que têm nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="607e3-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="607e3-104">Os dois assemblies devem ter nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="607e3-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="607e3-105">Embora os dois assemblies neste exemplo usem as mesmas chaves, você pode usar chaves diferentes para dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="607e3-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="607e3-106">Crie uma assembléia assinada e uma reunião de amigos</span><span class="sxs-lookup"><span data-stu-id="607e3-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="607e3-107">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="607e3-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="607e3-108">Use a seguinte sequência de comandos com a ferramenta Nome Forte para gerar um keyfile e exibir sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="607e3-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="607e3-109">Para obter mais informações, consulte [Sn.exe (ferramenta Nome Forte)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="607e3-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="607e3-110">Gerar uma chave de nome forte para este exemplo e armazená-la no arquivo *FriendAssemblies.snk*:</span><span class="sxs-lookup"><span data-stu-id="607e3-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="607e3-111">Extrair a chave pública de *FriendAssemblies.snk* e colocá-la em *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="607e3-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="607e3-112">Exibir a chave pública armazenada no arquivo *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="607e3-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="607e3-113">Crie um arquivo C# ou Visual Basic chamado *friend_signed_A* que contenha o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="607e3-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="607e3-114">O código <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> usa o atributo para declarar *friend_signed_B* como uma assembléia de amigos.</span><span class="sxs-lookup"><span data-stu-id="607e3-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="607e3-115">A ferramenta Nome Forte gera uma nova chave pública sempre que for executada.</span><span class="sxs-lookup"><span data-stu-id="607e3-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="607e3-116">Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="607e3-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="607e3-117">Compire e assine *friend_signed_A* usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="607e3-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="607e3-118">Crie um arquivo C# ou Visual Basic chamado *friend_signed_B* que contenha o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="607e3-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="607e3-119">Como *friend_signed_A* especifica *friend_signed_B* como uma reunião de amigos, o código em *friend_signed_B* pode `internal` acessar (C#) ou `Friend` (Visual Basic) tipos e membros de *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="607e3-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="607e3-120">O arquivo contém o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="607e3-120">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="607e3-121">Compire e assine *friend_signed_B* usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="607e3-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="607e3-122">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="607e3-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="607e3-123">Você deve especificar explicitamente o nome do conjunto de saída ( `-out` *.exe* ou *.dll*) usando a opção compilador.</span><span class="sxs-lookup"><span data-stu-id="607e3-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="607e3-124">Para obter mais informações, consulte [-out (opções de compilador C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="607e3-124">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="607e3-125">Execute o arquivo *friend_signed_B.exe.*</span><span class="sxs-lookup"><span data-stu-id="607e3-125">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="607e3-126">O programa produz a string **Class1.Test**.</span><span class="sxs-lookup"><span data-stu-id="607e3-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="607e3-127">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="607e3-127">.NET security</span></span>  
 <span data-ttu-id="607e3-128">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="607e3-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="607e3-129">A principal diferença <xref:System.Security.Permissions.StrongNameIdentityPermission> é que pode exigir permissões de segurança <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para executar uma determinada `internal` seção de `Friend` código, enquanto o atributo controla a visibilidade dos tipos e membros (C#) ou (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="607e3-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607e3-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="607e3-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="607e3-131">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="607e3-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="607e3-132">Assemblies amigáveis</span><span class="sxs-lookup"><span data-stu-id="607e3-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="607e3-133">Como: Criar assembléias de amigos não assinados</span><span class="sxs-lookup"><span data-stu-id="607e3-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="607e3-134">-arquivo de tecla (C#)</span><span class="sxs-lookup"><span data-stu-id="607e3-134">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="607e3-135">-arquivo-chave (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="607e3-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="607e3-136">Sn.exe (ferramenta Nome Forte)</span><span class="sxs-lookup"><span data-stu-id="607e3-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="607e3-137">Criar e usar assemblies com nome forte</span><span class="sxs-lookup"><span data-stu-id="607e3-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="607e3-138">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="607e3-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="607e3-139">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="607e3-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
