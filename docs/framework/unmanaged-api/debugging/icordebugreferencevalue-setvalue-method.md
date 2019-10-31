---
title: Método ICorDebugReferenceValue::SetValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 61563488bff682cc7a417296c3db8eb7e7cf965a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139327"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="39aeb-102">Método ICorDebugReferenceValue::SetValue</span><span class="sxs-lookup"><span data-stu-id="39aeb-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="39aeb-103">Define o endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="39aeb-103">Sets the specified memory address.</span></span> <span data-ttu-id="39aeb-104">Ou seja, esse método define esse ICorDebugReferenceValue para apontar para um objeto.</span><span class="sxs-lookup"><span data-stu-id="39aeb-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39aeb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39aeb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39aeb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39aeb-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="39aeb-107">no Um valor `CORDB_ADDRESS` que especifica o endereço do objeto ao qual esse `ICorDebugReferenceValue` aponta.</span><span class="sxs-lookup"><span data-stu-id="39aeb-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39aeb-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39aeb-108">Requirements</span></span>  
 <span data-ttu-id="39aeb-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39aeb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39aeb-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39aeb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39aeb-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39aeb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39aeb-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39aeb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
