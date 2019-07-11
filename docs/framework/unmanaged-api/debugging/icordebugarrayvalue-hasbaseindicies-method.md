---
title: Método ICorDebugArrayValue::HasBaseIndicies
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c488ca3a77f2c2b2a40c6143989cd86adf071787
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737437"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="d6059-102">Método ICorDebugArrayValue::HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="d6059-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="d6059-103">Obtém um valor que indica se todas as dimensões desta matriz tem um índice de base de diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="d6059-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6059-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6059-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6059-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6059-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="d6059-106">[out] Um ponteiro para um valor booliano que será `true` se um ou mais dimensões dessa `ICorDebugArrayValue` objeto tem um índice de base de diferente de zero; caso contrário, o valor booliano é `false`.</span><span class="sxs-lookup"><span data-stu-id="d6059-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6059-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6059-107">Requirements</span></span>  
 <span data-ttu-id="d6059-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6059-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6059-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6059-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6059-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6059-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6059-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6059-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
