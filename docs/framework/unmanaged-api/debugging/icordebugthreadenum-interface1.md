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
ms.openlocfilehash: 7edf103e397c6e3e1577b5ed4bc8fc0df264b843
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137989"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="617be-102">Interface ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="617be-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="617be-103">Implementa métodos ICorDebugEnum e enumera matrizes de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="617be-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="617be-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="617be-104">Methods</span></span>  
  
|<span data-ttu-id="617be-105">Método</span><span class="sxs-lookup"><span data-stu-id="617be-105">Method</span></span>|<span data-ttu-id="617be-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="617be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="617be-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="617be-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="617be-108">Obtém o número especificado de `ICorDebugThread` instâncias de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="617be-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="617be-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="617be-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="617be-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="617be-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="617be-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="617be-111">Requirements</span></span>  
 <span data-ttu-id="617be-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="617be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="617be-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="617be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="617be-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="617be-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="617be-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="617be-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="617be-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="617be-116">See also</span></span>

- [<span data-ttu-id="617be-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="617be-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
