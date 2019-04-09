---
title: Método ICorDebugCode::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 678b7fbd595b1238b7025c22b0ed80b02ed4becd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085669"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="95b03-102">Método ICorDebugCode::GetSize</span><span class="sxs-lookup"><span data-stu-id="95b03-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="95b03-103">Obtém o tamanho, em bytes, do código binário representado por esse "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="95b03-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b03-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95b03-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95b03-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95b03-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="95b03-106">[out] Um ponteiro para o tamanho, em bytes, do binário de que este código `ICorDebugCode` objeto representa.</span><span class="sxs-lookup"><span data-stu-id="95b03-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b03-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95b03-107">Requirements</span></span>  
 <span data-ttu-id="95b03-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95b03-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b03-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95b03-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95b03-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95b03-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="95b03-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="95b03-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95b03-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95b03-112">See also</span></span>
