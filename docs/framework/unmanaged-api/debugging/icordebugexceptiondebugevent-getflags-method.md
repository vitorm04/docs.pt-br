---
title: 'Método ICorDebugExceptionDebugEvent:: GetFlags'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbe6f6a2953c3f815606e881b86a693b7a0e6ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951894"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="ded5a-102">Método ICorDebugExceptionDebugEvent:: GetFlags</span><span class="sxs-lookup"><span data-stu-id="ded5a-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="ded5a-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="ded5a-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded5a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ded5a-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ded5a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ded5a-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="ded5a-106">fora Um ponteiro para um valor [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="ded5a-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ded5a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ded5a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ded5a-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ded5a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded5a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ded5a-109">Requirements</span></span>  
 <span data-ttu-id="ded5a-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ded5a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded5a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ded5a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ded5a-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ded5a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ded5a-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ded5a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded5a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ded5a-114">See also</span></span>

- [<span data-ttu-id="ded5a-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ded5a-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="ded5a-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ded5a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
