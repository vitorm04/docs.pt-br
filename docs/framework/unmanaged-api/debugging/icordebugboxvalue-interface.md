---
title: Interface ICorDebugBoxValue
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7238574334b599c7922693c7e9a476a51785491
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967315"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="1863d-102">Interface ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="1863d-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="1863d-103">Uma subclasse de "ICorDebugHeapValue" que representa um objeto de classe de valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="1863d-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1863d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1863d-104">Methods</span></span>  
  
|<span data-ttu-id="1863d-105">Método</span><span class="sxs-lookup"><span data-stu-id="1863d-105">Method</span></span>|<span data-ttu-id="1863d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1863d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1863d-107">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="1863d-107">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-getobject-method.md)|<span data-ttu-id="1863d-108">Obtém um ponteiro de interface para a instância de "ICorDebugObjectValue" demarcada.</span><span class="sxs-lookup"><span data-stu-id="1863d-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1863d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1863d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1863d-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="1863d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1863d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1863d-111">Requirements</span></span>  
 <span data-ttu-id="1863d-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1863d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1863d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1863d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1863d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1863d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1863d-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1863d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1863d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1863d-116">See also</span></span>
- [<span data-ttu-id="1863d-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1863d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
