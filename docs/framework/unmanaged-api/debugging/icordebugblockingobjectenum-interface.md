---
title: Interface ICorDebugBlockingObjectEnum
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11693416d0a3e0afe80c2356ff0a12ecea0d8d15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959308"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="f4173-102">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="f4173-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="f4173-103">Fornece um enumerador para uma lista de estruturas [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f4173-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="f4173-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f4173-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4173-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f4173-105">Methods</span></span>  
  
|<span data-ttu-id="f4173-106">Método</span><span class="sxs-lookup"><span data-stu-id="f4173-106">Method</span></span>|<span data-ttu-id="f4173-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4173-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4173-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="f4173-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="f4173-109">Enumera por meio de uma lista de estruturas [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f4173-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4173-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4173-110">Remarks</span></span>  
 <span data-ttu-id="f4173-111">Cada `CorDebugBlockingObject` estrutura representa um objeto que está bloqueando um thread.</span><span class="sxs-lookup"><span data-stu-id="f4173-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4173-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="f4173-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4173-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4173-113">Requirements</span></span>  
 <span data-ttu-id="f4173-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4173-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4173-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4173-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4173-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4173-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4173-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4173-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4173-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4173-118">See also</span></span>

- [<span data-ttu-id="f4173-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f4173-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f4173-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="f4173-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
