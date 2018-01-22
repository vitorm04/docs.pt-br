---
title: Wrappers COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b899ed162fa626f8c378923907f275cebf9a7db4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="com-wrappers"></a><span data-ttu-id="9d593-102">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="9d593-102">COM Wrappers</span></span>
<span data-ttu-id="9d593-103">O COM difere do modelo de objeto .NET Framework de várias maneiras importantes:</span><span class="sxs-lookup"><span data-stu-id="9d593-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="9d593-104">Os clientes de objetos COM devem gerenciar o tempo de vida desses objetos; o Common Language Runtime gerencia o tempo de vida de objetos em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="9d593-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="9d593-105">Os clientes de objetos COM descobrem se um serviço está disponível solicitando uma interface que fornece esse serviço e recebendo um ponteiro de interface ou não.</span><span class="sxs-lookup"><span data-stu-id="9d593-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="9d593-106">Os clientes de objetos .NET podem obter uma descrição da funcionalidade de um objeto usando a reflexão.</span><span class="sxs-lookup"><span data-stu-id="9d593-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="9d593-107">Os objetos .NET residem na memória gerenciada pelo ambiente de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d593-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="9d593-108">O ambiente de execução pode mover objetos na memória por motivos de desempenho e atualizar todas as referências nos objetos movidos por ele.</span><span class="sxs-lookup"><span data-stu-id="9d593-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="9d593-109">Os clientes não gerenciados, depois de obter um ponteiro para um objeto, dependem do objeto para permanecerem no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="9d593-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="9d593-110">Esses clientes não têm nenhum mecanismo para lidar com um objeto cujo local não é fixo.</span><span class="sxs-lookup"><span data-stu-id="9d593-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="9d593-111">Para superar essas diferenças, o tempo de execução fornece classes wrapper para fazer com que os clientes gerenciados e não gerenciados acreditem que estão chamando objetos em seus respectivos ambientes.</span><span class="sxs-lookup"><span data-stu-id="9d593-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="9d593-112">Sempre que o cliente gerenciado chama um método em um objeto COM, o tempo de execução cria um [RCW](../../../docs/framework/interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="9d593-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="9d593-113">Os RCWs eliminam as diferenças entre os mecanismos de referência gerenciada e não gerenciada, entre outras coisas.</span><span class="sxs-lookup"><span data-stu-id="9d593-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="9d593-114">O tempo de execução também cria um [CCW](../../../docs/framework/interop/com-callable-wrapper.md) (COM Callable Wrapper) para reverter o processo, permitindo que um cliente COM chame um método em um objeto .NET diretamente.</span><span class="sxs-lookup"><span data-stu-id="9d593-114">The runtime also creates a [COM callable wrapper](../../../docs/framework/interop/com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="9d593-115">Como mostra a ilustração a seguir, a perspectiva do código de chamada determina qual classe wrapper é criada pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9d593-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="9d593-116">![Visão geral do wrapper COM](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")</span><span class="sxs-lookup"><span data-stu-id="9d593-116">![COM wrapper overview](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="9d593-117">Visão geral do wrapper COM</span><span class="sxs-lookup"><span data-stu-id="9d593-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="9d593-118">Na maioria dos casos, o RCW padrão ou o CCW gerado pelo tempo de execução fornece o marshaling adequado para chamadas que cruzam o limite entre o COM e o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d593-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="9d593-119">Usando atributos personalizados, opcionalmente, você pode ajustar a maneira como o tempo de execução representa o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9d593-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d593-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d593-120">See Also</span></span>  
 [<span data-ttu-id="9d593-121">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="9d593-121">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="9d593-122">RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="9d593-122">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="9d593-123">COM Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="9d593-123">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)  
 [<span data-ttu-id="9d593-124">Personalizando Wrappers padrão</span><span class="sxs-lookup"><span data-stu-id="9d593-124">Customizing Standard Wrappers</span></span>](http://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d)  
 [<span data-ttu-id="9d593-125">Como personalizar RCWs (Runtime Callable Wrappers)</span><span class="sxs-lookup"><span data-stu-id="9d593-125">How to: Customize Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732)
