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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56c8eba49260eba9e3e0ca7e9ab4c7cfcd3261f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995625"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="41fa0-102">Método ICorDebugFunction::GetToken</span><span class="sxs-lookup"><span data-stu-id="41fa0-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="41fa0-103">Obtém os metadados de token para essa função.</span><span class="sxs-lookup"><span data-stu-id="41fa0-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41fa0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41fa0-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41fa0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41fa0-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="41fa0-106">[out] Um ponteiro para um `mdMethodDef` token que referencia os metadados para essa função.</span><span class="sxs-lookup"><span data-stu-id="41fa0-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41fa0-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41fa0-107">Requirements</span></span>  
 <span data-ttu-id="41fa0-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41fa0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41fa0-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41fa0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41fa0-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41fa0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41fa0-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41fa0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
