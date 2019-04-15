---
title: Criando uma classe para conter funções de DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 399ad6649016e53d91d5d9d30ecc031ae8a97a4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149351"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="afea5-102">Criando uma classe para conter funções de DLL</span><span class="sxs-lookup"><span data-stu-id="afea5-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="afea5-103">O encapsulamento de uma função de DLL frequentemente usada em uma classe gerenciada é uma abordagem eficiente para encapsular a funcionalidade da plataforma.</span><span class="sxs-lookup"><span data-stu-id="afea5-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="afea5-104">Embora não seja obrigatório fazer isso em todos os casos, o fornecimento de um wrapper de classe é conveniente, pois a definição de funções de DLL pode ser inconveniente e propensa a erros.</span><span class="sxs-lookup"><span data-stu-id="afea5-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="afea5-105">Se você estiver programando no Visual Basic ou no C#, declare as funções de DLL em uma classe ou um módulo do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="afea5-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="afea5-106">Em uma classe, defina um método estático para cada função de DLL que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="afea5-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="afea5-107">A definição pode incluir informações adicionais, como o conjunto de caracteres ou a convenção de chamada usados para passar argumentos de método; ao omitir essas informações, selecione as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="afea5-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="afea5-108">Para obter uma lista completa de opções de declaração e suas configurações padrão, consulte [Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="afea5-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="afea5-109">Depois de encapsular, você poderá chamar os métodos na classe da mesma forma em que chama métodos estáticos em qualquer outra classe.</span><span class="sxs-lookup"><span data-stu-id="afea5-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="afea5-110">A invocação de plataforma manipula a função exportada subjacente automaticamente.</span><span class="sxs-lookup"><span data-stu-id="afea5-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="afea5-111">Ao criar uma classe gerenciada para a invocação de plataforma, considere as relações entre as classes e as funções de DLL.</span><span class="sxs-lookup"><span data-stu-id="afea5-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="afea5-112">Por exemplo, você pode:</span><span class="sxs-lookup"><span data-stu-id="afea5-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="afea5-113">Declare as funções de DLL em uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="afea5-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="afea5-114">Crie uma classe individual para cada função de DLL, mantendo as funções isoladas e fáceis de serem localizadas.</span><span class="sxs-lookup"><span data-stu-id="afea5-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="afea5-115">Crie uma classe para um conjunto de funções de DLL relacionadas para formar agrupamentos lógicos e reduzir a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="afea5-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="afea5-116">Nomeie a classe e seus métodos conforme desejar.</span><span class="sxs-lookup"><span data-stu-id="afea5-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="afea5-117">Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="afea5-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afea5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afea5-118">See also</span></span>

- [<span data-ttu-id="afea5-119">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="afea5-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="afea5-120">Identificando funções em DLLs</span><span class="sxs-lookup"><span data-stu-id="afea5-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [<span data-ttu-id="afea5-121">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="afea5-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="afea5-122">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="afea5-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
