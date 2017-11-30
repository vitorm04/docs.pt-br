---
title: 'Pontos de extremidade: chamadas com falha por segundo'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f52a0f0b44a788bd5c2d34c125e31884c2a9afb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="fb04e-102">Pontos de extremidade: chamadas com falha por segundo</span><span class="sxs-lookup"><span data-stu-id="fb04e-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="fb04e-103">Nome do contador: Chamadas com falha por segundo.</span><span class="sxs-lookup"><span data-stu-id="fb04e-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb04e-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb04e-104">Description</span></span>  
 <span data-ttu-id="fb04e-105">Número de chamadas que retornados falhas para esse ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="fb04e-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="fb04e-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb04e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fb04e-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="fb04e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="fb04e-108">Em [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplicativos, métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento.</span><span class="sxs-lookup"><span data-stu-id="fb04e-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="fb04e-109">Falhas de SOAP são tipos de mensagem que estão incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar a execução mais robusta ou interativo.</span><span class="sxs-lookup"><span data-stu-id="fb04e-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="fb04e-110">Como falhas de SOAP são demonstradas para clientes em formato XML, eles são altamente interoperáveis.</span><span class="sxs-lookup"><span data-stu-id="fb04e-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb04e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb04e-111">See Also</span></span>  
 <span data-ttu-id="fb04e-112">[Specifying and Handling Faults in Contracts and Services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) (Especificando e lidando com falhas em contratos e serviços)</span><span class="sxs-lookup"><span data-stu-id="fb04e-112">[Specifying and Handling Faults in Contracts and Services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)</span></span>
