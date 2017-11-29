---
title: Recursos do sistema operacional exigidos pelo WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cfe114e5e044a6aaa1e356194a46b4a46011aa0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="a87da-102">Recursos do sistema operacional exigidos pelo WCF</span><span class="sxs-lookup"><span data-stu-id="a87da-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="a87da-103">O [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] depende de vários recursos que são fornecidos pelo sistema operacional para funcionar.</span><span class="sxs-lookup"><span data-stu-id="a87da-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="a87da-104">A tabela a seguir lista esses recursos.</span><span class="sxs-lookup"><span data-stu-id="a87da-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="a87da-105">Recurso</span><span class="sxs-lookup"><span data-stu-id="a87da-105">Resource</span></span>|<span data-ttu-id="a87da-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a87da-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a87da-107">Coordenador de Transações Distribuídas da Microsoft (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="a87da-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="a87da-108">Necessário para dar suporte a transações OleTx.</span><span class="sxs-lookup"><span data-stu-id="a87da-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="a87da-109">Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="a87da-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="a87da-110">Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a87da-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="a87da-111">Serviço de Ativação de Processos do Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="a87da-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="a87da-112">Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a87da-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a87da-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a87da-113">See Also</span></span>  
 [<span data-ttu-id="a87da-114">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="a87da-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
