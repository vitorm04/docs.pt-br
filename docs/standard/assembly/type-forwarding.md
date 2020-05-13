---
title: Encaminhamento de tipo no Common Language Runtime
description: O encaminhamento de tipo permite que você mova um tipo para outro assembly .NET sem precisar recompilar os aplicativos que usam o assembly original.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f0be61bd4ce88569e22a350a9ea9490d67e74ff3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378591"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="eefbc-103">Encaminhamento de tipo no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="eefbc-103">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="eefbc-104">O encaminhamento de tipo permite que você mova um tipo para outro assembly sem ter que recompilar os aplicativos que usam o assembly original.</span><span class="sxs-lookup"><span data-stu-id="eefbc-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="eefbc-105">Por exemplo, suponha que um aplicativo use a `Example` classe em um assembly chamado *Utility. dll*.</span><span class="sxs-lookup"><span data-stu-id="eefbc-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="eefbc-106">Os desenvolvedores de *Utility. dll* podem decidir refatorar o assembly e, no processo, eles podem mover a `Example` classe para outro assembly.</span><span class="sxs-lookup"><span data-stu-id="eefbc-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="eefbc-107">Se a versão antiga do *Utility. dll* for substituída pela nova versão do *Utility. dll* e seu assembly complementar, o aplicativo que usa a `Example` classe falhará porque ele não pode localizar a `Example` classe na nova versão do *Utility. dll*.</span><span class="sxs-lookup"><span data-stu-id="eefbc-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="eefbc-108">Os desenvolvedores de *Utility. dll* podem evitar isso Encaminhando solicitações para a `Example` classe, usando o <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="eefbc-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="eefbc-109">Se o atributo tiver sido aplicado à nova versão do *Utility. dll*, as solicitações para a `Example` classe serão encaminhadas para o assembly que agora contém a classe.</span><span class="sxs-lookup"><span data-stu-id="eefbc-109">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="eefbc-110">O aplicativo existente continua a funcionar normalmente, sem recompilação.</span><span class="sxs-lookup"><span data-stu-id="eefbc-110">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eefbc-111">No .NET Framework versão 2.0, você não pode encaminhar os tipos de assemblies escritos em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eefbc-111">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="eefbc-112">No entanto, um aplicativo escrito em Visual Basic pode consumir tipos encaminhados.</span><span class="sxs-lookup"><span data-stu-id="eefbc-112">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="eefbc-113">Ou seja, se o aplicativo usar um assembly de código em C# ou C++, e um tipo desse assembly for encaminhado para outro assembly, o aplicativo em Visual Basic poderá usar o tipo encaminhado.</span><span class="sxs-lookup"><span data-stu-id="eefbc-113">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="eefbc-114">Tipos de encaminhamento</span><span class="sxs-lookup"><span data-stu-id="eefbc-114">Forward types</span></span>  
 <span data-ttu-id="eefbc-115">Há quatro etapas para encaminhar um tipo:</span><span class="sxs-lookup"><span data-stu-id="eefbc-115">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="eefbc-116">Mova o código-fonte para o tipo do assembly original para o conjunto de destino.</span><span class="sxs-lookup"><span data-stu-id="eefbc-116">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="eefbc-117">No assembly em que o tipo é usado para ser localizado, adicione um <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para o tipo que foi movido.</span><span class="sxs-lookup"><span data-stu-id="eefbc-117">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="eefbc-118">O código a seguir mostra o atributo para um tipo chamado `Example` que foi movido.</span><span class="sxs-lookup"><span data-stu-id="eefbc-118">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="eefbc-119">Compile o assembly que agora contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="eefbc-119">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="eefbc-120">Recompile o assembly onde o tipo estava localizado, com uma referência ao assembly que agora contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="eefbc-120">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="eefbc-121">Por exemplo, se você estiver Compilando um arquivo C# na linha de comando, use a opção [-Reference (opções do compilador C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) para especificar o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="eefbc-121">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="eefbc-122">Em C++, use a diretiva [#using](/cpp/preprocessor/hash-using-directive-cpp) no arquivo de origem para especificar o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="eefbc-122">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eefbc-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="eefbc-123">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="eefbc-124">Encaminhamento de tipo (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="eefbc-124">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="eefbc-125">#using diretiva</span><span class="sxs-lookup"><span data-stu-id="eefbc-125">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
