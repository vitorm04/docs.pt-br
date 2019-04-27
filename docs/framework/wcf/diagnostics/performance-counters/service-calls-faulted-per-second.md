---
title: 'Serviço: Chamadas com falha por segundo'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 595b623d70bad82ea39ab3ef93fb5fd499268ff2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915701"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="eb596-102">Serviço: Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="eb596-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="eb596-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="eb596-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="eb596-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb596-104">Description</span></span>  
 <span data-ttu-id="eb596-105">Número de chamadas que retornaram falhas para esse serviço em um segundo.</span><span class="sxs-lookup"><span data-stu-id="eb596-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="eb596-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="eb596-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="eb596-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="eb596-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="eb596-108">Em aplicativos do Windows Communication Foundation (WCF), métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento.</span><span class="sxs-lookup"><span data-stu-id="eb596-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="eb596-109">Falhas de SOAP são tipos de mensagem que são incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar sua execução mais robusta ou interativo.</span><span class="sxs-lookup"><span data-stu-id="eb596-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="eb596-110">Como falhas de SOAP são demonstradas para clientes no formato XML, eles são altamente interoperáveis.</span><span class="sxs-lookup"><span data-stu-id="eb596-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb596-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb596-111">See also</span></span>

- [<span data-ttu-id="eb596-112">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="eb596-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
