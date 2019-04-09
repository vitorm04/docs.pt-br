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
ms.openlocfilehash: a82606d90444c2d543065287780e42da4f8b4943
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180681"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="f51ed-102">Método ICorDebugCode::IsIL</span><span class="sxs-lookup"><span data-stu-id="f51ed-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="f51ed-103">Obtém um valor que indica se esse "ICorDebugCode" representa o código que foi compilado em Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="f51ed-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f51ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f51ed-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f51ed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f51ed-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="f51ed-106">[out] `true` se esse `ICorDebugCode` representa o código foi compilado na MSIL; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f51ed-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f51ed-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f51ed-107">Requirements</span></span>  
 <span data-ttu-id="f51ed-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f51ed-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f51ed-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f51ed-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f51ed-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f51ed-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f51ed-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f51ed-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f51ed-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f51ed-112">See also</span></span>
