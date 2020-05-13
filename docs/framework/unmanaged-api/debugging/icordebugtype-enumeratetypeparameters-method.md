---
title: Método ICorDebugType::EnumerateTypeParameters
ms.date: 03/30/2017
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
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379999"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="573dc-102">Método ICorDebugType::EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="573dc-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="573dc-103">Obtém um ponteiro de interface para um ICorDebugTypeEnum que contém os <xref:System.Type> parâmetros da classe referenciada por este ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="573dc-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="573dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="573dc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="573dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="573dc-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="573dc-106">fora Um ponteiro para o endereço de um `ICorDebugTypeEnum` que contém os parâmetros do tipo.</span><span class="sxs-lookup"><span data-stu-id="573dc-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="573dc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="573dc-107">Remarks</span></span>  
 <span data-ttu-id="573dc-108">Você pode usar `EnumerateTypeParameters` se o valor de CorElementType retornado por [ICorDebugType:: GetType](icordebugtype-gettype-method.md) for ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR ou ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="573dc-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="573dc-109">O número de parâmetros e sua ordem depende do tipo:</span><span class="sxs-lookup"><span data-stu-id="573dc-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="573dc-110">ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE: o número de parâmetros de tipo contidos no `ICorDebugTypeEnum` que esse método retorna, dependerá do número de parâmetros de tipo formal para a classe correspondente.</span><span class="sxs-lookup"><span data-stu-id="573dc-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="573dc-111">Por exemplo, se o tipo for `class Dict<String,int32>` , `EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém objetos que representam `String` e `int32` em sequência.</span><span class="sxs-lookup"><span data-stu-id="573dc-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="573dc-112">ELEMENT_TYPE_FNPTR: o número de parâmetros de tipo contidos em `ICorDebugTypeEnum` será um maior que o número de argumentos aceitos pela função.</span><span class="sxs-lookup"><span data-stu-id="573dc-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="573dc-113">O primeiro parâmetro de tipo contido no `ICorDebugTypeEnum` é o tipo de retorno para a função, e os parâmetros de tipo subsequentes são os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="573dc-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="573dc-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR: um parâmetro de tipo será retornado.</span><span class="sxs-lookup"><span data-stu-id="573dc-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="573dc-115">Por exemplo, se o tipo for um tipo de matriz como `int32[]` , `EnumerateTypeParameters` retornará um `ICorDebugTypeEnum` que contém um objeto que representa `int32` .</span><span class="sxs-lookup"><span data-stu-id="573dc-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="573dc-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="573dc-116">Requirements</span></span>  
 <span data-ttu-id="573dc-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="573dc-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="573dc-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="573dc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="573dc-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="573dc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="573dc-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="573dc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
