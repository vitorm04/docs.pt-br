---
title: Como criar assemblies Friend assinados
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 3bf71adc694f3c6e072990717198b4f2003cd503
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523891"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="ec83b-102">Como criar assemblies Friend assinados</span><span class="sxs-lookup"><span data-stu-id="ec83b-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="ec83b-103">Este exemplo mostra como usar assemblies amigáveis com assemblies que têm nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="ec83b-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="ec83b-104">Os dois assemblies devem ter nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="ec83b-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="ec83b-105">Embora os dois assemblies neste exemplo usem as mesmas chaves, você pode usar chaves diferentes para dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="ec83b-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="ec83b-106">Criar um assembly assinado e um assembly Friend</span><span class="sxs-lookup"><span data-stu-id="ec83b-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="ec83b-107">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ec83b-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="ec83b-108">Use a seguinte sequência de comandos com a ferramenta Nome Forte para gerar um keyfile e exibir sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="ec83b-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="ec83b-109">Para obter mais informações, consulte [sn. exe (Strong Name Tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ec83b-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="ec83b-110">Gere uma chave de nome forte para este exemplo e armazene-a no arquivo *FriendAssemblies. SNK*:</span><span class="sxs-lookup"><span data-stu-id="ec83b-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="ec83b-111">Extraia a chave pública de *FriendAssemblies. SNK* e coloque-a em *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="ec83b-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="ec83b-112">Exiba a chave pública armazenada no arquivo *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="ec83b-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="ec83b-113">Crie um C# arquivo ou Visual Basic chamado *friend_signed_A* que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec83b-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="ec83b-114">O código usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar *friend_signed_B* como um assembly Friend.</span><span class="sxs-lookup"><span data-stu-id="ec83b-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  
   
   <span data-ttu-id="ec83b-115">A ferramenta Nome Forte gera uma nova chave pública sempre que for executada.</span><span class="sxs-lookup"><span data-stu-id="ec83b-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="ec83b-116">Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec83b-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
   
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
   
4. <span data-ttu-id="ec83b-117">Compile e assine o *friend_signed_A* usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec83b-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. <span data-ttu-id="ec83b-118">Crie um C# arquivo ou Visual Basic chamado *friend_signed_B* que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec83b-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="ec83b-119">Como *friend_signed_A* especifica *friend_signed_B* como um assembly Friend, o código em *friend_signed_B* pode acessar tipos `internal`C#() ou `Friend` (Visual Basic) e membros de *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="ec83b-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="ec83b-120">O arquivo contém o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="ec83b-120">The file contains the following code.</span></span>  
   
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
   
6. <span data-ttu-id="ec83b-121">Compile e assine o *friend_signed_B* usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec83b-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   <span data-ttu-id="ec83b-122">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ec83b-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="ec83b-123">Você deve especificar explicitamente o nome do assembly de saída ( *. exe* ou *. dll*) usando a opção de compilador `/out`.</span><span class="sxs-lookup"><span data-stu-id="ec83b-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="ec83b-124">Para obter mais informações, consulte [/outC# (opções do compilador)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="ec83b-124">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
   
7. <span data-ttu-id="ec83b-125">Execute o arquivo *friend_signed_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="ec83b-125">Run the *friend_signed_B.exe* file.</span></span>  
   
   <span data-ttu-id="ec83b-126">O programa gera a cadeia de caracteres **Class1. Test**.</span><span class="sxs-lookup"><span data-stu-id="ec83b-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="ec83b-127">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="ec83b-127">.NET security</span></span>  
 <span data-ttu-id="ec83b-128">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="ec83b-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="ec83b-129">A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode exigir permissões de segurança para executar uma determinada seção de código, enquanto o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla a visibilidade dos membrosC#e tipos `internal` () ou `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ec83b-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec83b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec83b-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="ec83b-131">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="ec83b-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="ec83b-132">Assemblies Friend</span><span class="sxs-lookup"><span data-stu-id="ec83b-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="ec83b-133">Como: criar assemblies Friend não assinados</span><span class="sxs-lookup"><span data-stu-id="ec83b-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="ec83b-134">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="ec83b-134">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="ec83b-135">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec83b-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="ec83b-136">Sn. exe (ferramenta Strong Name)</span><span class="sxs-lookup"><span data-stu-id="ec83b-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="ec83b-137">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="ec83b-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="ec83b-138">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="ec83b-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ec83b-139">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec83b-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
