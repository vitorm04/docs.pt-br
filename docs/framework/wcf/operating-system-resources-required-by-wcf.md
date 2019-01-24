---
title: Recursos do sistema operacional exigidos pelo WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 759ab099066e300484860cf3f91d6d084ba1d339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527075"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="d8bd5-102">Recursos do sistema operacional exigidos pelo WCF</span><span class="sxs-lookup"><span data-stu-id="d8bd5-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="d8bd5-103">Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para a função.</span><span class="sxs-lookup"><span data-stu-id="d8bd5-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="d8bd5-104">A tabela a seguir lista esses recursos.</span><span class="sxs-lookup"><span data-stu-id="d8bd5-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="d8bd5-105">Recurso</span><span class="sxs-lookup"><span data-stu-id="d8bd5-105">Resource</span></span>|<span data-ttu-id="d8bd5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8bd5-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d8bd5-107">Coordenador de Transações Distribuídas da Microsoft (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="d8bd5-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="d8bd5-108">Necessário para dar suporte a transações OleTx.</span><span class="sxs-lookup"><span data-stu-id="d8bd5-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="d8bd5-109">Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="d8bd5-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="d8bd5-110">Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8bd5-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="d8bd5-111">Serviço de Ativação de Processos do Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="d8bd5-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="d8bd5-112">Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8bd5-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8bd5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8bd5-113">See also</span></span>
- [<span data-ttu-id="d8bd5-114">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="d8bd5-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
