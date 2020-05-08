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
ms.openlocfilehash: e6e8eb91bbc41faf0dcea010da9aa54995058653
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894973"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="7784e-102">Método ICorDebugArrayValue::HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="7784e-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="7784e-103">Obtém um valor que indica se qualquer dimensão dessa matriz tem um índice base diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="7784e-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7784e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7784e-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7784e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7784e-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="7784e-106">fora Um ponteiro para um valor booliano que `true` se uma ou mais dimensões desse `ICorDebugArrayValue` objeto têm um índice base diferente de zero; caso contrário, o valor booliano é `false`.</span><span class="sxs-lookup"><span data-stu-id="7784e-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7784e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7784e-107">Requirements</span></span>  
 <span data-ttu-id="7784e-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7784e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7784e-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7784e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7784e-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7784e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7784e-111">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7784e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
