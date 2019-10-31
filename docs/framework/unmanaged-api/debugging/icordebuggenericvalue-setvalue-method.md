---
title: Método ICorDebugGenericValue::SetValue
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: 4cd03895b4e33c3e42c71acca12eaf950fc9a145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138554"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="8bdad-102">Método ICorDebugGenericValue::SetValue</span><span class="sxs-lookup"><span data-stu-id="8bdad-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="8bdad-103">Copia um novo valor do buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="8bdad-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bdad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bdad-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bdad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8bdad-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="8bdad-106">no Um ponteiro para o buffer do qual copiar o valor.</span><span class="sxs-lookup"><span data-stu-id="8bdad-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bdad-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8bdad-107">Remarks</span></span>  
 <span data-ttu-id="8bdad-108">Para tipos de referência, o valor é a referência, não o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8bdad-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bdad-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bdad-109">Requirements</span></span>  
 <span data-ttu-id="8bdad-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bdad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bdad-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bdad-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bdad-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bdad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bdad-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bdad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
