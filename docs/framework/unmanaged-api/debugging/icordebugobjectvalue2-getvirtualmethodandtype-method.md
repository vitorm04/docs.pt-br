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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af07df53c094654ab86f5e6531fd78124aded988
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630886"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="1c0d3-102">Método ICorDebugObjectValue2::GetVirtualMethodAndType</span><span class="sxs-lookup"><span data-stu-id="1c0d3-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="1c0d3-103">Este método ainda não foi implementado.</span><span class="sxs-lookup"><span data-stu-id="1c0d3-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c0d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c0d3-104">Syntax</span></span>  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1c0d3-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c0d3-105">Remarks</span></span>  
 <span data-ttu-id="1c0d3-106">Obtém a interface ponteiros para as instâncias de "ICorDebugFunction" e "ICorDebugType" que representam o método de mais derivado e o tipo para a referência de membro especificado.</span><span class="sxs-lookup"><span data-stu-id="1c0d3-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0d3-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c0d3-107">See also</span></span>


