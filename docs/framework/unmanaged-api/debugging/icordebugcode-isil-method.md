---
title: "Método ICorDebugCode::IsIL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.IsIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07b0490e322c70763a37b86fbb02e2f8b99bd768
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="cfee3-102">Método ICorDebugCode::IsIL</span><span class="sxs-lookup"><span data-stu-id="cfee3-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="cfee3-103">Obtém um valor que indica se este "ICorDebugCode" representa o código que foi compilado no Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="cfee3-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfee3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfee3-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfee3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfee3-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="cfee3-106">[out] `true` se este `ICorDebugCode` representa o código que foi compilado na MSIL; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="cfee3-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfee3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfee3-107">Requirements</span></span>  
 <span data-ttu-id="cfee3-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfee3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfee3-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfee3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfee3-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfee3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfee3-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfee3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfee3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfee3-112">See Also</span></span>  
 
