---
title: 'Como: Criar assemblies amigáveis com sinal (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 13b99cd1118071e7c403828260003c80b9417792
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354486"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="6f439-102">Como: Criar assemblies amigáveis com sinal (C#)</span><span class="sxs-lookup"><span data-stu-id="6f439-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="6f439-103">Este exemplo mostra como usar assemblies amigáveis com assemblies que têm nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="6f439-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="6f439-104">Os dois assemblies devem ter nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="6f439-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="6f439-105">Embora os dois assemblies neste exemplo usem as mesmas chaves, você pode usar chaves diferentes para dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="6f439-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="6f439-106">Para criar um assembly assinado e um assembly amigável</span><span class="sxs-lookup"><span data-stu-id="6f439-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="6f439-107">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="6f439-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="6f439-108">Use a seguinte sequência de comandos com a ferramenta Nome Forte para gerar um keyfile e exibir sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="6f439-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="6f439-109">Para saber mais, veja [Sn.exe (Ferramenta de Nome Forte)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6f439-109">For more information, see [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1.  <span data-ttu-id="6f439-110">Gere uma chave de nome forte para este exemplo e armazene-a no arquivo FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="6f439-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="6f439-111">Extraia a chave pública de FriendAssemblies.snk e coloque-a no FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="6f439-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="6f439-112">Exiba a chave pública armazenada no arquivo FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="6f439-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="6f439-113">Crie um arquivo do C# chamado `friend_signed_A` que contenha o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="6f439-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="6f439-114">O código usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar friend_signed_B como um assembly autorizado.</span><span class="sxs-lookup"><span data-stu-id="6f439-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="6f439-115">A ferramenta Nome Forte gera uma nova chave pública sempre que for executada.</span><span class="sxs-lookup"><span data-stu-id="6f439-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="6f439-116">Portanto, você deve substituir a chave pública no código a seguir com a chave pública que você acabou de gerar, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f439-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="6f439-117">Compile e assine o friend_signed_A usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="6f439-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="6f439-118">Crie um arquivo do C# chamado `friend_signed_B` e que contenha o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f439-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="6f439-119">Como o friend_signed_A especifica o friend_signed_B como um assembly amigável, o código em friend_signed_B pode acessar tipos `internal` e membros do friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="6f439-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="6f439-120">O arquivo contém o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="6f439-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="6f439-121">Compile e assine o friend_signed_B, usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="6f439-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="6f439-122">O nome do assembly gerado pelo compilador deve corresponder ao nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6f439-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="6f439-123">Você deve especificar explicitamente o nome do assembly de saída (.exe ou .dll) usando a opção do compilador `/out`.</span><span class="sxs-lookup"><span data-stu-id="6f439-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="6f439-124">Para obter mais informações, consulte [/out (opções do compilador C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="6f439-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="6f439-125">Execute o arquivo friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="6f439-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="6f439-126">O programa imprime a cadeia de caracteres "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="6f439-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6f439-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f439-127">.NET Framework Security</span></span>  
 <span data-ttu-id="6f439-128">Há semelhanças entre o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e a classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="6f439-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="6f439-129">A principal diferença é que <xref:System.Security.Permissions.StrongNameIdentityPermission> pode solicitar permissões de segurança para executar uma determinada seção de código, enquanto o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla a visibilidade de membros e tipos de `internal`.</span><span class="sxs-lookup"><span data-stu-id="6f439-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f439-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f439-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="6f439-131">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="6f439-131">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="6f439-132">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="6f439-132">Friend Assemblies</span></span>](../../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="6f439-133">Como: Criar assemblies amigáveis sem sinal (C#)</span><span class="sxs-lookup"><span data-stu-id="6f439-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="6f439-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="6f439-134">/keyfile</span></span>](../../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="6f439-135">Sn.exe (Ferramenta Nome Forte)</span><span class="sxs-lookup"><span data-stu-id="6f439-135">Sn.exe (Strong Name Tool)</span></span>](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="6f439-136">Criar e usar assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="6f439-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="6f439-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6f439-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
