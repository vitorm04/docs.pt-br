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
ms.openlocfilehash: fb0030a25dd48ab4236ec2b51891e0ac41aac902
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612613"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="61d4c-102">Método ICorDebugValue::GetSize</span><span class="sxs-lookup"><span data-stu-id="61d4c-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="61d4c-103">Obtém o tamanho, em bytes, do objeto "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="61d4c-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61d4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61d4c-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61d4c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61d4c-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="61d4c-106">[out] O tamanho, em bytes, do objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="61d4c-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61d4c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="61d4c-107">Remarks</span></span>  
 <span data-ttu-id="61d4c-108">Se o tipo de valor é um tipo de referência, esse método retorna o tamanho do ponteiro em vez do tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="61d4c-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="61d4c-109">O `ICorDebugValue::GetSize` retorno do método `COR_E_OVERFLOW` para objetos que são maiores do que 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="61d4c-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="61d4c-110">Use o [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) método em vez disso, para objetos que são maiores do que 4 GB.</span><span class="sxs-lookup"><span data-stu-id="61d4c-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61d4c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61d4c-111">Requirements</span></span>  
 <span data-ttu-id="61d4c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61d4c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61d4c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61d4c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61d4c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61d4c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61d4c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61d4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d4c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61d4c-116">See also</span></span>

- [<span data-ttu-id="61d4c-117">Método GetSize64</span><span class="sxs-lookup"><span data-stu-id="61d4c-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
