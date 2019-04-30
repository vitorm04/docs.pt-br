---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964288"
---
# <a name="activitytransfer"></a><span data-ttu-id="332ec-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="332ec-102">ActivityTransfer</span></span>
<span data-ttu-id="332ec-103">Evento de transferência de atividade</span><span class="sxs-lookup"><span data-stu-id="332ec-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="332ec-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="332ec-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="332ec-105">Methods</span></span>  
 <span data-ttu-id="332ec-106">A classe ActivityTransfer não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="332ec-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="332ec-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="332ec-107">Properties</span></span>  
 <span data-ttu-id="332ec-108">A classe ActivityTransfer tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="332ec-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="332ec-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="332ec-109">ActivityID</span></span>  
  
- <span data-ttu-id="332ec-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="332ec-110">Data type: object</span></span>  
    <span data-ttu-id="332ec-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="332ec-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="332ec-112">ID da Atividade</span><span class="sxs-lookup"><span data-stu-id="332ec-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="332ec-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="332ec-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="332ec-114">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="332ec-114">Data type: object</span></span>  
    <span data-ttu-id="332ec-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="332ec-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="332ec-116">ID da atividade relacionada</span><span class="sxs-lookup"><span data-stu-id="332ec-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="332ec-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="332ec-117">Requirements</span></span>  
  
|<span data-ttu-id="332ec-118">MOF</span><span class="sxs-lookup"><span data-stu-id="332ec-118">MOF</span></span>|<span data-ttu-id="332ec-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="332ec-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="332ec-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="332ec-120">Namespace</span></span>|<span data-ttu-id="332ec-121">Definido no root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="332ec-121">Defined in root\ServiceModel.</span></span>|
