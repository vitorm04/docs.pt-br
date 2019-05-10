---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662817"
---
# <a name="activitytransfer"></a><span data-ttu-id="e45e5-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="e45e5-102">ActivityTransfer</span></span>
<span data-ttu-id="e45e5-103">Evento de transferência de atividade</span><span class="sxs-lookup"><span data-stu-id="e45e5-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e45e5-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e45e5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e45e5-105">Methods</span></span>  
 <span data-ttu-id="e45e5-106">A classe ActivityTransfer não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="e45e5-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e45e5-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e45e5-107">Properties</span></span>  
 <span data-ttu-id="e45e5-108">A classe ActivityTransfer tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e45e5-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="e45e5-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="e45e5-109">ActivityID</span></span>  
  
- <span data-ttu-id="e45e5-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="e45e5-110">Data type: object</span></span>  
    <span data-ttu-id="e45e5-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e45e5-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="e45e5-112">ID da Atividade</span><span class="sxs-lookup"><span data-stu-id="e45e5-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="e45e5-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="e45e5-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="e45e5-114">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="e45e5-114">Data type: object</span></span>  
    <span data-ttu-id="e45e5-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e45e5-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="e45e5-116">ID da atividade relacionada</span><span class="sxs-lookup"><span data-stu-id="e45e5-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e45e5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e45e5-117">Requirements</span></span>  
  
|<span data-ttu-id="e45e5-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e45e5-118">MOF</span></span>|<span data-ttu-id="e45e5-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e45e5-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e45e5-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="e45e5-120">Namespace</span></span>|<span data-ttu-id="e45e5-121">Definido no root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="e45e5-121">Defined in root\ServiceModel.</span></span>|
