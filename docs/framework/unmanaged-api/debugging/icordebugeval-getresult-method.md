---
title: "Método ICorDebugEval::GetResult"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.GetResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7379237c73d79d9e8c66112a101edadca357cb10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="9e69f-102">Método ICorDebugEval::GetResult</span><span class="sxs-lookup"><span data-stu-id="9e69f-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="9e69f-103">Obtém os resultados dessa avaliação.</span><span class="sxs-lookup"><span data-stu-id="9e69f-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e69f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e69f-104">Syntax</span></span>  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e69f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e69f-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="9e69f-106">[out] Ponteiro para o endereço de um objeto ICorDebugValue que representa os resultados dessa avaliação, se a avaliação for concluída normalmente.</span><span class="sxs-lookup"><span data-stu-id="9e69f-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e69f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e69f-107">Remarks</span></span>  
 <span data-ttu-id="9e69f-108">O `GetResult` método é válido somente depois que a avaliação é concluída.</span><span class="sxs-lookup"><span data-stu-id="9e69f-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="9e69f-109">Se a avaliação for concluída normalmente, `ppResult` Especifica os resultados.</span><span class="sxs-lookup"><span data-stu-id="9e69f-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="9e69f-110">Se ele termina com uma exceção, o resultado é a exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="9e69f-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="9e69f-111">Se a avaliação de um novo objeto, o resultado é a referência ao novo objeto.</span><span class="sxs-lookup"><span data-stu-id="9e69f-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e69f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e69f-112">Requirements</span></span>  
 <span data-ttu-id="9e69f-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e69f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e69f-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e69f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e69f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e69f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e69f-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e69f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
