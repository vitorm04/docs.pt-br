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
ms.openlocfilehash: 5a23d21d0ed8c6a6a226d5e58eafb7bde65a4896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645429"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="c5eab-102">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="c5eab-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="c5eab-103">Fornece um enumerador para uma lista dos [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="c5eab-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="c5eab-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="c5eab-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5eab-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5eab-105">Methods</span></span>  
  
|<span data-ttu-id="c5eab-106">Método</span><span class="sxs-lookup"><span data-stu-id="c5eab-106">Method</span></span>|<span data-ttu-id="c5eab-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5eab-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5eab-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="c5eab-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="c5eab-109">Enumera uma lista dos [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="c5eab-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5eab-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5eab-110">Remarks</span></span>  
 <span data-ttu-id="c5eab-111">Cada `CorDebugBlockingObject` estrutura representa um objeto que está bloqueando um thread.</span><span class="sxs-lookup"><span data-stu-id="c5eab-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5eab-112">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="c5eab-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5eab-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5eab-113">Requirements</span></span>  
 <span data-ttu-id="c5eab-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5eab-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5eab-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5eab-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5eab-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5eab-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5eab-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5eab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5eab-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5eab-118">See also</span></span>

- [<span data-ttu-id="c5eab-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c5eab-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c5eab-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="c5eab-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
