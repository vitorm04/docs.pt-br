---
title: Encaminhamento de tipo no Common Language Runtime
description: O encaminhamento de tipo permite que você mova um tipo para outro assembly .NET sem precisar recompilar os aplicativos que usam o assembly original.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687667"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="7755a-103">Encaminhamento de tipo no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="7755a-103">Type forwarding in the common language runtime</span></span>

<span data-ttu-id="7755a-104">O encaminhamento de tipo permite que você mova um tipo para outro assembly sem ter que recompilar os aplicativos que usam o assembly original.</span><span class="sxs-lookup"><span data-stu-id="7755a-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="7755a-105">Por exemplo, suponha que um aplicativo use a `Example` classe em um assembly chamado *Utility.dll* .</span><span class="sxs-lookup"><span data-stu-id="7755a-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll* .</span></span> <span data-ttu-id="7755a-106">Os desenvolvedores de *Utility.dll* podem decidir refatorar o assembly e, no processo, eles podem mover a `Example` classe para outro assembly.</span><span class="sxs-lookup"><span data-stu-id="7755a-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="7755a-107">Se a versão antiga do *Utility.dll* for substituída pela nova versão do *Utility.dll* e seu assembly complementar, o aplicativo que usa a `Example` classe falhará porque não consegue localizar a `Example` classe na nova versão do *Utility.dll* .</span><span class="sxs-lookup"><span data-stu-id="7755a-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll* .</span></span>  
  
 <span data-ttu-id="7755a-108">Os desenvolvedores de *Utility.dll* podem evitar isso Encaminhando solicitações para a `Example` classe, usando o <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="7755a-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="7755a-109">Se o atributo tiver sido aplicado à nova versão do *Utility.dll* , as solicitações para a `Example` classe serão encaminhadas para o assembly que agora contém a classe.</span><span class="sxs-lookup"><span data-stu-id="7755a-109">If the attribute has been applied to the new version of *Utility.dll* , requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="7755a-110">O aplicativo existente continua a funcionar normalmente, sem recompilação.</span><span class="sxs-lookup"><span data-stu-id="7755a-110">The existing application continues to function normally, without recompilation.</span></span>

## <a name="forward-a-type"></a><span data-ttu-id="7755a-111">Encaminhar um tipo</span><span class="sxs-lookup"><span data-stu-id="7755a-111">Forward a type</span></span>

 <span data-ttu-id="7755a-112">Há quatro etapas para encaminhar um tipo:</span><span class="sxs-lookup"><span data-stu-id="7755a-112">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="7755a-113">Mova o código-fonte para o tipo do assembly original para o conjunto de destino.</span><span class="sxs-lookup"><span data-stu-id="7755a-113">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="7755a-114">No assembly em que o tipo é usado para ser localizado, adicione um <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para o tipo que foi movido.</span><span class="sxs-lookup"><span data-stu-id="7755a-114">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="7755a-115">O código a seguir mostra o atributo para um tipo chamado `Example` que foi movido.</span><span class="sxs-lookup"><span data-stu-id="7755a-115">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="7755a-116">Compile o assembly que agora contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="7755a-116">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="7755a-117">Recompile o assembly onde o tipo estava localizado, com uma referência ao assembly que agora contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="7755a-117">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="7755a-118">Por exemplo, se você estiver Compilando um arquivo C# na linha de comando, use a opção [-Reference (opções do compilador C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) para especificar o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="7755a-118">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="7755a-119">Em C++, use a diretiva [#using](/cpp/preprocessor/hash-using-directive-cpp) no arquivo de origem para especificar o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="7755a-119">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7755a-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="7755a-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="7755a-121">Encaminhamento de tipo (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="7755a-121">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="7755a-122">#using diretiva</span><span class="sxs-lookup"><span data-stu-id="7755a-122">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
