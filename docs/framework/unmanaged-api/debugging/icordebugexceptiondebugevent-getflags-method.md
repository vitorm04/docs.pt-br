---
title: 'Método ICorDebugExceptionDebugEvent:: GetFlags'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782914"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="0e0bb-102">Método ICorDebugExceptionDebugEvent:: GetFlags</span><span class="sxs-lookup"><span data-stu-id="0e0bb-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="0e0bb-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="0e0bb-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e0bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e0bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e0bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e0bb-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="0e0bb-106">fora Um ponteiro para um valor [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="0e0bb-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e0bb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e0bb-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e0bb-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0e0bb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e0bb-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0e0bb-109">Requirements</span></span>  
 <span data-ttu-id="0e0bb-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e0bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e0bb-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e0bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e0bb-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e0bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e0bb-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e0bb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0bb-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="0e0bb-114">See also</span></span>

- [<span data-ttu-id="0e0bb-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="0e0bb-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="0e0bb-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0e0bb-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
