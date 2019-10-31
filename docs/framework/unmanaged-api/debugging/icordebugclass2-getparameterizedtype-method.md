---
title: Método ICorDebugClass2::GetParameterizedType
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
ms.openlocfilehash: 64537ab97c1256cc6f963999b027bafc25cbbccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125739"
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="a178a-102">Método ICorDebugClass2::GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="a178a-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="a178a-103">Obtém a declaração de tipo para esta classe.</span><span class="sxs-lookup"><span data-stu-id="a178a-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a178a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a178a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a178a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a178a-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="a178a-106">no Um valor da enumeração CorElementType que especifica o tipo de elemento para esta classe: defina esse valor como ELEMENT_TYPE_VALUETYPE se esse ICorDebugClass2 representar um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a178a-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="a178a-107">Defina esse valor como ELEMENT_TYPE_CLASS se este `ICorDebugClass2` representar um tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="a178a-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="a178a-108">no O número de parâmetros de tipo, se o tipo for genérico.</span><span class="sxs-lookup"><span data-stu-id="a178a-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="a178a-109">O número de parâmetros de tipo (se houver) deve corresponder ao número exigido pela classe.</span><span class="sxs-lookup"><span data-stu-id="a178a-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="a178a-110">no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugType que representa um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="a178a-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="a178a-111">Se a classe for não genérica, esse valor será NULL.</span><span class="sxs-lookup"><span data-stu-id="a178a-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a178a-112">fora Um ponteiro para o endereço de um objeto de `ICorDebugType` que representa a declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="a178a-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="a178a-113">Este objeto é equivalente a um objeto <xref:System.Type> no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a178a-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a178a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="a178a-114">Remarks</span></span>  
 <span data-ttu-id="a178a-115">Se a classe não for genérica, ou seja, se ela não tiver parâmetros de tipo, `GetParameterizedType` simplesmente obterá o objeto de tipo de tempo de execução correspondente à classe.</span><span class="sxs-lookup"><span data-stu-id="a178a-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="a178a-116">O parâmetro `elementType` deve ser definido como o tipo de elemento correto para a classe: ELEMENT_TYPE_VALUETYPE se a classe for um tipo de valor; caso contrário, ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="a178a-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="a178a-117">Se a classe aceita parâmetros de tipo (por exemplo, `ArrayList<T>`), você pode usar `GetParameterizedType` para construir um objeto de tipo para um tipo instanciado, como `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="a178a-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="a178a-118">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="a178a-118">Background Information</span></span>  
 <span data-ttu-id="a178a-119">No .NET Framework versões 1,0 e 1,1, todos os tipos nos metadados podem ser mapeados diretamente para um tipo no processo em execução.</span><span class="sxs-lookup"><span data-stu-id="a178a-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="a178a-120">Assim, um tipo de metadados e um tipo de tempo de execução tinham uma única representação no processo em execução.</span><span class="sxs-lookup"><span data-stu-id="a178a-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="a178a-121">No entanto, um tipo genérico em metadados pode ser mapeado para várias instanciações diferentes do tipo no processo em execução.</span><span class="sxs-lookup"><span data-stu-id="a178a-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="a178a-122">Por exemplo, o tipo de metadados `SortedList<K,V>` pode ser mapeado para `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a178a-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="a178a-123">Portanto, você precisa de uma maneira de tratar a instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="a178a-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="a178a-124">O .NET Framework versão 2,0 apresenta a interface `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a178a-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="a178a-125">Para um tipo genérico, um objeto `ICorDebugClass` ou `ICorDebugClass2` representa o tipo não instanciado (`SortedList<K,V>`) e um objeto `ICorDebugType` representa os vários tipos instanciados.</span><span class="sxs-lookup"><span data-stu-id="a178a-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="a178a-126">Dado um objeto `ICorDebugClass` ou `ICorDebugClass2`, você pode criar um objeto `ICorDebugType` para qualquer instanciação chamando o método `ICorDebugClass2::GetParameterizedType`.</span><span class="sxs-lookup"><span data-stu-id="a178a-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="a178a-127">Você também pode criar um objeto `ICorDebugType` para um tipo simples, como Int32, ou para um tipo não genérico.</span><span class="sxs-lookup"><span data-stu-id="a178a-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="a178a-128">A introdução do objeto `ICorDebugType` para representar a noção de tempo de execução de um tipo tem um efeito de ondulação em toda a API.</span><span class="sxs-lookup"><span data-stu-id="a178a-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="a178a-129">As funções que anteriormente levaram um objeto `ICorDebugClass` ou `ICorDebugClass2` ou até mesmo um valor `CorElementType` são generalizadas para pegar um objeto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a178a-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a178a-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a178a-130">Requirements</span></span>  
 <span data-ttu-id="a178a-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a178a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a178a-132">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a178a-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a178a-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a178a-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a178a-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a178a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
