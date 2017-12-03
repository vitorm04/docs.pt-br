---
title: "Práticas recomendadas: intermediárias"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfedfbd0177018de4affce67f16ee5f713f7d5de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="e62a7-102">Práticas recomendadas: intermediárias</span><span class="sxs-lookup"><span data-stu-id="e62a7-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="e62a7-103">Deve-se ter cuidado para lidar com falhas corretamente ao chamar intermediários para certificar-se de canais do lado do serviço em intermediária estão fechados corretamente.</span><span class="sxs-lookup"><span data-stu-id="e62a7-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="e62a7-104">Considere o cenário a seguir.</span><span class="sxs-lookup"><span data-stu-id="e62a7-104">Consider the following scenario.</span></span> <span data-ttu-id="e62a7-105">Um cliente faz uma chamada para um intermediário que chama um serviço back-end.</span><span class="sxs-lookup"><span data-stu-id="e62a7-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="e62a7-106">O serviço de back-end não define nenhum contrato de falha, portanto, qualquer falha gerada por esse serviço será tratada como uma falha não digitada.</span><span class="sxs-lookup"><span data-stu-id="e62a7-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="e62a7-107">A serviço de back-end lança um <xref:System.ApplicationException> e WCF corretamente anula o canal do lado do serviço.</span><span class="sxs-lookup"><span data-stu-id="e62a7-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="e62a7-108">O <xref:System.ApplicationException> superfícies, em seguida, como um <xref:System.ServiceModel.FaultException> que é gerada para o intermediário.</span><span class="sxs-lookup"><span data-stu-id="e62a7-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="e62a7-109">Intermediária gera novamente o <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="e62a7-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="e62a7-110">WCF interpreta como uma falha não digitada do intermediária e a encaminha para o cliente.</span><span class="sxs-lookup"><span data-stu-id="e62a7-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="e62a7-111">Ao receber a falha, intermediária e o cliente falha seus canais de cliente.</span><span class="sxs-lookup"><span data-stu-id="e62a7-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="e62a7-112">Canal do lado do serviço do intermediário porém permanece aberta porque o WCF não sabe que a falha é fatal.</span><span class="sxs-lookup"><span data-stu-id="e62a7-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="e62a7-113">É a prática recomendada neste cenário detectar se a falha proveniente do serviço é fatal e então intermediária deve falha seu canal do lado do serviço, conforme mostrado no seguinte trecho de código.</span><span class="sxs-lookup"><span data-stu-id="e62a7-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e62a7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e62a7-114">See Also</span></span>  
 <span data-ttu-id="e62a7-115">[WCF Error Handling](../../../docs/framework/wcf/wcf-error-handling.md) (Tratamento de erro do WCF)</span><span class="sxs-lookup"><span data-stu-id="e62a7-115">[WCF Error Handling](../../../docs/framework/wcf/wcf-error-handling.md)</span></span>  
 <span data-ttu-id="e62a7-116">[Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) (Especificando e lidando com falhas em contratos e serviços)</span><span class="sxs-lookup"><span data-stu-id="e62a7-116">[Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)</span></span>
