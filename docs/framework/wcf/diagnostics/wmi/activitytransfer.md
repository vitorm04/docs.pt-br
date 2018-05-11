---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="activitytransfer"></a><span data-ttu-id="99a70-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="99a70-102">ActivityTransfer</span></span>
<span data-ttu-id="99a70-103">Evento de transferência da atividade</span><span class="sxs-lookup"><span data-stu-id="99a70-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99a70-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="99a70-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="99a70-105">Methods</span></span>  
 <span data-ttu-id="99a70-106">A classe ActivityTransfer não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="99a70-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="99a70-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="99a70-107">Properties</span></span>  
 <span data-ttu-id="99a70-108">A classe ActivityTransfer tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="99a70-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="99a70-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="99a70-109">ActivityID</span></span>  
  
-   <span data-ttu-id="99a70-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="99a70-110">Data type: object</span></span>  
    <span data-ttu-id="99a70-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="99a70-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="99a70-112">ID da Atividade</span><span class="sxs-lookup"><span data-stu-id="99a70-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="99a70-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="99a70-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="99a70-114">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="99a70-114">Data type: object</span></span>  
    <span data-ttu-id="99a70-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="99a70-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="99a70-116">ID da atividade relacionada</span><span class="sxs-lookup"><span data-stu-id="99a70-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99a70-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99a70-117">Requirements</span></span>  
  
|<span data-ttu-id="99a70-118">MOF</span><span class="sxs-lookup"><span data-stu-id="99a70-118">MOF</span></span>|<span data-ttu-id="99a70-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="99a70-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="99a70-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="99a70-120">Namespace</span></span>|<span data-ttu-id="99a70-121">Definido em root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="99a70-121">Defined in root\ServiceModel.</span></span>|
