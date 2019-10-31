---
title: Interface ICorDebugFrameEnum
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
ms.openlocfilehash: 3a33d25ee13e12a2612d0132da1dc84c24f2f95b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090534"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="a0321-102">Interface ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="a0321-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="a0321-103">Implementa métodos ICorDebugEnum e enumera matrizes ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="a0321-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0321-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a0321-104">Methods</span></span>  
  
|<span data-ttu-id="a0321-105">Método</span><span class="sxs-lookup"><span data-stu-id="a0321-105">Method</span></span>|<span data-ttu-id="a0321-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0321-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0321-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="a0321-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="a0321-108">Obtém o número especificado de instâncias de `ICorDebugFrame` da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="a0321-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0321-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0321-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0321-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="a0321-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0321-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0321-111">Requirements</span></span>  
 <span data-ttu-id="a0321-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0321-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0321-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0321-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0321-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0321-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0321-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0321-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0321-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0321-116">See also</span></span>

- [<span data-ttu-id="a0321-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a0321-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
