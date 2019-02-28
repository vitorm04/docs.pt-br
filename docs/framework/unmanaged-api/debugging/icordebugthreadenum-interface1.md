---
title: Interface ICorDebugThreadEnum
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b620357967d5d22148f64a3258fbb8dc52361d86
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981719"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="fd619-102">Interface ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="fd619-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="fd619-103">Implementa métodos ICorDebugEnum e enumera matrizes de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="fd619-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd619-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fd619-104">Methods</span></span>  
  
|<span data-ttu-id="fd619-105">Método</span><span class="sxs-lookup"><span data-stu-id="fd619-105">Method</span></span>|<span data-ttu-id="fd619-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd619-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd619-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="fd619-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="fd619-108">Obtém o número especificado de `ICorDebugThread` instâncias de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="fd619-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd619-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd619-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd619-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="fd619-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd619-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd619-111">Requirements</span></span>  
 <span data-ttu-id="fd619-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd619-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd619-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd619-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd619-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd619-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd619-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd619-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd619-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd619-116">See also</span></span>
- [<span data-ttu-id="fd619-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fd619-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
