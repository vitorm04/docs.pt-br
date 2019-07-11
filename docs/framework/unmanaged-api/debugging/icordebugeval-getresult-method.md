---
title: Método ICorDebugEval::GetResult
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b12ba5ad5c85643d1f4c91585cf7abca210d22bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752947"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="3850c-102">Método ICorDebugEval::GetResult</span><span class="sxs-lookup"><span data-stu-id="3850c-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="3850c-103">Obtém os resultados da avaliação.</span><span class="sxs-lookup"><span data-stu-id="3850c-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3850c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3850c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3850c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3850c-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="3850c-106">[out] Ponteiro para o endereço de um objeto ICorDebugValue que representa os resultados dessa avaliação, se a avaliação for concluída normalmente.</span><span class="sxs-lookup"><span data-stu-id="3850c-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3850c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3850c-107">Remarks</span></span>  
 <span data-ttu-id="3850c-108">O `GetResult` método é válido somente depois que a avaliação é concluída.</span><span class="sxs-lookup"><span data-stu-id="3850c-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="3850c-109">Se a avaliação for concluída normalmente, `ppResult` Especifica os resultados.</span><span class="sxs-lookup"><span data-stu-id="3850c-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="3850c-110">Se ele termina com uma exceção, o resultado é a exceção lançada.</span><span class="sxs-lookup"><span data-stu-id="3850c-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="3850c-111">Se a avaliação foi para um novo objeto, o resultado é a referência ao novo objeto.</span><span class="sxs-lookup"><span data-stu-id="3850c-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3850c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3850c-112">Requirements</span></span>  
 <span data-ttu-id="3850c-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3850c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3850c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3850c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3850c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3850c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3850c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3850c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
