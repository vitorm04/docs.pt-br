---
title: ICorDebugObjectEnum Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3674643d5590c320bddd5a0e6f1f95814e07ecf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420196"
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="c1e6b-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="c1e6b-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="c1e6b-103">Implementa métodos ICorDebugEnum e enumera as matrizes de objetos por seus endereços virtuais relativos (RVAs).</span><span class="sxs-lookup"><span data-stu-id="c1e6b-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1e6b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c1e6b-104">Methods</span></span>  
  
|<span data-ttu-id="c1e6b-105">Método</span><span class="sxs-lookup"><span data-stu-id="c1e6b-105">Method</span></span>|<span data-ttu-id="c1e6b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1e6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1e6b-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="c1e6b-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="c1e6b-108">Obtém os RVAs do número especificado de objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="c1e6b-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1e6b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1e6b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e6b-110">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="c1e6b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1e6b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1e6b-111">Requirements</span></span>  
 <span data-ttu-id="c1e6b-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1e6b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1e6b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1e6b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1e6b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1e6b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1e6b-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1e6b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e6b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1e6b-116">See Also</span></span>  
 [<span data-ttu-id="c1e6b-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c1e6b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
