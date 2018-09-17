---
title: Encaminhamento de tipo no Common Language Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d25bac953ff68422a1dddc54bdb01b4b4f241cbb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664521"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="96cd2-102">Encaminhamento de tipo no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="96cd2-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="96cd2-103">O encaminhamento de tipo permite que você mova um tipo para outro assembly sem ter que recompilar os aplicativos que usam o assembly original.</span><span class="sxs-lookup"><span data-stu-id="96cd2-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="96cd2-104">Por exemplo, suponha que um aplicativo use a classe `Example` em um assembly chamado `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="96cd2-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="96cd2-105">Os desenvolvedores de `Utility.dll` podem decidir refatorar o assembly e, durante o processo, podem mover a classe `Example` para outro conjunto.</span><span class="sxs-lookup"><span data-stu-id="96cd2-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="96cd2-106">Se a versão antiga do `Utility.dll` for substituída pela nova versão do `Utility.dll` e por seu assembly complementar, o aplicativo que usa a classe `Example` falhará porque não foi possível localizar a classe `Example` na nova versão do `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="96cd2-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="96cd2-107">Os desenvolvedores de `Utility.dll` pode evitar isso encaminhando solicitações para a classe `Example`, usando o atributo <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="96cd2-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="96cd2-108">Se o atributo tiver sido aplicado à nova versão do `Utility.dll`, as solicitações para a classe `Example` são encaminhadas ao assembly que agora contém a classe.</span><span class="sxs-lookup"><span data-stu-id="96cd2-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="96cd2-109">O aplicativo existente continua a funcionar normalmente, sem recompilação.</span><span class="sxs-lookup"><span data-stu-id="96cd2-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96cd2-110">No .NET Framework versão 2.0, você não pode encaminhar os tipos de assemblies escritos em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="96cd2-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="96cd2-111">No entanto, um aplicativo escrito em Visual Basic pode consumir tipos encaminhados.</span><span class="sxs-lookup"><span data-stu-id="96cd2-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="96cd2-112">Ou seja, se o aplicativo usar um assembly de código em C# ou C++, e um tipo desse assembly for encaminhado para outro assembly, o aplicativo em Visual Basic poderá usar o tipo encaminhado.</span><span class="sxs-lookup"><span data-stu-id="96cd2-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="96cd2-113">Encaminhamento de tipos</span><span class="sxs-lookup"><span data-stu-id="96cd2-113">Forwarding Types</span></span>  
 <span data-ttu-id="96cd2-114">Há quatro etapas para encaminhar um tipo:</span><span class="sxs-lookup"><span data-stu-id="96cd2-114">There are four steps to forwarding a type:</span></span>  
  
1.  <span data-ttu-id="96cd2-115">Mova o código-fonte para o tipo do assembly original para o conjunto de destino.</span><span class="sxs-lookup"><span data-stu-id="96cd2-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2.  <span data-ttu-id="96cd2-116">No assembly em que o tipo é usado para ser localizado, adicione um <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para o tipo que foi movido.</span><span class="sxs-lookup"><span data-stu-id="96cd2-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="96cd2-117">O código a seguir mostra o atributo para um tipo chamado `Example` que foi movido.</span><span class="sxs-lookup"><span data-stu-id="96cd2-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  <span data-ttu-id="96cd2-118">Compile o assembly que agora contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="96cd2-118">Compile the assembly that now contains the type.</span></span>  
  
4.  <span data-ttu-id="96cd2-119">Recompile o assembly onde o tipo estava localizado, com uma referência ao assembly que agora contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="96cd2-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="96cd2-120">Por exemplo, se você estiver compilando um arquivo em C# na linha de comando, use a opção [/reference (opções do compilador em C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) para especificar o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="96cd2-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="96cd2-121">Em C++, use a diretiva [#using](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) no arquivo de origem para especificar o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="96cd2-121">In C++, use the [#using](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96cd2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96cd2-122">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [<span data-ttu-id="96cd2-123">Encaminhamento de tipo (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="96cd2-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)  
 [<span data-ttu-id="96cd2-124">Diretiva #using</span><span class="sxs-lookup"><span data-stu-id="96cd2-124">#using Directive</span></span>](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
