---
title: "Método ICorDebugValue::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf99b35d45c1dda8f187e0206e068c128f347d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="215f3-102">Método ICorDebugValue::GetSize</span><span class="sxs-lookup"><span data-stu-id="215f3-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="215f3-103">Obtém o tamanho, em bytes, do objeto "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="215f3-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="215f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="215f3-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="215f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="215f3-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="215f3-106">[out] O tamanho, em bytes, do objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="215f3-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="215f3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="215f3-107">Remarks</span></span>  
 <span data-ttu-id="215f3-108">Se o tipo do valor é um tipo de referência, esse método retorna o tamanho do ponteiro em vez do tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="215f3-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="215f3-109">O `ICorDebugValue::GetSize` método retorna `COR_E_OVERFLOW` para objetos que são maiores do que 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="215f3-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="215f3-110">Use o [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) método em vez disso, para objetos que são maiores do que 4 GB.</span><span class="sxs-lookup"><span data-stu-id="215f3-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="215f3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="215f3-111">Requirements</span></span>  
 <span data-ttu-id="215f3-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="215f3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="215f3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="215f3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="215f3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="215f3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="215f3-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="215f3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215f3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="215f3-116">See Also</span></span>  
    
 [<span data-ttu-id="215f3-117">Método GetSize64</span><span class="sxs-lookup"><span data-stu-id="215f3-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
