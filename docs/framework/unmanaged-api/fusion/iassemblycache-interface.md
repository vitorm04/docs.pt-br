---
title: Interface IAssemblyCache
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
ms.openlocfilehash: 5ed0075da1429c70900750f3f28e8ce36a41fb28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134534"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="0cf05-102">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="0cf05-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="0cf05-103">Representa o cache de assembly global para uso pela tecnologia Fusion.</span><span class="sxs-lookup"><span data-stu-id="0cf05-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0cf05-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0cf05-104">Methods</span></span>  
  
|<span data-ttu-id="0cf05-105">Método</span><span class="sxs-lookup"><span data-stu-id="0cf05-105">Method</span></span>|<span data-ttu-id="0cf05-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cf05-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0cf05-107">Método CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="0cf05-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="0cf05-108">Obtém uma referência a um novo [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0cf05-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="0cf05-109">Método CreateAssemblyScavenger</span><span class="sxs-lookup"><span data-stu-id="0cf05-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="0cf05-110">Reservado para uso interno pela tecnologia Fusion.</span><span class="sxs-lookup"><span data-stu-id="0cf05-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="0cf05-111">Método InstallAssembly</span><span class="sxs-lookup"><span data-stu-id="0cf05-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="0cf05-112">Instala o assembly especificado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="0cf05-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="0cf05-113">Método QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="0cf05-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="0cf05-114">Obtém os dados solicitados sobre o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="0cf05-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="0cf05-115">Método UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="0cf05-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="0cf05-116">Desinstala o assembly especificado do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="0cf05-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0cf05-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0cf05-117">Requirements</span></span>  
 <span data-ttu-id="0cf05-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cf05-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cf05-119">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0cf05-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0cf05-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf05-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf05-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cf05-121">See also</span></span>

- [<span data-ttu-id="0cf05-122">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="0cf05-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="0cf05-123">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="0cf05-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)
