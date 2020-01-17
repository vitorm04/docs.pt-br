---
title: Chamadas com falha por segundo
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 37fd47a3e4ca474338a4a6ae1117c2626acb546f
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163144"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="6a969-102">Chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="6a969-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="6a969-103">Nome do contador: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="6a969-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="6a969-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a969-104">Description</span></span>  
 <span data-ttu-id="6a969-105">Número de chamadas que retornaram falhas para esta operação em um segundo.</span><span class="sxs-lookup"><span data-stu-id="6a969-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="6a969-106">Este contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a969-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6a969-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="6a969-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="6a969-108">Em aplicativos Windows Communication Foundation (WCF), os métodos de serviço comunicam informações de erro de processamento usando mensagens de falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="6a969-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="6a969-109">Falhas de SOAP são tipos de mensagem que são incluídos nos metadados de uma operação de serviço e, portanto, criam um contrato de falha que os clientes podem usar para tornar sua execução mais robusta ou interativa.</span><span class="sxs-lookup"><span data-stu-id="6a969-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="6a969-110">Como as falhas de SOAP são expressas para clientes em formato XML, elas são altamente interoperáveis.</span><span class="sxs-lookup"><span data-stu-id="6a969-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a969-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="6a969-111">See also</span></span>

- [<span data-ttu-id="6a969-112">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="6a969-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
