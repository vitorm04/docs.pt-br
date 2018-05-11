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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a5b3a28c7250a16e78e199bceff7c9e64517319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugclass2getparameterizedtype-method"></a><span data-ttu-id="e4455-102">Método ICorDebugClass2::GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="e4455-102">ICorDebugClass2::GetParameterizedType Method</span></span>
<span data-ttu-id="e4455-103">Obtém o tipo de declaração para essa classe.</span><span class="sxs-lookup"><span data-stu-id="e4455-103">Gets the type declaration for this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4455-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4455-104">Syntax</span></span>  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4455-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4455-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="e4455-106">[in] Um valor da enumeração CorElementType que especifica o tipo de elemento para esta classe: Defina esse valor como ELEMENT_TYPE_VALUETYPE se este ICorDebugClass2 representa um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="e4455-106">[in] A value of the CorElementType enumeration that specifies the element type for this class: Set this value to ELEMENT_TYPE_VALUETYPE if this ICorDebugClass2 represents a value type.</span></span> <span data-ttu-id="e4455-107">Defina esse valor como ELEMENT_TYPE_CLASS se este `ICorDebugClass2` representa um tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="e4455-107">Set this value to ELEMENT_TYPE_CLASS if this `ICorDebugClass2` represents a complex type.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="e4455-108">[in] O número de parâmetros de tipo, se o tipo é genérico.</span><span class="sxs-lookup"><span data-stu-id="e4455-108">[in] The number of type parameters, if the type is generic.</span></span> <span data-ttu-id="e4455-109">O número de parâmetros de tipo (se houver) deve corresponder ao número exigido pela classe.</span><span class="sxs-lookup"><span data-stu-id="e4455-109">The number of type parameters (if any) must match the number required by the class.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="e4455-110">[in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugType que representa um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="e4455-110">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type parameter.</span></span> <span data-ttu-id="e4455-111">Se a classe não-genérica, esse valor é nulo.</span><span class="sxs-lookup"><span data-stu-id="e4455-111">If the class is non-generic, this value is null.</span></span>  
  
 `ppType`  
 <span data-ttu-id="e4455-112">[out] Um ponteiro para o endereço de uma `ICorDebugType` objeto que representa o tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="e4455-112">[out] A pointer to the address of an `ICorDebugType` object that represents the type declaration.</span></span> <span data-ttu-id="e4455-113">Esse objeto é equivalente a um <xref:System.Type> objeto no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e4455-113">This object is equivalent to a <xref:System.Type> object in managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4455-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4455-114">Remarks</span></span>  
 <span data-ttu-id="e4455-115">Se a classe for não genérico, ou seja, se nenhum parâmetro de tipo, `GetParameterizedType` simplesmente obtém o objeto de tipo de tempo de execução correspondente à classe.</span><span class="sxs-lookup"><span data-stu-id="e4455-115">If the class is non-generic, that is, if it has no type parameters, `GetParameterizedType` simply gets the runtime type object corresponding to the class.</span></span> <span data-ttu-id="e4455-116">O `elementType` parâmetro deve ser definido para o tipo de elemento correto para a classe: ELEMENT_TYPE_VALUETYPE se a classe for um tipo de valor; caso contrário, ELEMENT_TYPE_CLASS.</span><span class="sxs-lookup"><span data-stu-id="e4455-116">The `elementType` parameter should be set to the correct element type for the class: ELEMENT_TYPE_VALUETYPE if the class is a value type; otherwise, ELEMENT_TYPE_CLASS.</span></span>  
  
 <span data-ttu-id="e4455-117">Se a classe aceita parâmetros de tipo (por exemplo, `ArrayList<T>`), você pode usar `GetParameterizedType` para construir um objeto de tipo para um tipo instanciado como `ArrayList<int>`.</span><span class="sxs-lookup"><span data-stu-id="e4455-117">If the class accepts type parameters (for example, `ArrayList<T>`), you can use `GetParameterizedType` to construct a type object for an instantiated type such as `ArrayList<int>`.</span></span>  
  
