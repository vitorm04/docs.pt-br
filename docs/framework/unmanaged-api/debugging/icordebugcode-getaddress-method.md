---
title: Método ICorDebugCode::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2de22729fd3d7a511c1105ebf810d0402bd73a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="2fbc0-102">Método ICorDebugCode::GetAddress</span><span class="sxs-lookup"><span data-stu-id="2fbc0-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="2fbc0-103">Obtém o endereço virtual relativo (RVA) do segmento de código que representa essa interface "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="2fbc0-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbc0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fbc0-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fbc0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2fbc0-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="2fbc0-106">[out] Um ponteiro para o RVA do segmento de código.</span><span class="sxs-lookup"><span data-stu-id="2fbc0-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fbc0-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fbc0-107">Requirements</span></span>  
 <span data-ttu-id="2fbc0-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fbc0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fbc0-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fbc0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fbc0-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fbc0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fbc0-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fbc0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fbc0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fbc0-112">See Also</span></span>  
 
