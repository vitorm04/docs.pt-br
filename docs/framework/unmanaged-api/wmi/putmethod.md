---
title: Função PutMethod (referência de API não gerenciada)
description: A função PutMethod cria um método.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f74b0d30a1a8899d3c8d0a2bf0f108ea11165cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461846"
---
# <a name="putmethod-function"></a><span data-ttu-id="fd666-103">Função PutMethod</span><span class="sxs-lookup"><span data-stu-id="fd666-103">PutMethod function</span></span>
<span data-ttu-id="fd666-104">Cria um método.</span><span class="sxs-lookup"><span data-stu-id="fd666-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="fd666-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd666-105">Syntax</span></span>  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="fd666-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd666-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fd666-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="fd666-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fd666-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="fd666-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="fd666-109">[in] O nome do método para criar.</span><span class="sxs-lookup"><span data-stu-id="fd666-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="fd666-110">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="fd666-110">[in] Reserved.</span></span> <span data-ttu-id="fd666-111">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="fd666-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="fd666-112">[in] Um ponteiro para uma cópia do [classe de sistema de Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) que contém o `in` parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="fd666-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="fd666-113">Esse parâmetro é ignorado se definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="fd666-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="fd666-114">[in]  Um ponteiro para uma cópia do [classe de sistema de Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) que contém o `out` parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="fd666-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="fd666-115">Esse parâmetro é ignorado se definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="fd666-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="fd666-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fd666-116">Return value</span></span>

<span data-ttu-id="fd666-117">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="fd666-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fd666-118">Constante</span><span class="sxs-lookup"><span data-stu-id="fd666-118">Constant</span></span>  |<span data-ttu-id="fd666-119">Valor</span><span class="sxs-lookup"><span data-stu-id="fd666-119">Value</span></span>  |<span data-ttu-id="fd666-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd666-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fd666-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fd666-121">0x80041008</span></span> | <span data-ttu-id="fd666-122">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="fd666-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="fd666-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="fd666-123">0x80041043</span></span> | <span data-ttu-id="fd666-124">O `[in, out]` especificado no parâmetro do método de *pInSignature* e *pOutSignature* objetos têm diferentes qualificadores.</span><span class="sxs-lookup"><span data-stu-id="fd666-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="fd666-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="fd666-125">0x80041036</span></span> | <span data-ttu-id="fd666-126">Um parâmetro de método não tem a especificação da **ID** qualificador.</span><span class="sxs-lookup"><span data-stu-id="fd666-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="fd666-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="fd666-127">0x80041038</span></span> | <span data-ttu-id="fd666-128">A série de ID que é atribuída aos parâmetros de método não é consecutiva ou não começam com 0.</span><span class="sxs-lookup"><span data-stu-id="fd666-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="fd666-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="fd666-129">0x80041039</span></span> | <span data-ttu-id="fd666-130">O valor de retorno de um método tem um **ID** qualificador.</span><span class="sxs-lookup"><span data-stu-id="fd666-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="fd666-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="fd666-131">0x80041034</span></span> | <span data-ttu-id="fd666-132">Foi feita uma tentativa de reutilizar um nome de método existente de uma classe pai, e as assinaturas não correspondeu.</span><span class="sxs-lookup"><span data-stu-id="fd666-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="fd666-133">0</span><span class="sxs-lookup"><span data-stu-id="fd666-133">0</span></span> | <span data-ttu-id="fd666-134">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="fd666-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="fd666-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd666-135">Remarks</span></span>

<span data-ttu-id="fd666-136">Essa função encapsula uma chamada para o [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="fd666-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="fd666-137">Esta chamada de método só terá suporte se `ptr` é uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="fd666-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="fd666-138">Manipulação de método não está disponível no [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) ponteiros que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="fd666-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="fd666-139">Os usuários não é possível criar métodos com nomes que podem começam ou terminam com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="fd666-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="fd666-140">Isso é reservado para propriedades e classes do sistema.</span><span class="sxs-lookup"><span data-stu-id="fd666-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="fd666-141">Para um método, o `in` e `out` parâmetros são descritos como propriedades na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objetos.</span><span class="sxs-lookup"><span data-stu-id="fd666-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="fd666-142">Um `[in/out]` parâmetro pode ser definido adicionando a mesma propriedade para os dois objetos apontados pelo `pInSignature` e `pOutSignature` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fd666-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="fd666-143">Nesse caso, as propriedades compartilham o mesmo **ID** valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="fd666-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="fd666-144">Cada propriedade em uma [Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) diferente do objeto de classe `ReturnValue` deve ter uma **ID** qualificador, um valor numérico de base zero que identifica a ordem na qual os parâmetros aparecem.</span><span class="sxs-lookup"><span data-stu-id="fd666-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="fd666-145">Não há dois parâmetros podem ter o mesmo **ID** valor e não **ID** valor pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="fd666-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="fd666-146">Se uma dessas condições ocorre, o `PutMethod` função retorna `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="fd666-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="fd666-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd666-147">Example</span></span>

<span data-ttu-id="fd666-148">Para obter um exemplo, consulte o [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="fd666-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd666-149">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd666-149">Requirements</span></span>  
 <span data-ttu-id="fd666-150">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd666-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd666-151">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fd666-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fd666-152">**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fd666-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd666-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd666-153">See also</span></span>  
[<span data-ttu-id="fd666-154">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="fd666-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
