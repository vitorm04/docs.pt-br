---
title: Interface ICorPublishProcess
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765be4e0ae7657d169ea561bc6a36bcf8cc11153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="93fb6-102">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="93fb6-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="93fb6-103">Fornece métodos que acessam informações a ser exibida sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="93fb6-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93fb6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="93fb6-104">Methods</span></span>  
  
|<span data-ttu-id="93fb6-105">Método</span><span class="sxs-lookup"><span data-stu-id="93fb6-105">Method</span></span>|<span data-ttu-id="93fb6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="93fb6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93fb6-107">Método EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="93fb6-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="93fb6-108">Obtém um [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instância que contém os domínios de aplicativo no processo de referenciada por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="93fb6-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="93fb6-109">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="93fb6-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="93fb6-110">Obtém o caminho completo do executável para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="93fb6-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="93fb6-111">Método GetProcessID</span><span class="sxs-lookup"><span data-stu-id="93fb6-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="93fb6-112">Obtém o identificador de sistema operacional para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="93fb6-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="93fb6-113">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="93fb6-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="93fb6-114">Obtém um valor que indica se o processo é referenciada por este `ICorPublishProcess` é conhecido para estar em execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="93fb6-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93fb6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93fb6-115">Requirements</span></span>  
 <span data-ttu-id="93fb6-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93fb6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93fb6-117">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="93fb6-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="93fb6-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93fb6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93fb6-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93fb6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fb6-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93fb6-120">See Also</span></span>  
 [<span data-ttu-id="93fb6-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="93fb6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="93fb6-122">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="93fb6-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
