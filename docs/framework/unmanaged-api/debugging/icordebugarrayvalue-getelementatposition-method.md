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
ms.openlocfilehash: 10584442d7e0bd61e6decaf2b494dfe39f339d6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088424"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="5ec64-102">Método ICorDebugArrayValue::GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="5ec64-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="5ec64-103">Obtém o elemento na posição fornecida, tratando a matriz como uma matriz unidimensional com base em zero.</span><span class="sxs-lookup"><span data-stu-id="5ec64-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ec64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ec64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ec64-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ec64-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="5ec64-106">no A posição do elemento a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="5ec64-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5ec64-107">fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento.</span><span class="sxs-lookup"><span data-stu-id="5ec64-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ec64-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ec64-108">Remarks</span></span>  
 <span data-ttu-id="5ec64-109">O layout de uma matriz de várias dimensões segue o C++ estilo do layout da matriz.</span><span class="sxs-lookup"><span data-stu-id="5ec64-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ec64-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ec64-110">Requirements</span></span>  
 <span data-ttu-id="5ec64-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ec64-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ec64-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ec64-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ec64-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ec64-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ec64-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ec64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
