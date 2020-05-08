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
ms.openlocfilehash: 5644c20ec5df2606c7258131573691997f424e50
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895023"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="7943f-102">Método ICorDebugArrayValue::GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="7943f-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="7943f-103">Obtém o elemento na posição fornecida, tratando a matriz como uma matriz unidimensional com base em zero.</span><span class="sxs-lookup"><span data-stu-id="7943f-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7943f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7943f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7943f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7943f-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="7943f-106">no A posição do elemento a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="7943f-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="7943f-107">fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento.</span><span class="sxs-lookup"><span data-stu-id="7943f-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7943f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7943f-108">Remarks</span></span>  
 <span data-ttu-id="7943f-109">O layout de uma matriz de várias dimensões segue o estilo C++ de layout de matriz.</span><span class="sxs-lookup"><span data-stu-id="7943f-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7943f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7943f-110">Requirements</span></span>  
 <span data-ttu-id="7943f-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7943f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7943f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7943f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7943f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7943f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7943f-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7943f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
