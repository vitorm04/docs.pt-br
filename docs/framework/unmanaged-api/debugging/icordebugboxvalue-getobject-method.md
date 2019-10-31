---
title: Método ICorDebugBoxValue::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: 475cc6c688262f318aa7f844b975ad69fa80bbe9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122815"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="e3a56-102">Método ICorDebugBoxValue::GetObject</span><span class="sxs-lookup"><span data-stu-id="e3a56-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="e3a56-103">Obtém o valor em caixa.</span><span class="sxs-lookup"><span data-stu-id="e3a56-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a56-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3a56-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3a56-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3a56-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="e3a56-106">fora Um ponteiro para o endereço de um objeto ICorDebugObjectValue que representa o valor boxed.</span><span class="sxs-lookup"><span data-stu-id="e3a56-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a56-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3a56-107">Requirements</span></span>  
 <span data-ttu-id="e3a56-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3a56-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a56-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3a56-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3a56-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3a56-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3a56-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3a56-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
