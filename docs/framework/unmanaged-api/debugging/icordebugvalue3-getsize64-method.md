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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c0b45e08f7b88d9374023f95c6e3e22139c8949
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144762"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="8d4f8-102">Método ICorDebugValue3::GetSize64</span><span class="sxs-lookup"><span data-stu-id="8d4f8-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="8d4f8-103">Obtém o tamanho, em bytes, isso [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="8d4f8-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d4f8-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d4f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d4f8-105">Parameters</span></span>  
 <span data-ttu-id="8d4f8-106">pSize</span><span class="sxs-lookup"><span data-stu-id="8d4f8-106">pSize</span></span>  
 <span data-ttu-id="8d4f8-107">[out] Um ponteiro para o tamanho, em bytes, do objeto.</span><span class="sxs-lookup"><span data-stu-id="8d4f8-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d4f8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d4f8-108">Remarks</span></span>  
 <span data-ttu-id="8d4f8-109">Se o tipo de valor, esse é um tipo de referência, esse método retorna o tamanho do ponteiro em vez do tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="8d4f8-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="8d4f8-110">O `ICorDebugValue3::GetSize` difere do método de [icordebugvalue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) método no tipo de seu parâmetro de saída.</span><span class="sxs-lookup"><span data-stu-id="8d4f8-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="8d4f8-111">Na [icordebugvalue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), o parâmetro de saída é um `ULONG32`; na `ICorDebugValue3::GetSize`, é um `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="8d4f8-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="8d4f8-112">Isso permite que o [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface para relatar o tamanho das matrizes que exceda 2 GB.</span><span class="sxs-lookup"><span data-stu-id="8d4f8-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d4f8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d4f8-113">Requirements</span></span>  
 <span data-ttu-id="8d4f8-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d4f8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d4f8-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d4f8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d4f8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d4f8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d4f8-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d4f8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4f8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d4f8-118">See also</span></span>

- [<span data-ttu-id="8d4f8-119">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="8d4f8-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="8d4f8-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8d4f8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
