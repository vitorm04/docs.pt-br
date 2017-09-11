---
title: "Criando uma classe para conter funções de DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: abf5c47e843801d47bb2d47c8686db7f81f42698
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="f2566-102">Criando uma classe para conter funções de DLL</span><span class="sxs-lookup"><span data-stu-id="f2566-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="f2566-103">O encapsulamento de uma função de DLL frequentemente usada em uma classe gerenciada é uma abordagem eficiente para encapsular a funcionalidade da plataforma.</span><span class="sxs-lookup"><span data-stu-id="f2566-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="f2566-104">Embora não seja obrigatório fazer isso em todos os casos, o fornecimento de um wrapper de classe é conveniente, pois a definição de funções de DLL pode ser inconveniente e propensa a erros.</span><span class="sxs-lookup"><span data-stu-id="f2566-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="f2566-105">Se você estiver programando no Visual Basic ou no C#, declare as funções de DLL em uma classe ou um módulo do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f2566-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="f2566-106">Em uma classe, defina um método estático para cada função de DLL que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="f2566-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="f2566-107">A definição pode incluir informações adicionais, como o conjunto de caracteres ou a convenção de chamada usados para passar argumentos de método; ao omitir essas informações, selecione as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="f2566-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="f2566-108">Para obter uma lista completa de opções de declaração e suas configurações padrão, consulte [Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="f2566-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="f2566-109">Depois do encapsulamento, você pode chamar métodos na função da mesma forma como chama métodos em qualquer outra função estática.</span><span class="sxs-lookup"><span data-stu-id="f2566-109">Once wrapped, you can call methods on the function as you call methods on any other static function.</span></span> <span data-ttu-id="f2566-110">A invocação de plataforma manipula a função exportada subjacente automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f2566-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="f2566-111">Ao criar uma classe gerenciada para a invocação de plataforma, considere as relações entre as classes e as funções de DLL.</span><span class="sxs-lookup"><span data-stu-id="f2566-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="f2566-112">Por exemplo, você pode:</span><span class="sxs-lookup"><span data-stu-id="f2566-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="f2566-113">Declare as funções de DLL em uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="f2566-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="f2566-114">Crie uma classe individual para cada função de DLL, mantendo as funções isoladas e fáceis de serem localizadas.</span><span class="sxs-lookup"><span data-stu-id="f2566-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="f2566-115">Crie uma classe para um conjunto de funções de DLL relacionadas para formar agrupamentos lógicos e reduzir a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="f2566-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="f2566-116">Nomeie a classe e seus métodos conforme desejar.</span><span class="sxs-lookup"><span data-stu-id="f2566-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="f2566-117">Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="f2566-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2566-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2566-118">See Also</span></span>  
 <span data-ttu-id="f2566-119">[Consumindo funções de DLL não gerenciadas](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md) </span><span class="sxs-lookup"><span data-stu-id="f2566-119">[Consuming Unmanaged DLL Functions](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md) </span></span>  
 <span data-ttu-id="f2566-120">[Identificando funções em DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md) </span><span class="sxs-lookup"><span data-stu-id="f2566-120">[Identifying Functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md) </span></span>  
 <span data-ttu-id="f2566-121">[Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md) </span><span class="sxs-lookup"><span data-stu-id="f2566-121">[Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md) </span></span>  
 [<span data-ttu-id="f2566-122">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="f2566-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)

