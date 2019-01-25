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
ms.openlocfilehash: 3a9a43735ec80821c2380b824bfced99113cf08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651084"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="951de-102">Método ICorDebugCode::GetSize</span><span class="sxs-lookup"><span data-stu-id="951de-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="951de-103">Obtém o tamanho, em bytes, do código binário representado por esse "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="951de-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="951de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="951de-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="951de-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="951de-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="951de-106">[out] Um ponteiro para o tamanho, em bytes, do binário de que este código `ICorDebugCode` objeto representa.</span><span class="sxs-lookup"><span data-stu-id="951de-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="951de-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="951de-107">Requirements</span></span>  
 <span data-ttu-id="951de-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="951de-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="951de-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="951de-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="951de-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="951de-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="951de-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="951de-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951de-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="951de-112">See also</span></span>

