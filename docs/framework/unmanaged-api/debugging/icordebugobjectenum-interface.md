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
ms.openlocfilehash: 3a9f10301db488e4ca68ce5fdaf0ba767053d7d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546995"
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="33110-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="33110-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="33110-103">Implementa métodos ICorDebugEnum e enumera matrizes de objetos por endereços virtuais (relacionados RVAs).</span><span class="sxs-lookup"><span data-stu-id="33110-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33110-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="33110-104">Methods</span></span>  
  
|<span data-ttu-id="33110-105">Método</span><span class="sxs-lookup"><span data-stu-id="33110-105">Method</span></span>|<span data-ttu-id="33110-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="33110-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33110-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="33110-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="33110-108">Obtém os RVAs do número especificado de objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="33110-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33110-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="33110-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33110-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="33110-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33110-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33110-111">Requirements</span></span>  
 <span data-ttu-id="33110-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33110-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33110-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33110-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33110-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33110-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33110-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33110-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33110-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33110-116">See also</span></span>
- [<span data-ttu-id="33110-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="33110-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
