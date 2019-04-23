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
ms.openlocfilehash: 11ced90b88f083eb69b06d197d64a8ef4252f9d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141486"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="6f159-102">Método ICorDebugCode::GetAddress</span><span class="sxs-lookup"><span data-stu-id="6f159-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="6f159-103">Obtém o endereço virtual relativo (RVA) ou o segmento de código que representa essa interface "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="6f159-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f159-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f159-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f159-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f159-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="6f159-106">[out] Um ponteiro para o RVA do segmento de código.</span><span class="sxs-lookup"><span data-stu-id="6f159-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f159-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f159-107">Requirements</span></span>  
 <span data-ttu-id="6f159-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f159-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f159-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f159-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f159-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f159-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f159-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f159-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f159-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f159-112">See also</span></span>
