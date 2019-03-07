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
ms.openlocfilehash: a682999c888a93cef94162a8179673c862dc43ce
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476640"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="a75b7-102">Método ICorDebugFunction::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="a75b7-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="a75b7-103">Obtém os metadados de token para a assinatura de variável local da função que é representada por esta instância de ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="a75b7-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a75b7-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a75b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a75b7-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="a75b7-106">[out] Um ponteiro para o `mdSignature` token para a assinatura de variável local desta função ou `mdSignatureNil`, se essa função não tiver variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="a75b7-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75b7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a75b7-107">Requirements</span></span>  
 <span data-ttu-id="a75b7-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75b7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75b7-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a75b7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a75b7-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a75b7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a75b7-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a75b7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
