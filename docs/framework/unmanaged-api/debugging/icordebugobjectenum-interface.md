---
title: ICorDebugObjectEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum
helpviewer_keywords: ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f2610600d102177c80821c78e7d07f8aed1b6de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="c783d-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="c783d-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="c783d-103">Implementa métodos ICorDebugEnum e enumera as matrizes de objetos por seus endereços virtuais relativos (RVAs).</span><span class="sxs-lookup"><span data-stu-id="c783d-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c783d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c783d-104">Methods</span></span>  
  
|<span data-ttu-id="c783d-105">Método</span><span class="sxs-lookup"><span data-stu-id="c783d-105">Method</span></span>|<span data-ttu-id="c783d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c783d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c783d-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="c783d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="c783d-108">Obtém os RVAs do número especificado de objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="c783d-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c783d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c783d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c783d-110">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="c783d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c783d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c783d-111">Requirements</span></span>  
 <span data-ttu-id="c783d-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c783d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c783d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c783d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c783d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c783d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c783d-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c783d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c783d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c783d-116">See Also</span></span>  
 [<span data-ttu-id="c783d-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c783d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
