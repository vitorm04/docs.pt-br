---
title: Método ICorDebugExceptionDebugEvent::GetFlags
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af4c7feb7076eeac6089a3255c7832c17a43469b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666957"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="6c874-102">Método ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="6c874-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="6c874-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="6c874-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c874-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c874-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c874-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c874-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="6c874-106">[out] Um ponteiro para um [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) valor que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="6c874-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c874-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c874-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c874-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6c874-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c874-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c874-109">Requirements</span></span>  
 <span data-ttu-id="6c874-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c874-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c874-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c874-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c874-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c874-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c874-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c874-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c874-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c874-114">See also</span></span>

- [<span data-ttu-id="6c874-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="6c874-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="6c874-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6c874-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
