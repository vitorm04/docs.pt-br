---
title: Método ICorDebugArrayValue::GetDimensions
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: fa2be894af6e44d09c25a736f45acba56052f9fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895046"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="2348d-102">Método ICorDebugArrayValue::GetDimensions</span><span class="sxs-lookup"><span data-stu-id="2348d-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="2348d-103">Obtém o número de elementos em cada dimensão dessa matriz.</span><span class="sxs-lookup"><span data-stu-id="2348d-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2348d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2348d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2348d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2348d-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="2348d-106">no O número de dimensões deste objeto ICorDebugArrayValue.</span><span class="sxs-lookup"><span data-stu-id="2348d-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="2348d-107">Esse valor também é o tamanho da `dims` matriz porque seu tamanho é igual ao número de dimensões do `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="2348d-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="2348d-108">fora Uma matriz de inteiros, cada um dos quais Especifica o número de elementos em uma dimensão neste `ICorDebugArrayValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="2348d-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2348d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2348d-109">Requirements</span></span>  
 <span data-ttu-id="2348d-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2348d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2348d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2348d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2348d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2348d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2348d-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2348d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
