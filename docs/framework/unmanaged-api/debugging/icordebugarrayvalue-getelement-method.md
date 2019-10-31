---
title: Método ICorDebugArrayValue::GetElement
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 3d45caae56403d77776f1a8adbb5fb9c368ff105
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088488"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="3bbef-102">Método ICorDebugArrayValue::GetElement</span><span class="sxs-lookup"><span data-stu-id="3bbef-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="3bbef-103">Obtém o valor do elemento da matriz fornecido.</span><span class="sxs-lookup"><span data-stu-id="3bbef-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bbef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bbef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bbef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3bbef-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="3bbef-106">no O número de dimensões deste objeto de `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="3bbef-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="3bbef-107">Esse valor também é o tamanho da matriz de `indices` porque seu tamanho é igual ao número de dimensões do objeto `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="3bbef-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="3bbef-108">no Uma matriz de valores de índice, cada um deles especifica uma posição dentro de uma dimensão do objeto `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="3bbef-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="3bbef-109">Esse valor não deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="3bbef-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3bbef-110">fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="3bbef-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bbef-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3bbef-111">Requirements</span></span>  
 <span data-ttu-id="3bbef-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bbef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bbef-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bbef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bbef-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bbef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bbef-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bbef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
