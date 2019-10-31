---
title: Interface ICorPublish
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121764"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="7e738-102">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="7e738-102">ICorPublish Interface</span></span>
<span data-ttu-id="7e738-103">O serve como interface geral para publicar informações sobre processos e informações sobre os domínios de aplicativo nesses processos.</span><span class="sxs-lookup"><span data-stu-id="7e738-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e738-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7e738-104">Methods</span></span>  
  
|<span data-ttu-id="7e738-105">Método</span><span class="sxs-lookup"><span data-stu-id="7e738-105">Method</span></span>|<span data-ttu-id="7e738-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e738-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e738-107">Método EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="7e738-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="7e738-108">Obtém uma instância de [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) que contém os processos gerenciados em execução neste computador.</span><span class="sxs-lookup"><span data-stu-id="7e738-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="7e738-109">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="7e738-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="7e738-110">Obtém uma instância de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="7e738-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e738-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e738-111">Requirements</span></span>  
 <span data-ttu-id="7e738-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e738-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e738-113">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="7e738-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7e738-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e738-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e738-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e738-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e738-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e738-116">See also</span></span>

- [<span data-ttu-id="7e738-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7e738-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7e738-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="7e738-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
