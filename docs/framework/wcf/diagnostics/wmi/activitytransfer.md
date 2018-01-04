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
ms.workload: dotnet
ms.openlocfilehash: 7f3db50a32fabc117c79eef5ac086a7798f86ed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="ff415-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="ff415-102">ActivityTransfer</span></span>
<span data-ttu-id="ff415-103">Evento de transferência da atividade</span><span class="sxs-lookup"><span data-stu-id="ff415-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff415-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff415-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ff415-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ff415-105">Methods</span></span>  
 <span data-ttu-id="ff415-106">A classe ActivityTransfer não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="ff415-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ff415-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ff415-107">Properties</span></span>  
 <span data-ttu-id="ff415-108">A classe ActivityTransfer tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ff415-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="ff415-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="ff415-109">ActivityID</span></span>  
  
-   <span data-ttu-id="ff415-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="ff415-110">Data type: object</span></span>  
    <span data-ttu-id="ff415-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ff415-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="ff415-112">ID da Atividade</span><span class="sxs-lookup"><span data-stu-id="ff415-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="ff415-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="ff415-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="ff415-114">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="ff415-114">Data type: object</span></span>  
    <span data-ttu-id="ff415-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ff415-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="ff415-116">ID da atividade relacionada</span><span class="sxs-lookup"><span data-stu-id="ff415-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff415-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff415-117">Requirements</span></span>  
  
|<span data-ttu-id="ff415-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ff415-118">MOF</span></span>|<span data-ttu-id="ff415-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ff415-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ff415-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="ff415-120">Namespace</span></span>|<span data-ttu-id="ff415-121">Definido em root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="ff415-121">Defined in root\ServiceModel.</span></span>|
