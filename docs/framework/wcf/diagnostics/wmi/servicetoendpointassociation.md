---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452703"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="1c7a6-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="1c7a6-102">ServiceToEndpointAssociation</span></span>
<span data-ttu-id="1c7a6-103">Mapeia um serviço para um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c7a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c7a6-104">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1c7a6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1c7a6-105">Methods</span></span>  
 <span data-ttu-id="1c7a6-106">A classe ServiceToEndpointAssociation não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1c7a6-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1c7a6-107">Properties</span></span>  
 <span data-ttu-id="1c7a6-108">A classe ServiceToEndpointAssociation tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1c7a6-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="1c7a6-109">ref</span><span class="sxs-lookup"><span data-stu-id="1c7a6-109">ref</span></span>  
 <span data-ttu-id="1c7a6-110">Tipo de dados: serviço</span><span class="sxs-lookup"><span data-stu-id="1c7a6-110">Data type: Service</span></span>  
  
 <span data-ttu-id="1c7a6-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c7a6-111">Access type: Read-only</span></span>  
<span data-ttu-id="1c7a6-112">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="1c7a6-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="1c7a6-113">O serviço associado com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="1c7a6-114">ref</span><span class="sxs-lookup"><span data-stu-id="1c7a6-114">ref</span></span>  
 <span data-ttu-id="1c7a6-115">Tipo de dados: ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="1c7a6-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="1c7a6-116">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c7a6-116">Access type: Read-only</span></span>  
<span data-ttu-id="1c7a6-117">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="1c7a6-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="1c7a6-118">O ponto de extremidade associado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c7a6-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c7a6-119">Requirements</span></span>  
  
|<span data-ttu-id="1c7a6-120">MOF</span><span class="sxs-lookup"><span data-stu-id="1c7a6-120">MOF</span></span>|<span data-ttu-id="1c7a6-121">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1c7a6-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="1c7a6-122">Namespace</span></span>|<span data-ttu-id="1c7a6-123">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c7a6-123">Defined in root\ServiceModel</span></span>|
