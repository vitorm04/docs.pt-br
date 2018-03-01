---
title: "Método ICorDebugType::EnumerateTypeParameters"
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
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d4b864b2b5fd4f2a6ed03218ce6e7b6f3bf62202
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="156d5-102">Método ICorDebugType::EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="156d5-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="156d5-103">Obtém um ponteiro de interface para um ICorDebugTypeEnum que contém o <xref:System.Type> parâmetros da classe referenciada por este ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="156d5-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="156d5-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="156d5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="156d5-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="156d5-106">[out] Um ponteiro para o endereço de um `ICorDebugTypeEnum` que contém os parâmetros do tipo.</span><span class="sxs-lookup"><span data-stu-id="156d5-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="156d5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="156d5-107">Remarks</span></span>  
 <span data-ttu-id="156d5-108">Você pode usar `EnumerateTypeParameters` se o valor de CorElementType retornado por [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) é ELEMENT_TYPE_CLASS ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE _ PTR ou ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="156d5-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="156d5-109">O número de parâmetros e sua ordem depende do tipo:</span><span class="sxs-lookup"><span data-stu-id="156d5-109">The number of parameters and their order depends on the type:</span></span>  
  
-   <span data-ttu-id="156d5-110">ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE: O número de parâmetros de tipo dentro de `ICorDebugTypeEnum` que este método retorna, dependerá do número de parâmetros de tipo formal para a classe correspondente.</span><span class="sxs-lookup"><span data-stu-id="156d5-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="156d5-111">Por exemplo, se o tipo é `class Dict<String,int32>`, em seguida, `EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém objetos que representam `String` e `int32` em sequência.</span><span class="sxs-lookup"><span data-stu-id="156d5-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
-   <span data-ttu-id="156d5-112">ELEMENT_TYPE_FNPTR: O número de parâmetros de tipo contidos no `ICorDebugTypeEnum` terá um maior que o número de argumentos aceitados pela função.</span><span class="sxs-lookup"><span data-stu-id="156d5-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="156d5-113">O primeiro parâmetro de tipo contido no `ICorDebugTypeEnum` é o tipo de retorno da função e os parâmetros de tipo subsequentes são os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="156d5-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
-   <span data-ttu-id="156d5-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR: um parâmetro de tipo será retornado.</span><span class="sxs-lookup"><span data-stu-id="156d5-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="156d5-115">Por exemplo, se o tipo é um tipo de matriz, como `int32[]`,`EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém um objeto que representa `int32`.</span><span class="sxs-lookup"><span data-stu-id="156d5-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="156d5-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="156d5-116">Requirements</span></span>  
 <span data-ttu-id="156d5-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="156d5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="156d5-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="156d5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="156d5-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="156d5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="156d5-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="156d5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
