---
title: Como referenciar um assembly de nome forte
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 427550e1fbeb38cefbb4afe97d80e198ac2d6cb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127640"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="d8413-102">Como referenciar um assembly de nome forte</span><span class="sxs-lookup"><span data-stu-id="d8413-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="d8413-103">O processo para referenciar tipos ou recursos em um assembly de nome forte é normalmente transparente.</span><span class="sxs-lookup"><span data-stu-id="d8413-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="d8413-104">Você pode fazer a referência no tempo de compilação (vinculação inicial) ou no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d8413-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="d8413-105">Uma referência de tempo de compilação ocorre quando você indica ao compilador que o assembly a ser compilado explicitamente referencia outro assembly.</span><span class="sxs-lookup"><span data-stu-id="d8413-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="d8413-106">Quando você usa a referência no tempo de compilação, o compilador obtém automaticamente a chave pública do assembly com nome forte direcionado e o coloca na referência de assembly do assembly que está sendo compilado.</span><span class="sxs-lookup"><span data-stu-id="d8413-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d8413-107">Assembly de nome forte só pode usar tipos de outros assemblies de nome forte.</span><span class="sxs-lookup"><span data-stu-id="d8413-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="d8413-108">Caso contrário, a segurança do assembly de nome forte estaria comprometida.</span><span class="sxs-lookup"><span data-stu-id="d8413-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="d8413-109">Fazer uma referência de tempo de compilação a um assembly de nome forte</span><span class="sxs-lookup"><span data-stu-id="d8413-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="d8413-110">Em um prompt de comando, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d8413-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="d8413-111">\<*comando do compilador*>  **/reference:** \<*nome do assembly*></span><span class="sxs-lookup"><span data-stu-id="d8413-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="d8413-112">Nesse comando, o *comando do compilador* é o comando do compilador para a linguagem que você está usando, e *nome do assembly* é o nome do assembly de nome forte que está sendo referenciado.</span><span class="sxs-lookup"><span data-stu-id="d8413-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="d8413-113">Você também pode usar outras opções de compilador, como a opção **/t:library** para criar um assembly de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d8413-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="d8413-114">O exemplo a seguir cria um assembly chamado *myAssembly. dll* que faz referência a um assembly de nome forte chamado *myLibAssembly. dll* de um módulo de código chamado *myAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="d8413-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="d8413-115">Fazer uma referência de tempo de execução para um assembly de nome forte</span><span class="sxs-lookup"><span data-stu-id="d8413-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="d8413-116">Quando você faz uma referência de tempo de execução para um assembly de nome forte, por exemplo, usando o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>, você deve usar o nome de exibição do assembly de nome forte referenciado.</span><span class="sxs-lookup"><span data-stu-id="d8413-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="d8413-117">A sintaxe de um nome de exibição é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8413-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="d8413-118">\<*nome do assembly*> **,** \<*número da versão*> **,** \<*cultura*> **,** \<*token de chave pública*></span><span class="sxs-lookup"><span data-stu-id="d8413-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="d8413-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d8413-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
```  

<span data-ttu-id="d8413-120">Neste exemplo, `PublicKeyToken` é a forma hexadecimal do token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="d8413-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="d8413-121">Se não houver valor de cultura, use `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="d8413-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="d8413-122">O exemplo de código a seguir mostra como usar essas informações com o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8413-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="d8413-123">Você pode imprimir o formato hexadecimal da chave pública e do token de chave pública para um assembly específico usando o seguinte comando [Nome Forte (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md):</span><span class="sxs-lookup"><span data-stu-id="d8413-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="d8413-124">**sn -Tp \<** *assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="d8413-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="d8413-125">Se você tiver um arquivo de chave pública, use o comando a seguir (observe a diferença no caso da opção de linha de comando):</span><span class="sxs-lookup"><span data-stu-id="d8413-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="d8413-126">**sn -tp \<** *arquivo de chave pública* **>**</span><span class="sxs-lookup"><span data-stu-id="d8413-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="d8413-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8413-127">See also</span></span>

- [<span data-ttu-id="d8413-128">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="d8413-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
