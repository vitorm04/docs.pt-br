---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484323"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="b6d80-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="b6d80-102">ServiceToEndpointAssociation</span></span>
<span data-ttu-id="b6d80-103">Um serviço é mapeado para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b6d80-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6d80-104">Syntax</span></span>  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b6d80-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b6d80-105">Methods</span></span>  
 <span data-ttu-id="b6d80-106">A classe ServiceToEndpointAssociation não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="b6d80-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b6d80-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b6d80-107">Properties</span></span>  
 <span data-ttu-id="b6d80-108">A classe ServiceToEndpointAssociation tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b6d80-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b6d80-109">ref</span><span class="sxs-lookup"><span data-stu-id="b6d80-109">ref</span></span>  
 <span data-ttu-id="b6d80-110">Tipo de dados: serviço</span><span class="sxs-lookup"><span data-stu-id="b6d80-110">Data type: Service</span></span>  
  
 <span data-ttu-id="b6d80-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b6d80-111">Access type: Read-only</span></span>  
<span data-ttu-id="b6d80-112">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="b6d80-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="b6d80-113">O serviço associado com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b6d80-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b6d80-114">ref</span><span class="sxs-lookup"><span data-stu-id="b6d80-114">ref</span></span>  
 <span data-ttu-id="b6d80-115">Tipo de dados: ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="b6d80-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="b6d80-116">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b6d80-116">Access type: Read-only</span></span>  
<span data-ttu-id="b6d80-117">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="b6d80-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="b6d80-118">O ponto de extremidade associado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="b6d80-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d80-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6d80-119">Requirements</span></span>  
  
|<span data-ttu-id="b6d80-120">MOF</span><span class="sxs-lookup"><span data-stu-id="b6d80-120">MOF</span></span>|<span data-ttu-id="b6d80-121">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b6d80-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b6d80-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="b6d80-122">Namespace</span></span>|<span data-ttu-id="b6d80-123">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b6d80-123">Defined in root\ServiceModel</span></span>|
