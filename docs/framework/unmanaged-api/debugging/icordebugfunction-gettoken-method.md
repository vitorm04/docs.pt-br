---
title: Método ICorDebugFunction::GetToken
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 4229d567fc4ced5e3b78b390ced29fb9ea60f93b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137837"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="21f6a-102">Método ICorDebugFunction::GetToken</span><span class="sxs-lookup"><span data-stu-id="21f6a-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="21f6a-103">Obtém o token de metadados para esta função.</span><span class="sxs-lookup"><span data-stu-id="21f6a-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21f6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21f6a-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="21f6a-106">fora Um ponteiro para um `mdMethodDef` token que faz referência aos metadados para essa função.</span><span class="sxs-lookup"><span data-stu-id="21f6a-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f6a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21f6a-107">Requirements</span></span>  
 <span data-ttu-id="21f6a-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f6a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f6a-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21f6a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21f6a-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21f6a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21f6a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f6a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
