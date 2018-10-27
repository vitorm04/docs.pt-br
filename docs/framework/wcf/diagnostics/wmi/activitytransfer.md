---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034411"
---
# <a name="activitytransfer"></a><span data-ttu-id="4a426-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="4a426-102">ActivityTransfer</span></span>
<span data-ttu-id="4a426-103">Evento de transferência de atividade</span><span class="sxs-lookup"><span data-stu-id="4a426-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a426-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a426-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4a426-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4a426-105">Methods</span></span>  
 <span data-ttu-id="4a426-106">A classe ActivityTransfer não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="4a426-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4a426-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4a426-107">Properties</span></span>  
 <span data-ttu-id="4a426-108">A classe ActivityTransfer tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="4a426-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="4a426-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="4a426-109">ActivityID</span></span>  
  
-   <span data-ttu-id="4a426-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="4a426-110">Data type: object</span></span>  
    <span data-ttu-id="4a426-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4a426-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="4a426-112">ID da Atividade</span><span class="sxs-lookup"><span data-stu-id="4a426-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="4a426-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="4a426-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="4a426-114">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="4a426-114">Data type: object</span></span>  
    <span data-ttu-id="4a426-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4a426-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="4a426-116">ID da atividade relacionada</span><span class="sxs-lookup"><span data-stu-id="4a426-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a426-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a426-117">Requirements</span></span>  
  
|<span data-ttu-id="4a426-118">MOF</span><span class="sxs-lookup"><span data-stu-id="4a426-118">MOF</span></span>|<span data-ttu-id="4a426-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4a426-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4a426-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="4a426-120">Namespace</span></span>|<span data-ttu-id="4a426-121">Definido no root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="4a426-121">Defined in root\ServiceModel.</span></span>|
