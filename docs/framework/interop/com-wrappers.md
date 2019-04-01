---
title: Wrappers COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce15e0535bbd6bc67054c651a518f11cf9dd2ae1
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410349"
---
# <a name="com-wrappers"></a><span data-ttu-id="1ca62-102">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="1ca62-102">COM Wrappers</span></span>
<span data-ttu-id="1ca62-103">O COM difere do modelo de objeto .NET Framework de várias maneiras importantes:</span><span class="sxs-lookup"><span data-stu-id="1ca62-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="1ca62-104">Os clientes de objetos COM devem gerenciar o tempo de vida desses objetos; o Common Language Runtime gerencia o tempo de vida de objetos em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="1ca62-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="1ca62-105">Os clientes de objetos COM descobrem se um serviço está disponível solicitando uma interface que fornece esse serviço e recebendo um ponteiro de interface ou não.</span><span class="sxs-lookup"><span data-stu-id="1ca62-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="1ca62-106">Os clientes de objetos .NET podem obter uma descrição da funcionalidade de um objeto usando a reflexão.</span><span class="sxs-lookup"><span data-stu-id="1ca62-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="1ca62-107">Os objetos .NET residem na memória gerenciada pelo ambiente de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ca62-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="1ca62-108">O ambiente de execução pode mover objetos na memória por motivos de desempenho e atualizar todas as referências nos objetos movidos por ele.</span><span class="sxs-lookup"><span data-stu-id="1ca62-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="1ca62-109">Os clientes não gerenciados, depois de obter um ponteiro para um objeto, dependem do objeto para permanecerem no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="1ca62-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="1ca62-110">Esses clientes não têm nenhum mecanismo para lidar com um objeto cujo local não é fixo.</span><span class="sxs-lookup"><span data-stu-id="1ca62-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="1ca62-111">Para superar essas diferenças, o tempo de execução fornece classes wrapper para fazer com que os clientes gerenciados e não gerenciados acreditem que estão chamando objetos em seus respectivos ambientes.</span><span class="sxs-lookup"><span data-stu-id="1ca62-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="1ca62-112">Sempre que o cliente gerenciado chama um método em um objeto COM, o tempo de execução cria um [RCW](runtime-callable-wrapper.md) (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="1ca62-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="1ca62-113">Os RCWs eliminam as diferenças entre os mecanismos de referência gerenciada e não gerenciada, entre outras coisas.</span><span class="sxs-lookup"><span data-stu-id="1ca62-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="1ca62-114">O tempo de execução também cria um [CCW](com-callable-wrapper.md) (COM Callable Wrapper) para reverter o processo, permitindo que um cliente COM chame um método em um objeto .NET diretamente.</span><span class="sxs-lookup"><span data-stu-id="1ca62-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="1ca62-115">Como mostra a ilustração a seguir, a perspectiva do código de chamada determina qual classe wrapper é criada pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1ca62-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Visão geral do wrapper COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="1ca62-117">Na maioria dos casos, o RCW padrão ou o CCW gerado pelo tempo de execução fornece o marshaling adequado para chamadas que cruzam o limite entre o COM e o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ca62-117">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="1ca62-118">Usando atributos personalizados, opcionalmente, você pode ajustar a maneira como o tempo de execução representa o código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1ca62-118">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca62-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ca62-119">See also</span></span>
- <span data-ttu-id="1ca62-120">[Interoperabilidade COM avançada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1ca62-120">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="1ca62-121">RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="1ca62-121">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="1ca62-122">COM Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="1ca62-122">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="1ca62-123">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)) (Personalizando wrappers padrão)</span><span class="sxs-lookup"><span data-stu-id="1ca62-123">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="1ca62-124">[Como: Personalizar RCWs (Runtime Callable Wrappers)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1ca62-124">[How to: Customize Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
