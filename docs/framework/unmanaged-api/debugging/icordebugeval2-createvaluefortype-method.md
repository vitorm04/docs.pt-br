---
title: "Método ICorDebugEval2::CreateValueForType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18e7eb5fc30c27fd2c4865dc61e2f75dc9e96068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="9c5c6-102">Método ICorDebugEval2::CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="9c5c6-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="9c5c6-103">Obtém um ponteiro para um novo ICorDebugValue do tipo especificado, com um valor inicial de zero ou nulo.</span><span class="sxs-lookup"><span data-stu-id="9c5c6-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c5c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c5c6-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c5c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c5c6-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="9c5c6-106">[in] Ponteiro para um objeto ICorDebugType que representa o tipo.</span><span class="sxs-lookup"><span data-stu-id="9c5c6-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9c5c6-107">[out] Ponteiro para o endereço de uma `ICorDebugValue` objeto que representa o valor.</span><span class="sxs-lookup"><span data-stu-id="9c5c6-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c5c6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c5c6-108">Remarks</span></span>  
 <span data-ttu-id="9c5c6-109">`CreateValueForType`generaliza [: Createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , permitindo que você especifique um tipo de objeto arbitrário, incluindo construído tipos como `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="9c5c6-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="9c5c6-110">A única finalidade deste método é gerar um valor que pode ser passado para uma avaliação de função.</span><span class="sxs-lookup"><span data-stu-id="9c5c6-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="9c5c6-111">O tipo deve ser uma classe ou um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="9c5c6-111">The type must be a class or a value type.</span></span> <span data-ttu-id="9c5c6-112">Você não pode usar esse método para criar valores de cadeia de caracteres ou valores de matriz.</span><span class="sxs-lookup"><span data-stu-id="9c5c6-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c5c6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c5c6-113">Requirements</span></span>  
 <span data-ttu-id="9c5c6-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c5c6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c5c6-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c5c6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c5c6-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c5c6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c5c6-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c5c6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
