---
title: Como referenciar um assembly de nome forte
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f78fff50d1a227061076790ad77f17debe3f690
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="06ab3-102">Como referenciar um assembly de nome forte</span><span class="sxs-lookup"><span data-stu-id="06ab3-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="06ab3-103">O processo para referenciar tipos ou recursos em um assembly de nome forte é normalmente transparente.</span><span class="sxs-lookup"><span data-stu-id="06ab3-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="06ab3-104">Você pode fazer a referência no tempo de compilação (vinculação inicial) ou no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="06ab3-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="06ab3-105">Uma referência de tempo de compilação ocorre quando você indica para o compilador que seu assembly faz referência explícita a outro assembly.</span><span class="sxs-lookup"><span data-stu-id="06ab3-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="06ab3-106">Quando você usa a referência no tempo de compilação, o compilador obtém automaticamente a chave pública do assembly com nome forte direcionado e o coloca na referência de assembly do assembly que está sendo compilado.</span><span class="sxs-lookup"><span data-stu-id="06ab3-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06ab3-107">Assembly de nome forte só pode usar tipos de outros assemblies de nome forte.</span><span class="sxs-lookup"><span data-stu-id="06ab3-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="06ab3-108">Caso contrário, a segurança do assembly de nome forte estaria comprometida.</span><span class="sxs-lookup"><span data-stu-id="06ab3-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="06ab3-109">Para fazer uma referência no tempo de compilação a um assembly de nome forte</span><span class="sxs-lookup"><span data-stu-id="06ab3-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="06ab3-110">No prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="06ab3-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="06ab3-111">\<*comando do compilador*> **/reference:**\<*nome do assembly*></span><span class="sxs-lookup"><span data-stu-id="06ab3-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="06ab3-112">Nesse comando, o *comando do compilador* é o comando do compilador para a linguagem que você está usando, e *nome do assembly* é o nome do assembly de nome forte que está sendo referenciado.</span><span class="sxs-lookup"><span data-stu-id="06ab3-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="06ab3-113">Você também pode usar outras opções de compilador, como a opção **/t:library** para criar um assembly de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="06ab3-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="06ab3-114">O exemplo a seguir cria um assembly chamado `myAssembly.dll` que faz referência a um assembly de nome forte chamado `myLibAssembly.dll` de um módulo de código chamado `myAssembly.cs`.</span><span class="sxs-lookup"><span data-stu-id="06ab3-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="06ab3-115">Para fazer uma referência no tempo de execução a um assembly de nome forte</span><span class="sxs-lookup"><span data-stu-id="06ab3-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="06ab3-116">Quando você faz uma referência de tempo de execução a um assembly de nome forte (por exemplo, usando o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> ou o <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>), você deve usar o nome de exibição do assembly de nome forte referenciado.</span><span class="sxs-lookup"><span data-stu-id="06ab3-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="06ab3-117">A sintaxe de um nome de exibição é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="06ab3-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="06ab3-118">\<*nome do assembly*>**,** \<*número da versão*>**,** \<*cultura*>**,** \<*token de chave pública*></span><span class="sxs-lookup"><span data-stu-id="06ab3-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="06ab3-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="06ab3-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="06ab3-120">Neste exemplo, `PublicKeyToken` é a forma hexadecimal do token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="06ab3-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="06ab3-121">Se não houver valor de cultura, use `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="06ab3-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="06ab3-122">O exemplo de código a seguir mostra como usar essas informações com o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06ab3-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="06ab3-123">Você pode imprimir o formato hexadecimal da chave pública e do token de chave pública para um assembly específico usando o seguinte comando [Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md):</span><span class="sxs-lookup"><span data-stu-id="06ab3-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="06ab3-124">**sn -Tp \<** *assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="06ab3-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="06ab3-125">Se você tiver um arquivo de chave pública, use o comando a seguir (observe a diferença no caso da opção de linha de comando):</span><span class="sxs-lookup"><span data-stu-id="06ab3-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="06ab3-126">**sn -tp \<** *assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="06ab3-126">**sn -tp \<** *assembly* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ab3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06ab3-127">See Also</span></span>  
 [<span data-ttu-id="06ab3-128">Criar e usar assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="06ab3-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
