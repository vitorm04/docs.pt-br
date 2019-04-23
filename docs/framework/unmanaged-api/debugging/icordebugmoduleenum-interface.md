---
title: Interface ICorDebugModuleEnum
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26efb3e43642b6d1fd10b084c2b321609c89d89b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146504"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="fcbc1-102">Interface ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="fcbc1-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="fcbc1-103">Implementa métodos ICorDebugEnum e enumera matrizes de ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="fcbc1-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcbc1-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fcbc1-104">Methods</span></span>  
  
|<span data-ttu-id="fcbc1-105">Método</span><span class="sxs-lookup"><span data-stu-id="fcbc1-105">Method</span></span>|<span data-ttu-id="fcbc1-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcbc1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcbc1-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="fcbc1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="fcbc1-108">Obtém o número especificado de `ICorDebugModule` instâncias de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="fcbc1-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcbc1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcbc1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcbc1-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="fcbc1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbc1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcbc1-111">Requirements</span></span>  
 <span data-ttu-id="fcbc1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcbc1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbc1-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcbc1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcbc1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcbc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcbc1-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbc1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbc1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcbc1-116">See also</span></span>

- [<span data-ttu-id="fcbc1-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fcbc1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
