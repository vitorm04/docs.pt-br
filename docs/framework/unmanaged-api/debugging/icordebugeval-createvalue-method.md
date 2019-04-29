---
title: Método ICorDebugEval::CreateValue
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c16f6d1334888fc389a7c39cf0a3865afca2085
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934739"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="c9e80-102">Método ICorDebugEval::CreateValue</span><span class="sxs-lookup"><span data-stu-id="c9e80-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="c9e80-103">Cria um valor do tipo especificado, com um valor inicial de zero ou nulo.</span><span class="sxs-lookup"><span data-stu-id="c9e80-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="c9e80-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="c9e80-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c9e80-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c9e80-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e80-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9e80-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9e80-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9e80-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="c9e80-108">[in] Um valor igual a [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeração que especifica o tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="c9e80-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="c9e80-109">[in] Ponteiro para um [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) objeto que especifica a classe de valor, se o tipo não for um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="c9e80-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c9e80-110">[out] Ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor.</span><span class="sxs-lookup"><span data-stu-id="c9e80-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9e80-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9e80-111">Remarks</span></span>  
 <span data-ttu-id="c9e80-112">`CreateValue` cria um `ICorDebugValue` objeto do tipo especificado para o único propósito de usá-lo em uma avaliação de função.</span><span class="sxs-lookup"><span data-stu-id="c9e80-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="c9e80-113">Esse objeto de valor pode ser usado para passar constantes do usuário como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c9e80-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="c9e80-114">Se o tipo do valor for um tipo primitivo, seu valor inicial é zero ou nulo.</span><span class="sxs-lookup"><span data-stu-id="c9e80-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="c9e80-115">Use [icordebuggenericvalue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) para definir o valor de um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="c9e80-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="c9e80-116">Se o valor de `elementType` é ELEMENT_TYPE_CLASS, você obtém "ICorDebugReferenceValue" (retornados em `ppValue`) que representa a referência de objeto nulo.</span><span class="sxs-lookup"><span data-stu-id="c9e80-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="c9e80-117">Você pode usar esse objeto passar null para uma avaliação de função que tem parâmetros de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="c9e80-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="c9e80-118">Não é possível definir o `ICorDebugValue` para qualquer coisa; ele sempre permanecerá nulo.</span><span class="sxs-lookup"><span data-stu-id="c9e80-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e80-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9e80-119">Requirements</span></span>  
 <span data-ttu-id="c9e80-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9e80-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9e80-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9e80-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9e80-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9e80-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9e80-123">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="c9e80-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e80-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9e80-124">See also</span></span>

- [<span data-ttu-id="c9e80-125">Método CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="c9e80-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="c9e80-126">Interface ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="c9e80-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
