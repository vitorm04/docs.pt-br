---
title: "Colocar a função (referência de API não gerenciada)"
description: "A função Put atribui um novo valor para uma propriedade nomeada."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c4ad979a3a662618ab62b52d63bda3dbb1e71b9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="put-function"></a><span data-ttu-id="52afd-103">Colocar a função</span><span class="sxs-lookup"><span data-stu-id="52afd-103">Put function</span></span>
<span data-ttu-id="52afd-104">Define uma propriedade nomeada para um novo valor.</span><span class="sxs-lookup"><span data-stu-id="52afd-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="52afd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52afd-105">Syntax</span></span>  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a><span data-ttu-id="52afd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52afd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="52afd-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="52afd-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="52afd-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="52afd-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="52afd-109">[in] O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="52afd-109">[in] The name of the property.</span></span> <span data-ttu-id="52afd-110">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="52afd-110">This parameter cannot be `null`.</span></span>

`lFlags`  
<span data-ttu-id="52afd-111">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="52afd-111">[in] Reserved.</span></span> <span data-ttu-id="52afd-112">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="52afd-112">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="52afd-113">[in] Um ponteiro para um válida `VARIANT` que se torna o novo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="52afd-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="52afd-114">Se `pVal` é `null` ou aponta para um `VARIANT` do tipo `VT_NULL`, a propriedade é definida como `null`.</span><span class="sxs-lookup"><span data-stu-id="52afd-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span> 

`vtType`  
<span data-ttu-id="52afd-115">[in] O tipo de `VARIANT` apontada pelo `pVal`.</span><span class="sxs-lookup"><span data-stu-id="52afd-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="52afd-116">Consulte o [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="52afd-116">See the [Remarks](#remarks) section for more information.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="52afd-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="52afd-117">Return value</span></span>

<span data-ttu-id="52afd-118">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="52afd-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="52afd-119">Constante</span><span class="sxs-lookup"><span data-stu-id="52afd-119">Constant</span></span>  |<span data-ttu-id="52afd-120">Valor</span><span class="sxs-lookup"><span data-stu-id="52afd-120">Value</span></span>  |<span data-ttu-id="52afd-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="52afd-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="52afd-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="52afd-122">0x80041001</span></span> | <span data-ttu-id="52afd-123">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="52afd-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="52afd-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="52afd-124">0x80041008</span></span> | <span data-ttu-id="52afd-125">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="52afd-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="52afd-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="52afd-126">0x8004102a</span></span> | <span data-ttu-id="52afd-127">O tipo de propriedade não é reconhecido.</span><span class="sxs-lookup"><span data-stu-id="52afd-127">The property type is not recognized.</span></span> <span data-ttu-id="52afd-128">Esse valor é retornado ao criar instâncias de classe, se a classe já existe.</span><span class="sxs-lookup"><span data-stu-id="52afd-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="52afd-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="52afd-129">0x80041006</span></span> | <span data-ttu-id="52afd-130">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="52afd-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="52afd-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="52afd-131">0x80041005</span></span> | <span data-ttu-id="52afd-132">Para instâncias: indica que `pVal` aponta para um `VARIANT` de um tipo incorreto para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="52afd-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="52afd-133">Para obter definições de classe: A propriedade já existe na classe pai e o novo tipo de COM é diferente do tipo de COM antigo.</span><span class="sxs-lookup"><span data-stu-id="52afd-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="52afd-134">0</span><span class="sxs-lookup"><span data-stu-id="52afd-134">0</span></span> | <span data-ttu-id="52afd-135">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="52afd-135">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="52afd-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="52afd-136">Remarks</span></span>

<span data-ttu-id="52afd-137">Essa função encapsula uma chamada para o [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="52afd-137">This function wraps a call to the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="52afd-138">Essa função sempre substitui o valor da propriedade atual com um novo.</span><span class="sxs-lookup"><span data-stu-id="52afd-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="52afd-139">Se o [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) aponta para uma definição de classe `Put` cria ou atualiza o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="52afd-139">If the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="52afd-140">Quando [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) aponta para uma instância CIM, `Put` atualiza o valor da propriedade. `Put` não é possível criar um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="52afd-140">When [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="52afd-141">O `__CLASS` sistema propriedade só é gravável durante a criação de classe quando ele não pode ser deixado em branco.</span><span class="sxs-lookup"><span data-stu-id="52afd-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="52afd-142">Todas as outras propriedades de sistema são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="52afd-142">All other system properties are read-only.</span></span>

<span data-ttu-id="52afd-143">Um usuário não é possível criar propriedades com nomes que podem começam ou terminam com um sublinhado ("_").</span><span class="sxs-lookup"><span data-stu-id="52afd-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="52afd-144">Isso é reservado para propriedades e classes do sistema.</span><span class="sxs-lookup"><span data-stu-id="52afd-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="52afd-145">Se a propriedade definida `Put` função existe na classe pai, o valor padrão da propriedade é alterado, a menos que o tipo de propriedade não coincide com o tipo de classe pai.</span><span class="sxs-lookup"><span data-stu-id="52afd-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="52afd-146">Se a propriedade não existe e não é uma incompatibilidade de tipo, a propriedade é ceated.</span><span class="sxs-lookup"><span data-stu-id="52afd-146">If the property does not exist and it is not a type mismatch, the property is ceated.</span></span>

<span data-ttu-id="52afd-147">Use o `vtType` parâmetro somente durante a criação de novas propriedades em uma definição de classe do CIM e `pVal` é `null` ou aponta para um `VARIANT` do tipo `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="52afd-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="52afd-148">Nesse caso, o `vType` parâmetro especifica o tipo CIM da propriedade.</span><span class="sxs-lookup"><span data-stu-id="52afd-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="52afd-149">Em todos os outros casos, `vtType` deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="52afd-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="52afd-150">`vtType`também deve ser 0 se o objeto subjacente é uma instância (mesmo se `Val` é `null`) porque o tipo da propriedade é fixo e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="52afd-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>   

## <a name="example"></a><span data-ttu-id="52afd-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52afd-151">Example</span></span>

<span data-ttu-id="52afd-152">Para obter um exemplo, consulte o [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="52afd-152">For an example, see the [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="52afd-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52afd-153">Requirements</span></span>  
 <span data-ttu-id="52afd-154">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52afd-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52afd-155">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="52afd-155">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="52afd-156">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="52afd-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52afd-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52afd-157">See also</span></span>  
[<span data-ttu-id="52afd-158">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="52afd-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
