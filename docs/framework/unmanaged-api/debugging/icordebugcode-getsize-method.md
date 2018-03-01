---
title: "Método ICorDebugCode::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69c28cba90c8ebef1b178263c8edac2cb5914c0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="00dff-102">Método ICorDebugCode::GetSize</span><span class="sxs-lookup"><span data-stu-id="00dff-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="00dff-103">Obtém o tamanho, em bytes, do código binário representado por esse "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="00dff-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00dff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00dff-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00dff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00dff-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="00dff-106">[out] Um ponteiro para o tamanho, em bytes, do binário de código que este `ICorDebugCode` objeto representa.</span><span class="sxs-lookup"><span data-stu-id="00dff-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00dff-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00dff-107">Requirements</span></span>  
 <span data-ttu-id="00dff-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00dff-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00dff-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00dff-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00dff-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00dff-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00dff-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00dff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00dff-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00dff-112">See Also</span></span>  
 
