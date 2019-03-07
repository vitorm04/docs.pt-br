---
title: Método ICorDebugCode::IsIL
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78f246f90e7e3b7c9fff984092a0b5eefcba5a13
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478057"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="19dc2-102">Método ICorDebugCode::IsIL</span><span class="sxs-lookup"><span data-stu-id="19dc2-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="19dc2-103">Obtém um valor que indica se esse "ICorDebugCode" representa o código que foi compilado em Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="19dc2-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19dc2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19dc2-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19dc2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19dc2-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="19dc2-106">[out] `true` se esse `ICorDebugCode` representa o código foi compilado na MSIL; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="19dc2-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19dc2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19dc2-107">Requirements</span></span>  
 <span data-ttu-id="19dc2-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19dc2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19dc2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19dc2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19dc2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19dc2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19dc2-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19dc2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19dc2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19dc2-112">See also</span></span>

