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
ms.openlocfilehash: 04f6a088c5bbe96e3909ba600aa8ffab937abe2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140405"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="bdc66-102">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="bdc66-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="bdc66-103">Fornece métodos que acessam informações a serem exibidas sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="bdc66-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdc66-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bdc66-104">Methods</span></span>  
  
|<span data-ttu-id="bdc66-105">Método</span><span class="sxs-lookup"><span data-stu-id="bdc66-105">Method</span></span>|<span data-ttu-id="bdc66-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc66-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdc66-107">Método EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="bdc66-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="bdc66-108">Obtém uma instância de [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) que contém os domínios de aplicativo no processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="bdc66-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="bdc66-109">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="bdc66-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="bdc66-110">Obtém o caminho completo do executável para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="bdc66-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="bdc66-111">Método GetProcessID</span><span class="sxs-lookup"><span data-stu-id="bdc66-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="bdc66-112">Obtém o identificador do sistema operacional para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="bdc66-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="bdc66-113">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="bdc66-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="bdc66-114">Obtém um valor que indica se o processo referenciado por essa `ICorPublishProcess` é conhecido por estar executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bdc66-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdc66-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdc66-115">Requirements</span></span>  
 <span data-ttu-id="bdc66-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdc66-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdc66-117">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="bdc66-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bdc66-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdc66-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdc66-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc66-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc66-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdc66-120">See also</span></span>

- [<span data-ttu-id="bdc66-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="bdc66-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bdc66-122">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="bdc66-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
