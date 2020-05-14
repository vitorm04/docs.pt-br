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
ms.openlocfilehash: 6eb26de83a6cdce47477e6cb3dffd6a94d889975
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397018"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="8ee5f-102">Método ICorDebugValue3::GetSize64</span><span class="sxs-lookup"><span data-stu-id="8ee5f-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="8ee5f-103">Obtém o tamanho, em bytes, deste objeto [ICorDebugValue3](icordebugvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8ee5f-103">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ee5f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ee5f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ee5f-105">Parameters</span></span>  
 <span data-ttu-id="8ee5f-106">pSize</span><span class="sxs-lookup"><span data-stu-id="8ee5f-106">pSize</span></span>  
 <span data-ttu-id="8ee5f-107">fora Um ponteiro para o tamanho, em bytes, deste objeto.</span><span class="sxs-lookup"><span data-stu-id="8ee5f-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ee5f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ee5f-108">Remarks</span></span>  
 <span data-ttu-id="8ee5f-109">Se o tipo desse valor for um tipo de referência, esse método retornará o tamanho do ponteiro em vez do tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="8ee5f-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="8ee5f-110">O `ICorDebugValue3::GetSize` método difere do método [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) no tipo de seu parâmetro de saída.</span><span class="sxs-lookup"><span data-stu-id="8ee5f-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="8ee5f-111">Em [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md), o parâmetro de saída é a `ULONG32` ; in `ICorDebugValue3::GetSize` , é um `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="8ee5f-111">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="8ee5f-112">Isso permite que a interface [ICorDebugValue3](icordebugvalue3-interface.md) relate o tamanho das matrizes que excedem 2GB.</span><span class="sxs-lookup"><span data-stu-id="8ee5f-112">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee5f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ee5f-113">Requirements</span></span>  
 <span data-ttu-id="8ee5f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee5f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee5f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ee5f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ee5f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ee5f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ee5f-117">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee5f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee5f-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="8ee5f-118">See also</span></span>

- [<span data-ttu-id="8ee5f-119">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="8ee5f-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="8ee5f-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8ee5f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
