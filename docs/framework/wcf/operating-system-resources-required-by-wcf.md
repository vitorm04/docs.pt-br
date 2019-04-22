---
title: Recursos do sistema operacional exigidos pelo WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100924"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="559b0-102">Recursos do sistema operacional exigidos pelo WCF</span><span class="sxs-lookup"><span data-stu-id="559b0-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="559b0-103">Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para a função.</span><span class="sxs-lookup"><span data-stu-id="559b0-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="559b0-104">A tabela a seguir lista esses recursos.</span><span class="sxs-lookup"><span data-stu-id="559b0-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="559b0-105">Recurso</span><span class="sxs-lookup"><span data-stu-id="559b0-105">Resource</span></span>|<span data-ttu-id="559b0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="559b0-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="559b0-107">Coordenador de Transações Distribuídas da Microsoft (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="559b0-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="559b0-108">Necessário para dar suporte a transações OleTx.</span><span class="sxs-lookup"><span data-stu-id="559b0-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="559b0-109">Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="559b0-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="559b0-110">Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="559b0-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="559b0-111">Serviço de Ativação de Processos do Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="559b0-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="559b0-112">Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="559b0-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="559b0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="559b0-113">See also</span></span>

- [<span data-ttu-id="559b0-114">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="559b0-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
