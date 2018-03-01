---
title: "Sindicalização do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1f7f5fd65fc298107a66e2049c059f3cc58b3d44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-syndication"></a><span data-ttu-id="f991c-102">Sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="f991c-102">WCF Syndication</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f991c-103">fornece suporte para trabalhar facilmente com feeds de agregação em Atom, RSS ou outros formatos personalizados, que permite a leitura e criá-los, bem como expô-los em um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="f991c-103"> provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="f991c-104">Os tópicos nesta seção descrevem este modelo de programação para distribuição em detalhes.</span><span class="sxs-lookup"><span data-stu-id="f991c-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f991c-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f991c-105">In This Section</span></span>  
 [<span data-ttu-id="f991c-106">Visão geral de sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="f991c-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="f991c-107">Fornece uma visão geral do suporte a distribuição fornecida pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f991c-107">Provides an overview of syndication support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="f991c-108">Arquitetura de sindicalização</span><span class="sxs-lookup"><span data-stu-id="f991c-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="f991c-109">Descreve as classes no modelo de objeto e a extensibilidade de distribuição.</span><span class="sxs-lookup"><span data-stu-id="f991c-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="f991c-110">Como o modelo de objeto de sindicalização do WCF é mapeado para Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="f991c-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="f991c-111">Descreve como os feeds são representados dentro do modelo de objeto de distribuição do WCF e como eles são convertidos em RSS e feeds Atom.</span><span class="sxs-lookup"><span data-stu-id="f991c-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="f991c-112">Como criar um feed RSS básico</span><span class="sxs-lookup"><span data-stu-id="f991c-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="f991c-113">Mostra como criar um serviço que disponibiliza um básico RSS feed.</span><span class="sxs-lookup"><span data-stu-id="f991c-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="f991c-114">Como criar um feed Atom básico</span><span class="sxs-lookup"><span data-stu-id="f991c-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="f991c-115">Mostra como criar um serviço que disponibiliza um básica ATOM feed.</span><span class="sxs-lookup"><span data-stu-id="f991c-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="f991c-116">Como expor um Feed como Atom e RSS</span><span class="sxs-lookup"><span data-stu-id="f991c-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="f991c-117">Mostra como criar um serviço que disponibiliza o mesmo feed ATOM e RSS.</span><span class="sxs-lookup"><span data-stu-id="f991c-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="f991c-118">Extensibilidade de sindicalização</span><span class="sxs-lookup"><span data-stu-id="f991c-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="f991c-119">Descreve os métodos de adição de elementos personalizados e atributos para um feed de distribuição.</span><span class="sxs-lookup"><span data-stu-id="f991c-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f991c-120">Referência</span><span class="sxs-lookup"><span data-stu-id="f991c-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f991c-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f991c-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f991c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f991c-122">See Also</span></span>  
 [<span data-ttu-id="f991c-123">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="f991c-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="f991c-124">Confiança parcial</span><span class="sxs-lookup"><span data-stu-id="f991c-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)
