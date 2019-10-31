---
title: Método ICorDebugObjectValue2::GetVirtualMethodAndType
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
ms.openlocfilehash: 17cb3440c5b33d461b1624608ce115e1942d6beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129711"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="2922f-102">Método ICorDebugObjectValue2::GetVirtualMethodAndType</span><span class="sxs-lookup"><span data-stu-id="2922f-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="2922f-103">Este método ainda não foi implementado.</span><span class="sxs-lookup"><span data-stu-id="2922f-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2922f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2922f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="2922f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2922f-105">Remarks</span></span>  
 <span data-ttu-id="2922f-106">Obtém ponteiros de interface para as instâncias "ICorDebugFunction" e "ICorDebugType" que representam o método e tipo mais derivados para a referência de membro especificada.</span><span class="sxs-lookup"><span data-stu-id="2922f-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2922f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2922f-107">See also</span></span>
