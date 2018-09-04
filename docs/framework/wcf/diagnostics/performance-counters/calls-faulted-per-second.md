---
title: Chamadas com falha por segundo
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 03ee2155504a021efadac00df6f7b9271baa5a65
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505773"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="6d8f6-102">Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="6d8f6-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="6d8f6-103">Nome do contador: Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="6d8f6-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="6d8f6-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d8f6-104">Description</span></span>  
 <span data-ttu-id="6d8f6-105">Número de chamadas que retornaram falhas para essa operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="6d8f6-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="6d8f6-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d8f6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6d8f6-107">(N 1 - N 0) / ((1!D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="6d8f6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="6d8f6-108">Em aplicativos do Windows Communication Foundation (WCF), métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento.</span><span class="sxs-lookup"><span data-stu-id="6d8f6-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="6d8f6-109">Falhas de SOAP são tipos de mensagem que são incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar sua execução mais robusta ou interativo.</span><span class="sxs-lookup"><span data-stu-id="6d8f6-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="6d8f6-110">Como falhas de SOAP são demonstradas para clientes no formato XML, eles são altamente interoperáveis.</span><span class="sxs-lookup"><span data-stu-id="6d8f6-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8f6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d8f6-111">See Also</span></span>  
 [<span data-ttu-id="6d8f6-112">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="6d8f6-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
