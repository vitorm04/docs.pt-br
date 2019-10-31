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
ms.openlocfilehash: bfd61d985eac3ab56d8a5df9474b2b1a9f641f3e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122851"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="5c774-102">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="5c774-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="5c774-103">Fornece um enumerador para uma lista de estruturas [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="5c774-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="5c774-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="5c774-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c774-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5c774-105">Methods</span></span>  
  
|<span data-ttu-id="5c774-106">Método</span><span class="sxs-lookup"><span data-stu-id="5c774-106">Method</span></span>|<span data-ttu-id="5c774-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c774-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c774-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="5c774-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="5c774-109">Enumera por meio de uma lista de estruturas [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="5c774-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c774-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c774-110">Remarks</span></span>  
 <span data-ttu-id="5c774-111">Cada estrutura de `CorDebugBlockingObject` representa um objeto que está bloqueando um thread.</span><span class="sxs-lookup"><span data-stu-id="5c774-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c774-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="5c774-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c774-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c774-113">Requirements</span></span>  
 <span data-ttu-id="5c774-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c774-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c774-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c774-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c774-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c774-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c774-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c774-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c774-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c774-118">See also</span></span>

- [<span data-ttu-id="5c774-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5c774-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5c774-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="5c774-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
