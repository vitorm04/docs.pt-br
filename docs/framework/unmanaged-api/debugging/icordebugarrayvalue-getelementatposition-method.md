---
title: Método ICorDebugArrayValue::GetElementAtPosition
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76100116f2ca3a9b9a99477ca2352d5fa1335ab2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645676"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="bc054-102">Método ICorDebugArrayValue::GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="bc054-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="bc054-103">Obtém o elemento na posição determinada, tratando da matriz como uma matriz unidimensional de base zero.</span><span class="sxs-lookup"><span data-stu-id="bc054-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc054-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc054-104">Syntax</span></span>  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc054-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc054-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="bc054-106">[in] A posição do elemento a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="bc054-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bc054-107">[out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento.</span><span class="sxs-lookup"><span data-stu-id="bc054-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc054-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc054-108">Remarks</span></span>  
 <span data-ttu-id="bc054-109">O layout de uma matriz multidimensional segue o estilo de C++ do layout de matriz.</span><span class="sxs-lookup"><span data-stu-id="bc054-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc054-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc054-110">Requirements</span></span>  
 <span data-ttu-id="bc054-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc054-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc054-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc054-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc054-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc054-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc054-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc054-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
