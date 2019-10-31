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
ms.openlocfilehash: 52bfe669d3b078657916554255a11cecfc07d484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085083"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="1e0f0-102">Método ICorDebugEval::GetResult</span><span class="sxs-lookup"><span data-stu-id="1e0f0-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="1e0f0-103">Obtém os resultados dessa avaliação.</span><span class="sxs-lookup"><span data-stu-id="1e0f0-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e0f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e0f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e0f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e0f0-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="1e0f0-106">fora Aponta para o endereço de um objeto ICorDebugValue que representa os resultados dessa avaliação, se a avaliação for concluída normalmente.</span><span class="sxs-lookup"><span data-stu-id="1e0f0-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e0f0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e0f0-107">Remarks</span></span>  
 <span data-ttu-id="1e0f0-108">O método `GetResult` é válido somente após a conclusão da avaliação.</span><span class="sxs-lookup"><span data-stu-id="1e0f0-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="1e0f0-109">Se a avaliação for concluída normalmente, `ppResult` especifica os resultados.</span><span class="sxs-lookup"><span data-stu-id="1e0f0-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="1e0f0-110">Se ele terminar com uma exceção, o resultado será a exceção lançada.</span><span class="sxs-lookup"><span data-stu-id="1e0f0-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="1e0f0-111">Se a avaliação foi para um novo objeto, o resultado é a referência ao novo objeto.</span><span class="sxs-lookup"><span data-stu-id="1e0f0-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e0f0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e0f0-112">Requirements</span></span>  
 <span data-ttu-id="1e0f0-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e0f0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e0f0-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e0f0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e0f0-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e0f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e0f0-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e0f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