## <a name="background-information"></a><span data-ttu-id="e4455-118">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="e4455-118">Background Information</span></span>  
 <span data-ttu-id="e4455-119">Nas versões do .NET Framework 1.0 e 1.1, todos os tipos nos metadados do podem ser mapeado diretamente para um tipo no processo de execução.</span><span class="sxs-lookup"><span data-stu-id="e4455-119">In the .NET Framework versions 1.0 and 1.1, every type in the metadata could be directly mapped to a type in the running process.</span></span> <span data-ttu-id="e4455-120">Portanto, um tipo de metadados e um tipo de tempo de execução tinham uma única representação do processo em execução.</span><span class="sxs-lookup"><span data-stu-id="e4455-120">Thus, a metadata type and a runtime type had a single representation in the running process.</span></span> <span data-ttu-id="e4455-121">No entanto, um tipo genérico nos metadados pode ser mapeado para muitas instâncias diferentes do tipo do processo em execução.</span><span class="sxs-lookup"><span data-stu-id="e4455-121">However, one generic type in metadata can be mapped to many different instantiations of the type in the running process.</span></span> <span data-ttu-id="e4455-122">Por exemplo, o tipo de metadados `SortedList<K,V>` pode ser mapeado para `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e4455-122">For example, the metadata type `SortedList<K,V>` can map to `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, and so on.</span></span> <span data-ttu-id="e4455-123">Assim, você precisa de uma maneira de lidar com uma instância de tipo.</span><span class="sxs-lookup"><span data-stu-id="e4455-123">Thus, you need a way to handle type instantiation.</span></span>  
  
 <span data-ttu-id="e4455-124">O .NET Framework versão 2.0 introduz o `ICorDebugType` interface.</span><span class="sxs-lookup"><span data-stu-id="e4455-124">The .NET Framework version 2.0 introduces the `ICorDebugType` interface.</span></span> <span data-ttu-id="e4455-125">Para um tipo genérico, um `ICorDebugClass` ou `ICorDebugClass2` objeto representa o tipo instanciado (`SortedList<K,V>`) e um `ICorDebugType` objeto representa os vários tipos de instâncias.</span><span class="sxs-lookup"><span data-stu-id="e4455-125">For a generic type, an `ICorDebugClass` or `ICorDebugClass2` object represents the uninstantiated type (`SortedList<K,V>`), and an `ICorDebugType` object represents the various instantiated types.</span></span> <span data-ttu-id="e4455-126">Dado um `ICorDebugClass` ou `ICorDebugClass2` do objeto, você pode criar um `ICorDebugType` objeto para qualquer instanciação chamando o `ICorDebugClass2::GetParameterizedType` método.</span><span class="sxs-lookup"><span data-stu-id="e4455-126">Given an `ICorDebugClass` or `ICorDebugClass2` object, you can create an `ICorDebugType` object for any instantiation by calling the `ICorDebugClass2::GetParameterizedType` method.</span></span> <span data-ttu-id="e4455-127">Você também pode criar um `ICorDebugType` objeto para um tipo simple, como Int32, ou para um tipo não genérico.</span><span class="sxs-lookup"><span data-stu-id="e4455-127">You can also create an `ICorDebugType` object for a simple type, such as Int32, or for a non-generic type.</span></span>  
  
 <span data-ttu-id="e4455-128">A introdução do `ICorDebugType` objeto para representar a noção de tempo de execução de um tipo tem um efeito de ondulação em toda a API.</span><span class="sxs-lookup"><span data-stu-id="e4455-128">The introduction of the `ICorDebugType` object to represent the run-time notion of a type has a ripple effect throughout the API.</span></span> <span data-ttu-id="e4455-129">Funções que levaram anteriormente um `ICorDebugClass` ou `ICorDebugClass2` do objeto ou até mesmo um `CorElementType` valor estão generalizados para tirar uma `ICorDebugType` objeto.</span><span class="sxs-lookup"><span data-stu-id="e4455-129">Functions that previously took an `ICorDebugClass` or `ICorDebugClass2` object or even a `CorElementType` value are generalized to take an `ICorDebugType` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4455-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4455-130">Requirements</span></span>  
 <span data-ttu-id="e4455-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4455-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4455-132">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4455-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4455-133">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4455-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4455-134">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4455-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
