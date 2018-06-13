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
ms.openlocfilehash: a6d30a9f03d8717486be7cd89bb182d350a82df7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411630"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="c7a80-102">Método ICorDebugGenericValue::GetValue</span><span class="sxs-lookup"><span data-stu-id="c7a80-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="c7a80-103">Copia o valor nesse genérico para o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="c7a80-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7a80-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7a80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7a80-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="c7a80-106">[out] Um ponteiro para o valor que é representado pelo objeto ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="c7a80-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="c7a80-107">O valor pode ser um tipo simples ou um tipo de referência (ou seja, um ponteiro).</span><span class="sxs-lookup"><span data-stu-id="c7a80-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a80-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7a80-108">Requirements</span></span>  
 <span data-ttu-id="c7a80-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a80-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a80-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7a80-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7a80-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7a80-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7a80-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a80-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
