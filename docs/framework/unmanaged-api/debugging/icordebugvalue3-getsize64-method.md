---
title: Método ICorDebugValue3::GetSize64
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 72a1b6fdc40f3169500d8cf3b3028315106ecc69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140235"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="21bc0-102">Método ICorDebugValue3::GetSize64</span><span class="sxs-lookup"><span data-stu-id="21bc0-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="21bc0-103">Obtém o tamanho, em bytes, deste objeto [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="21bc0-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21bc0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21bc0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21bc0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21bc0-105">Parameters</span></span>  
 <span data-ttu-id="21bc0-106">pSize</span><span class="sxs-lookup"><span data-stu-id="21bc0-106">pSize</span></span>  
 <span data-ttu-id="21bc0-107">fora Um ponteiro para o tamanho, em bytes, deste objeto.</span><span class="sxs-lookup"><span data-stu-id="21bc0-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21bc0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="21bc0-108">Remarks</span></span>  
 <span data-ttu-id="21bc0-109">Se o tipo desse valor for um tipo de referência, esse método retornará o tamanho do ponteiro em vez do tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="21bc0-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="21bc0-110">O método `ICorDebugValue3::GetSize` difere do método [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) no tipo de seu parâmetro de saída.</span><span class="sxs-lookup"><span data-stu-id="21bc0-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="21bc0-111">Em [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), o parâmetro de saída é um `ULONG32`; em `ICorDebugValue3::GetSize`, é um `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="21bc0-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="21bc0-112">Isso permite que a interface [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) relate o tamanho das matrizes que excedem 2GB.</span><span class="sxs-lookup"><span data-stu-id="21bc0-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21bc0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21bc0-113">Requirements</span></span>  
 <span data-ttu-id="21bc0-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21bc0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21bc0-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21bc0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21bc0-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21bc0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21bc0-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21bc0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bc0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21bc0-118">See also</span></span>

- [<span data-ttu-id="21bc0-119">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="21bc0-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="21bc0-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="21bc0-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
