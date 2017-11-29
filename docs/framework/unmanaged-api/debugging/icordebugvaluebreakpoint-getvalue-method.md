---
title: "Método ICorDebugValueBreakpoint::GetValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68f918b74a5a4abd9820071b4a4772f9b57b9c88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="759f4-102">Método ICorDebugValueBreakpoint::GetValue</span><span class="sxs-lookup"><span data-stu-id="759f4-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="759f4-103">Obtém um ponteiro de interface para um objeto de "ICorDebugValue" que representa o valor do objeto no qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="759f4-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="759f4-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="759f4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="759f4-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="759f4-106">[out] Um ponteiro para o endereço de uma `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="759f4-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="759f4-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="759f4-107">Requirements</span></span>  
 <span data-ttu-id="759f4-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="759f4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="759f4-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="759f4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="759f4-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="759f4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="759f4-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="759f4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759f4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="759f4-112">See Also</span></span>  
 
