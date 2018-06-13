---
title: Recursos do sistema operacional exigidos pelo WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498638"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="6a6f9-102">Recursos do sistema operacional exigidos pelo WCF</span><span class="sxs-lookup"><span data-stu-id="6a6f9-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="6a6f9-103">Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para a função.</span><span class="sxs-lookup"><span data-stu-id="6a6f9-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="6a6f9-104">A tabela a seguir lista esses recursos.</span><span class="sxs-lookup"><span data-stu-id="6a6f9-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="6a6f9-105">Recurso</span><span class="sxs-lookup"><span data-stu-id="6a6f9-105">Resource</span></span>|<span data-ttu-id="6a6f9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a6f9-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6a6f9-107">Coordenador de Transações Distribuídas da Microsoft (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="6a6f9-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="6a6f9-108">Necessário para dar suporte a transações OleTx.</span><span class="sxs-lookup"><span data-stu-id="6a6f9-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="6a6f9-109">Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="6a6f9-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="6a6f9-110">Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a6f9-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="6a6f9-111">Serviço de Ativação de Processos do Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="6a6f9-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="6a6f9-112">Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a6f9-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a6f9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a6f9-113">See Also</span></span>  
 [<span data-ttu-id="6a6f9-114">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="6a6f9-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
