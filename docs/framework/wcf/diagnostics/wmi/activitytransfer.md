---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c1caf0ae27efce858328e5db88434253be61d50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="fc902-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="fc902-102">ActivityTransfer</span></span>
<span data-ttu-id="fc902-103">Evento de transferência da atividade</span><span class="sxs-lookup"><span data-stu-id="fc902-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc902-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc902-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fc902-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="fc902-105">Methods</span></span>  
 <span data-ttu-id="fc902-106">A classe ActivityTransfer não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="fc902-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fc902-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="fc902-107">Properties</span></span>  
 <span data-ttu-id="fc902-108">A classe ActivityTransfer tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="fc902-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="fc902-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="fc902-109">ActivityID</span></span>  
  
-   <span data-ttu-id="fc902-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="fc902-110">Data type: object</span></span>  
    <span data-ttu-id="fc902-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="fc902-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="fc902-112">ID da Atividade</span><span class="sxs-lookup"><span data-stu-id="fc902-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="fc902-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="fc902-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="fc902-114">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="fc902-114">Data type: object</span></span>  
    <span data-ttu-id="fc902-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="fc902-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="fc902-116">ID da atividade relacionada</span><span class="sxs-lookup"><span data-stu-id="fc902-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc902-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc902-117">Requirements</span></span>  
  
|<span data-ttu-id="fc902-118">MOF</span><span class="sxs-lookup"><span data-stu-id="fc902-118">MOF</span></span>|<span data-ttu-id="fc902-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fc902-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fc902-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="fc902-120">Namespace</span></span>|<span data-ttu-id="fc902-121">Definido em root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="fc902-121">Defined in root\ServiceModel.</span></span>|
