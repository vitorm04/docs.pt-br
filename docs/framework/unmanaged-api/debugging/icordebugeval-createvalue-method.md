---
title: "Método ICorDebugEval::CreateValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CreateValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7242e98a69083ca8d5a6d8d54e9b25279abb7bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="d2121-102">Método ICorDebugEval::CreateValue</span><span class="sxs-lookup"><span data-stu-id="d2121-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="d2121-103">Cria um valor do tipo especificado, com um valor inicial de zero ou nulo.</span><span class="sxs-lookup"><span data-stu-id="d2121-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="d2121-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="d2121-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d2121-105">Use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d2121-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2121-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2121-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2121-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2121-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="d2121-108">[in] Um valor de [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeração que especifica o tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="d2121-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="d2121-109">[in] Ponteiro para um [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) objeto que especifica a classe de valor, se o tipo não é um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="d2121-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d2121-110">[out] Ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor.</span><span class="sxs-lookup"><span data-stu-id="d2121-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2121-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2121-111">Remarks</span></span>  
 <span data-ttu-id="d2121-112">`CreateValue`cria um `ICorDebugValue` objeto do tipo especificado para o único propósito de usá-lo em uma avaliação de função.</span><span class="sxs-lookup"><span data-stu-id="d2121-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="d2121-113">Este objeto de valor pode ser usado para passar constantes de usuário como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d2121-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="d2121-114">Se o tipo do valor é um tipo primitivo, o valor inicial é zero ou nulo.</span><span class="sxs-lookup"><span data-stu-id="d2121-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="d2121-115">Use [Icordebuggenericvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) para definir o valor de um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="d2121-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="d2121-116">Se o valor de `elementType` é ELEMENT_TYPE_CLASS, você obtém "ICorDebugReferenceValue" (retornados em `ppValue`) que representa a referência de objeto nulo.</span><span class="sxs-lookup"><span data-stu-id="d2121-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="d2121-117">Você pode usar esse objeto para passar nulo para uma avaliação de função que tem parâmetros de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="d2121-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="d2121-118">Não é possível definir o `ICorDebugValue` fazer nada; ele permanecerá nulo.</span><span class="sxs-lookup"><span data-stu-id="d2121-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2121-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2121-119">Requirements</span></span>  
 <span data-ttu-id="d2121-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2121-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2121-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2121-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2121-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2121-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2121-123">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="d2121-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2121-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2121-124">See Also</span></span>  
    
 [<span data-ttu-id="d2121-125">Método CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="d2121-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 <span data-ttu-id="d2121-126">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="d2121-126">ICorDebugValue</span></span>
