---
title: 'Método ICorDebugExceptionDebugEvent:: GetFlags'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 5793d939c8497ef842f614048707f69faa8ac568
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976038"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="2459c-102">Método ICorDebugExceptionDebugEvent:: GetFlags</span><span class="sxs-lookup"><span data-stu-id="2459c-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="2459c-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="2459c-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2459c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2459c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2459c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2459c-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="2459c-106">fora Um ponteiro para um valor [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="2459c-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2459c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2459c-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2459c-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2459c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2459c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2459c-109">Requirements</span></span>  
 <span data-ttu-id="2459c-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2459c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2459c-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2459c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2459c-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2459c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2459c-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2459c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2459c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2459c-114">See also</span></span>

- [<span data-ttu-id="2459c-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="2459c-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="2459c-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2459c-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
