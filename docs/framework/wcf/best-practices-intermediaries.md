---
title: 'Práticas recomendadas: Intermediários'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 8b0e0e635c0e790b342115b988905ba29a6b8ad1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143994"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="7467e-102">Práticas recomendadas: Intermediários</span><span class="sxs-lookup"><span data-stu-id="7467e-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="7467e-103">Deve-se ter cuidado ao lidar com falhas corretamente ao chamar intermediários para certificar-se de canais do lado do serviço em intermediário são fechadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="7467e-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="7467e-104">Considere o cenário a seguir.</span><span class="sxs-lookup"><span data-stu-id="7467e-104">Consider the following scenario.</span></span> <span data-ttu-id="7467e-105">Um cliente faz uma chamada para um intermediário que, em seguida, chama um serviço de back-end.</span><span class="sxs-lookup"><span data-stu-id="7467e-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="7467e-106">O serviço de back-end não define nenhum contrato de falha, portanto, qualquer falha lançada a partir desse serviço será tratada como uma falha não tipada.</span><span class="sxs-lookup"><span data-stu-id="7467e-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="7467e-107">O serviço de back-end gerará um <xref:System.ApplicationException> e corretamente, o WCF anulará o canal do lado do serviço.</span><span class="sxs-lookup"><span data-stu-id="7467e-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="7467e-108">O <xref:System.ApplicationException> , em seguida, revela como um <xref:System.ServiceModel.FaultException> que é gerada para o intermediário.</span><span class="sxs-lookup"><span data-stu-id="7467e-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="7467e-109">Intermediário gera novamente o <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="7467e-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="7467e-110">O WCF interpreta isso como uma falha sem tipo de intermediário e o encaminha para o cliente.</span><span class="sxs-lookup"><span data-stu-id="7467e-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="7467e-111">Ao receber a falha, intermediário e o cliente falha seus canais do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="7467e-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="7467e-112">Canal do lado do serviço do intermediário porém permanece aberta porque o WCF não reconhece que a falha é fatal.</span><span class="sxs-lookup"><span data-stu-id="7467e-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="7467e-113">A prática recomendada neste cenário é detectar se a falha proveniente do serviço é fatal e então intermediário deve falha seu canal do lado do serviço, conforme mostrado no trecho de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7467e-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7467e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7467e-114">See Also</span></span>  
 [<span data-ttu-id="7467e-115">Tratamento de erro do WCF</span><span class="sxs-lookup"><span data-stu-id="7467e-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)  
 [<span data-ttu-id="7467e-116">Especificando e lidando com falhas em contratos e serviços</span><span class="sxs-lookup"><span data-stu-id="7467e-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
