---
title: Método ICorDebugFunction::GetLocalVarSigToken
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e03e7a965bc923d91cb0c83a9ea8ea5899da63a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754664"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="369cd-102">Método ICorDebugFunction::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="369cd-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="369cd-103">Obtém os metadados de token para a assinatura de variável local da função que é representada por esta instância de ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="369cd-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="369cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="369cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="369cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="369cd-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="369cd-106">[out] Um ponteiro para o `mdSignature` token para a assinatura de variável local desta função ou `mdSignatureNil`, se essa função não tiver variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="369cd-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="369cd-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="369cd-107">Requirements</span></span>  
 <span data-ttu-id="369cd-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="369cd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="369cd-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="369cd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="369cd-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="369cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="369cd-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="369cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
