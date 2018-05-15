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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83aebad108a743d25b8ea93c99060d10bf5c3980
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="f2f72-102">Método ICorDebugGenericValue::SetValue</span><span class="sxs-lookup"><span data-stu-id="f2f72-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="f2f72-103">Copia um novo valor de buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="f2f72-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2f72-104">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2f72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2f72-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="f2f72-106">[in] Um ponteiro para o buffer da qual copiar o valor.</span><span class="sxs-lookup"><span data-stu-id="f2f72-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2f72-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2f72-107">Remarks</span></span>  
 <span data-ttu-id="f2f72-108">Para tipos de referência, o valor é a referência, não o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f2f72-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f72-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2f72-109">Requirements</span></span>  
 <span data-ttu-id="f2f72-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2f72-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f72-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2f72-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2f72-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2f72-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f72-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f72-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
