---
title: Método ICorDebugGenericValue::GetValue
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53db4dcb13303c9e7bdd77a46b3c9526364bac06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995638"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="c5d3b-102">Método ICorDebugGenericValue::GetValue</span><span class="sxs-lookup"><span data-stu-id="c5d3b-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="c5d3b-103">Copia o valor nesse genérico no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="c5d3b-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5d3b-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5d3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5d3b-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="c5d3b-106">[out] Um ponteiro para o valor que é representado por esse objeto ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="c5d3b-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="c5d3b-107">O valor pode ser um tipo simples ou um tipo de referência (ou seja, um ponteiro).</span><span class="sxs-lookup"><span data-stu-id="c5d3b-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d3b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5d3b-108">Requirements</span></span>  
 <span data-ttu-id="c5d3b-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d3b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d3b-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5d3b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5d3b-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5d3b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5d3b-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d3b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
