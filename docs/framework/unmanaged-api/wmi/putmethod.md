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
ms.openlocfilehash: 74654cf18d87fed8ad5ce9a4cd4249d56fdb4343
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693445"
---
# <a name="putmethod-function"></a><span data-ttu-id="2a80a-103">Função PutMethod</span><span class="sxs-lookup"><span data-stu-id="2a80a-103">PutMethod function</span></span>
<span data-ttu-id="2a80a-104">Cria um método.</span><span class="sxs-lookup"><span data-stu-id="2a80a-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="2a80a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a80a-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="2a80a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a80a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2a80a-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="2a80a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2a80a-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="2a80a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="2a80a-109">[in] O nome do método para criar.</span><span class="sxs-lookup"><span data-stu-id="2a80a-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="2a80a-110">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="2a80a-110">[in] Reserved.</span></span> <span data-ttu-id="2a80a-111">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="2a80a-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="2a80a-112">[in] Um ponteiro para uma cópia do [classe de sistema de Parameters](/windows/desktop/WmiSdk/--parameters) que contém o `in` parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="2a80a-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="2a80a-113">Esse parâmetro será ignorado se definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="2a80a-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="2a80a-114">[in]  Um ponteiro para uma cópia do [classe de sistema de Parameters](/windows/desktop/WmiSdk/--parameters) que contém o `out` parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="2a80a-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="2a80a-115">Esse parâmetro será ignorado se definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="2a80a-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="2a80a-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2a80a-116">Return value</span></span>

<span data-ttu-id="2a80a-117">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="2a80a-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2a80a-118">Constante</span><span class="sxs-lookup"><span data-stu-id="2a80a-118">Constant</span></span>  |<span data-ttu-id="2a80a-119">Valor</span><span class="sxs-lookup"><span data-stu-id="2a80a-119">Value</span></span>  |<span data-ttu-id="2a80a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a80a-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2a80a-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2a80a-121">0x80041008</span></span> | <span data-ttu-id="2a80a-122">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="2a80a-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="2a80a-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="2a80a-123">0x80041043</span></span> | <span data-ttu-id="2a80a-124">O `[in, out]` parâmetro de método especificado em ambos os *pInSignature* e *pOutSignature* objetos têm qualificadores diferentes.</span><span class="sxs-lookup"><span data-stu-id="2a80a-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="2a80a-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="2a80a-125">0x80041036</span></span> | <span data-ttu-id="2a80a-126">Um parâmetro de método não tem a especificação do **ID** qualificador.</span><span class="sxs-lookup"><span data-stu-id="2a80a-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="2a80a-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="2a80a-127">0x80041038</span></span> | <span data-ttu-id="2a80a-128">A série de ID que é atribuída aos parâmetros de método não é consecutiva ou não inicia em 0.</span><span class="sxs-lookup"><span data-stu-id="2a80a-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="2a80a-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="2a80a-129">0x80041039</span></span> | <span data-ttu-id="2a80a-130">O valor de retorno para um método tem um **ID** qualificador.</span><span class="sxs-lookup"><span data-stu-id="2a80a-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="2a80a-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="2a80a-131">0x80041034</span></span> | <span data-ttu-id="2a80a-132">Foi feita uma tentativa de reutilizar um nome de método existente de uma classe pai, e as assinaturas não correspondem.</span><span class="sxs-lookup"><span data-stu-id="2a80a-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2a80a-133">0</span><span class="sxs-lookup"><span data-stu-id="2a80a-133">0</span></span> | <span data-ttu-id="2a80a-134">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2a80a-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="2a80a-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a80a-135">Remarks</span></span>

<span data-ttu-id="2a80a-136">Essa função encapsula uma chamada para o [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) método.</span><span class="sxs-lookup"><span data-stu-id="2a80a-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="2a80a-137">Esta chamada de método só tem suporte se `ptr` é uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="2a80a-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="2a80a-138">Manipulação de método não está disponível no [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponteiros que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="2a80a-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="2a80a-139">Os usuários não é possível criar métodos com nomes que começam ou terminam com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="2a80a-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="2a80a-140">Isso é reservado para as propriedades e classes do sistema.</span><span class="sxs-lookup"><span data-stu-id="2a80a-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="2a80a-141">Para um método, o `in` e `out` parâmetros são descritos como propriedades nas [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objetos.</span><span class="sxs-lookup"><span data-stu-id="2a80a-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="2a80a-142">Uma `[in/out]` parâmetro pode ser definido, adicionando a mesma propriedade para ambos os objetos apontados pela `pInSignature` e `pOutSignature` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2a80a-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="2a80a-143">Nesse caso, as propriedades compartilham o mesmo **ID** valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="2a80a-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="2a80a-144">Cada propriedade em uma [Parameters](/windows/desktop/WmiSdk/--parameters) diferente de objeto de classe `ReturnValue` deve ter um **ID** qualificador, um valor numérico de base zero que identifica a ordem na qual os parâmetros aparecem.</span><span class="sxs-lookup"><span data-stu-id="2a80a-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="2a80a-145">Não há dois parâmetros podem ter o mesmo **identificação** valor e não **ID** valor pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="2a80a-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="2a80a-146">Se uma dessas condições ocorre, o `PutMethod` retornos de função `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="2a80a-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="2a80a-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a80a-147">Example</span></span>

<span data-ttu-id="2a80a-148">Por exemplo, consulte o [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) método.</span><span class="sxs-lookup"><span data-stu-id="2a80a-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a80a-149">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a80a-149">Requirements</span></span>  
 <span data-ttu-id="2a80a-150">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a80a-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a80a-151">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2a80a-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2a80a-152">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2a80a-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a80a-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a80a-153">See also</span></span>
- [<span data-ttu-id="2a80a-154">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="2a80a-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
