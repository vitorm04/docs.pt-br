---
title: Interface ICorPublishProcess
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182956"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="72a2e-102">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="72a2e-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="72a2e-103">Fornece métodos que acessam informações a serem exibidos sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="72a2e-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72a2e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="72a2e-104">Methods</span></span>  
  
|<span data-ttu-id="72a2e-105">Método</span><span class="sxs-lookup"><span data-stu-id="72a2e-105">Method</span></span>|<span data-ttu-id="72a2e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="72a2e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72a2e-107">Método EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="72a2e-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="72a2e-108">Obtém uma [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instância que contém os domínios de aplicativo no processo de referenciada por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="72a2e-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="72a2e-109">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="72a2e-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="72a2e-110">Obtém o caminho completo do executável para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="72a2e-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="72a2e-111">Método GetProcessID</span><span class="sxs-lookup"><span data-stu-id="72a2e-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="72a2e-112">Obtém o identificador de sistema operacional para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="72a2e-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="72a2e-113">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="72a2e-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="72a2e-114">Obtém um valor que indica se o processo é referenciada por este `ICorPublishProcess` é conhecido por estar em execução para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="72a2e-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72a2e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72a2e-115">Requirements</span></span>  
 <span data-ttu-id="72a2e-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a2e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a2e-117">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="72a2e-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="72a2e-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72a2e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72a2e-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a2e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a2e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72a2e-120">See also</span></span>

- [<span data-ttu-id="72a2e-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="72a2e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="72a2e-122">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="72a2e-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
