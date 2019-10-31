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
ms.openlocfilehash: 7923008eecb9011bead685fbbb7f05f81f12329b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138588"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="7dfb3-102">Método ICorDebugGenericValue::GetValue</span><span class="sxs-lookup"><span data-stu-id="7dfb3-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="7dfb3-103">Copia o valor desse genérico no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="7dfb3-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7dfb3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dfb3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7dfb3-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="7dfb3-106">fora Um ponteiro para o valor representado por esse objeto ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="7dfb3-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="7dfb3-107">O valor pode ser um tipo simples ou um tipo de referência (ou seja, um ponteiro).</span><span class="sxs-lookup"><span data-stu-id="7dfb3-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dfb3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7dfb3-108">Requirements</span></span>  
 <span data-ttu-id="7dfb3-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dfb3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dfb3-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dfb3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dfb3-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dfb3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dfb3-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dfb3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
