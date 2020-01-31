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
ms.openlocfilehash: 3d26ddb6d89af60acf6dc1214b0423ba75e488ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791161"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="216c7-102">Método ICorDebugValue::GetSize</span><span class="sxs-lookup"><span data-stu-id="216c7-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="216c7-103">Obtém o tamanho, em bytes, deste objeto "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="216c7-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="216c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="216c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="216c7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="216c7-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="216c7-106">fora O tamanho, em bytes, deste objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="216c7-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="216c7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="216c7-107">Remarks</span></span>  
 <span data-ttu-id="216c7-108">Se o tipo do valor for um tipo de referência, esse método retornará o tamanho do ponteiro em vez do tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="216c7-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="216c7-109">O método `ICorDebugValue::GetSize` retorna `COR_E_OVERFLOW` para objetos com mais de 4 GB em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="216c7-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="216c7-110">Use o método [ICorDebugValue3:: GetSize64](icordebugvalue3-getsize64-method.md) em vez de objetos com mais de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="216c7-110">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="216c7-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="216c7-111">Requirements</span></span>  
 <span data-ttu-id="216c7-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="216c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="216c7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="216c7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="216c7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="216c7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="216c7-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="216c7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216c7-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="216c7-116">See also</span></span>

- [<span data-ttu-id="216c7-117">Método GetSize64</span><span class="sxs-lookup"><span data-stu-id="216c7-117">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
