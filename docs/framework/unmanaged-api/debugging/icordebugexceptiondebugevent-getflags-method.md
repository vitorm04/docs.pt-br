---
title: 'Método ICorDebugExceptionDebugEvent:: GetFlags'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 6c330ce5b375daacdf257eda16fd5e34012f5d69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084760"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="fcb12-102">Método ICorDebugExceptionDebugEvent:: GetFlags</span><span class="sxs-lookup"><span data-stu-id="fcb12-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="fcb12-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="fcb12-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcb12-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcb12-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fcb12-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="fcb12-106">fora Um ponteiro para um valor [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="fcb12-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcb12-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcb12-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcb12-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fcb12-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcb12-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcb12-109">Requirements</span></span>  
 <span data-ttu-id="fcb12-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcb12-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcb12-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcb12-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcb12-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcb12-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcb12-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcb12-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb12-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcb12-114">See also</span></span>

- [<span data-ttu-id="fcb12-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="fcb12-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="fcb12-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fcb12-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
