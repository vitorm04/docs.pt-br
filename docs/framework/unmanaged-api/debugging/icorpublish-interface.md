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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7581d68f5c2b575403ddc84d06147f012e7ab39e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993559"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="3de6b-102">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="3de6b-102">ICorPublish Interface</span></span>
<span data-ttu-id="3de6b-103">Serve como a interface geral para a publicação de informações sobre os processos e informações sobre os domínios de aplicativo desses processos.</span><span class="sxs-lookup"><span data-stu-id="3de6b-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3de6b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3de6b-104">Methods</span></span>  
  
|<span data-ttu-id="3de6b-105">Método</span><span class="sxs-lookup"><span data-stu-id="3de6b-105">Method</span></span>|<span data-ttu-id="3de6b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3de6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3de6b-107">Método EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="3de6b-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="3de6b-108">Obtém uma [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instância que contém os processos gerenciados em execução neste computador.</span><span class="sxs-lookup"><span data-stu-id="3de6b-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="3de6b-109">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="3de6b-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="3de6b-110">Obtém uma [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instância que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="3de6b-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3de6b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3de6b-111">Requirements</span></span>  
 <span data-ttu-id="3de6b-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de6b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de6b-113">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3de6b-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3de6b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3de6b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3de6b-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de6b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de6b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3de6b-116">See also</span></span>

- [<span data-ttu-id="3de6b-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3de6b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3de6b-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="3de6b-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
