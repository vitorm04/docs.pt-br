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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988709"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="2ec1e-102">Método ICorDebugFunction::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="2ec1e-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="2ec1e-103">Obtém os metadados de token para a assinatura de variável local da função que é representada por esta instância de ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="2ec1e-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ec1e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ec1e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ec1e-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="2ec1e-106">[out] Um ponteiro para o `mdSignature` token para a assinatura de variável local desta função ou `mdSignatureNil`, se essa função não tiver variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="2ec1e-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec1e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ec1e-107">Requirements</span></span>  
 <span data-ttu-id="2ec1e-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec1e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec1e-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ec1e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ec1e-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ec1e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ec1e-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec1e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
