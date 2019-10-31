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
ms.openlocfilehash: c159a175ddd380015cc2dc21637c8b63fd3caea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137891"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="6169f-102">Método ICorDebugFunction::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="6169f-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="6169f-103">Obtém o token de metadados para a assinatura de variável local da função que é representada por essa instância de ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="6169f-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6169f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6169f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6169f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6169f-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="6169f-106">fora Um ponteiro para o token de `mdSignature` para a assinatura de variável local dessa função, ou `mdSignatureNil`, se essa função não tiver variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="6169f-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6169f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6169f-107">Requirements</span></span>  
 <span data-ttu-id="6169f-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6169f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6169f-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6169f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6169f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6169f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6169f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6169f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
