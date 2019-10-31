---
title: Interface ICorDebugValueEnum
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
ms.openlocfilehash: 4cc9849ee8cd160a33ae9c769f7b98a87eafb8dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134611"
---
# <a name="icordebugvalueenum-interface"></a><span data-ttu-id="ebfe2-102">Interface ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="ebfe2-102">ICorDebugValueEnum Interface</span></span>
<span data-ttu-id="ebfe2-103">Implementa os métodos "ICorDebugEnum" e enumera as matrizes "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="ebfe2-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugValue" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebfe2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ebfe2-104">Methods</span></span>  
  
|<span data-ttu-id="ebfe2-105">Método</span><span class="sxs-lookup"><span data-stu-id="ebfe2-105">Method</span></span>|<span data-ttu-id="ebfe2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebfe2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebfe2-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="ebfe2-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-next-method.md)|<span data-ttu-id="ebfe2-108">Obtém o número especificado de instâncias de `ICorDebugValue` da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-108">Gets the specified number of `ICorDebugValue` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebfe2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebfe2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebfe2-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebfe2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ebfe2-111">Requirements</span></span>  
 <span data-ttu-id="ebfe2-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebfe2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebfe2-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebfe2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebfe2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebfe2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebfe2-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebfe2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfe2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebfe2-116">See also</span></span>

- [<span data-ttu-id="ebfe2-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ebfe2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
