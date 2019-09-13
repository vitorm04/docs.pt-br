---
title: 'Método ICorDebugExceptionDebugEvent:: GetFlags'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb92deee21c63c935454ff7c7c4e70be6f770436
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895001"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="4b1c9-102">Método ICorDebugExceptionDebugEvent:: GetFlags</span><span class="sxs-lookup"><span data-stu-id="4b1c9-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="4b1c9-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="4b1c9-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b1c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b1c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b1c9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b1c9-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="4b1c9-106">fora Um ponteiro para um valor [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="4b1c9-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b1c9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b1c9-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b1c9-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4b1c9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b1c9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b1c9-109">Requirements</span></span>  
 <span data-ttu-id="4b1c9-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b1c9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b1c9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b1c9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b1c9-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b1c9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b1c9-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b1c9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1c9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b1c9-114">See also</span></span>

- [<span data-ttu-id="4b1c9-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4b1c9-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="4b1c9-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4b1c9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
