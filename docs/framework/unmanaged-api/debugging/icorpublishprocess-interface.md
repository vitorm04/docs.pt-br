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
ms.openlocfilehash: cb62da277ff13bea33969bb9c728cac5d5a15554
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="7470d-102">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="7470d-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="7470d-103">Fornece métodos que acessam informações a ser exibida sobre um processo.</span><span class="sxs-lookup"><span data-stu-id="7470d-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7470d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7470d-104">Methods</span></span>  
  
|<span data-ttu-id="7470d-105">Método</span><span class="sxs-lookup"><span data-stu-id="7470d-105">Method</span></span>|<span data-ttu-id="7470d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7470d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7470d-107">Método EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="7470d-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="7470d-108">Obtém um [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instância que contém os domínios de aplicativo no processo de referenciada por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="7470d-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="7470d-109">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="7470d-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="7470d-110">Obtém o caminho completo do executável para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="7470d-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="7470d-111">Método GetProcessID</span><span class="sxs-lookup"><span data-stu-id="7470d-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="7470d-112">Obtém o identificador de sistema operacional para o processo referenciado por este `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="7470d-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="7470d-113">Método IsManaged</span><span class="sxs-lookup"><span data-stu-id="7470d-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="7470d-114">Obtém um valor que indica se o processo é referenciada por este `ICorPublishProcess` é conhecido para estar em execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7470d-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7470d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7470d-115">Requirements</span></span>  
 <span data-ttu-id="7470d-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7470d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7470d-117">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7470d-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7470d-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7470d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7470d-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7470d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7470d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7470d-120">See Also</span></span>  
 [<span data-ttu-id="7470d-121">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="7470d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7470d-122">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="7470d-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
