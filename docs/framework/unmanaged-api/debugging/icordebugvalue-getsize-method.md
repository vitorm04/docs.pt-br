---
title: Método ICorDebugValue::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0023b8ad815b9204ed56791698c7242dfe90bec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="afc1d-102">Método ICorDebugValue::GetSize</span><span class="sxs-lookup"><span data-stu-id="afc1d-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="afc1d-103">Obtém o tamanho, em bytes, do objeto "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="afc1d-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc1d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="afc1d-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afc1d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="afc1d-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="afc1d-106">[out] O tamanho, em bytes, do objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="afc1d-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afc1d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="afc1d-107">Remarks</span></span>  
 <span data-ttu-id="afc1d-108">Se o tipo do valor é um tipo de referência, esse método retorna o tamanho do ponteiro em vez do tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="afc1d-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="afc1d-109">O `ICorDebugValue::GetSize` método retorna `COR_E_OVERFLOW` para objetos que são maiores do que 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="afc1d-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="afc1d-110">Use o [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) método em vez disso, para objetos que são maiores do que 4 GB.</span><span class="sxs-lookup"><span data-stu-id="afc1d-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afc1d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="afc1d-111">Requirements</span></span>  
 <span data-ttu-id="afc1d-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afc1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afc1d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afc1d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afc1d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afc1d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afc1d-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afc1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc1d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afc1d-116">See Also</span></span>  
    
 [<span data-ttu-id="afc1d-117">Método GetSize64</span><span class="sxs-lookup"><span data-stu-id="afc1d-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
