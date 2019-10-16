---
title: Recursos do sistema operacional exigidos pelo WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: ac9bd5ed7c2092720c6521d0f78185c3fbf9f94b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318941"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="8de8b-102">Recursos do sistema operacional exigidos pelo WCF</span><span class="sxs-lookup"><span data-stu-id="8de8b-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="8de8b-103">O Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para funcionar.</span><span class="sxs-lookup"><span data-stu-id="8de8b-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="8de8b-104">A tabela a seguir lista esses recursos.</span><span class="sxs-lookup"><span data-stu-id="8de8b-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="8de8b-105">Recurso</span><span class="sxs-lookup"><span data-stu-id="8de8b-105">Resource</span></span>|<span data-ttu-id="8de8b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="8de8b-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8de8b-107">Coordenador de Transações Distribuídas da Microsoft (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="8de8b-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="8de8b-108">Necessário para dar suporte a transações OleTx.</span><span class="sxs-lookup"><span data-stu-id="8de8b-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="8de8b-109">Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="8de8b-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="8de8b-110">Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8de8b-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="8de8b-111">Serviço de Ativação de Processos do Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="8de8b-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="8de8b-112">Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8de8b-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8de8b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8de8b-113">See also</span></span>

- [<span data-ttu-id="8de8b-114">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="8de8b-114">System Requirements</span></span>](wcf-system-requirements.md)
