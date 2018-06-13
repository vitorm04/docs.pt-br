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
ms.openlocfilehash: f22d9d86e2b943a8825e1ec271a401b03f73fb6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407008"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="ea657-102">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="ea657-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="ea657-103">Fornece um enumerador para obter uma lista de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="ea657-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="ea657-104">Esta interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="ea657-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea657-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ea657-105">Methods</span></span>  
  
|<span data-ttu-id="ea657-106">Método</span><span class="sxs-lookup"><span data-stu-id="ea657-106">Method</span></span>|<span data-ttu-id="ea657-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea657-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea657-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="ea657-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="ea657-109">Enumera uma lista de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="ea657-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea657-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea657-110">Remarks</span></span>  
 <span data-ttu-id="ea657-111">Cada `CorDebugBlockingObject` estrutura representa um objeto que está bloqueando um thread.</span><span class="sxs-lookup"><span data-stu-id="ea657-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea657-112">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="ea657-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea657-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea657-113">Requirements</span></span>  
 <span data-ttu-id="ea657-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea657-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea657-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea657-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea657-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea657-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea657-117">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea657-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea657-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea657-118">See Also</span></span>  
 [<span data-ttu-id="ea657-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ea657-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ea657-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="ea657-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
