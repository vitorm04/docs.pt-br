---
title: Função PutMethod (referência a PiPI não gerenciada)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174908"
---
# <a name="putmethod-function"></a><span data-ttu-id="6a393-103">Função PutMethod</span><span class="sxs-lookup"><span data-stu-id="6a393-103">PutMethod function</span></span>
<span data-ttu-id="6a393-104">Cria um método.</span><span class="sxs-lookup"><span data-stu-id="6a393-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6a393-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a393-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="6a393-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a393-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6a393-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="6a393-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6a393-108">[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="6a393-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="6a393-109">[em] O nome do método para criar.</span><span class="sxs-lookup"><span data-stu-id="6a393-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="6a393-110">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="6a393-110">[in] Reserved.</span></span> <span data-ttu-id="6a393-111">Este parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="6a393-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="6a393-112">[em] Um ponteiro para uma cópia da classe `in` do sistema [__Parameters](/windows/desktop/WmiSdk/--parameters) que contém os parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="6a393-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="6a393-113">Este parâmetro é ignorado se `null`definido como .</span><span class="sxs-lookup"><span data-stu-id="6a393-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="6a393-114">[em]  Um ponteiro para uma cópia da classe `out` do sistema [__Parameters](/windows/desktop/WmiSdk/--parameters) que contém os parâmetros para o método.</span><span class="sxs-lookup"><span data-stu-id="6a393-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="6a393-115">Este parâmetro é ignorado se `null`definido como .</span><span class="sxs-lookup"><span data-stu-id="6a393-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="6a393-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6a393-116">Return value</span></span>

<span data-ttu-id="6a393-117">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="6a393-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6a393-118">Constante</span><span class="sxs-lookup"><span data-stu-id="6a393-118">Constant</span></span>  |<span data-ttu-id="6a393-119">Valor</span><span class="sxs-lookup"><span data-stu-id="6a393-119">Value</span></span>  |<span data-ttu-id="6a393-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a393-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6a393-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6a393-121">0x80041008</span></span> | <span data-ttu-id="6a393-122">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="6a393-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="6a393-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="6a393-123">0x80041043</span></span> | <span data-ttu-id="6a393-124">O `[in, out]` parâmetro de método especificado nos objetos *pInSignature* e *pOutSignature* tem qualificações diferentes.</span><span class="sxs-lookup"><span data-stu-id="6a393-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="6a393-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="6a393-125">0x80041036</span></span> | <span data-ttu-id="6a393-126">Um parâmetro de método está faltando a especificação do qualificador de **ID.**</span><span class="sxs-lookup"><span data-stu-id="6a393-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="6a393-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="6a393-127">0x80041038</span></span> | <span data-ttu-id="6a393-128">A série ID atribuída aos parâmetros do método não é consecutiva ou não começa em 0.</span><span class="sxs-lookup"><span data-stu-id="6a393-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="6a393-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="6a393-129">0x80041039</span></span> | <span data-ttu-id="6a393-130">O valor de retorno para um método tem um qualificador **de ID.**</span><span class="sxs-lookup"><span data-stu-id="6a393-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="6a393-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="6a393-131">0x80041034</span></span> | <span data-ttu-id="6a393-132">Uma tentativa foi feita para reutilizar um nome de método existente de uma classe pai, e as assinaturas não coincidiram.</span><span class="sxs-lookup"><span data-stu-id="6a393-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6a393-133">0</span><span class="sxs-lookup"><span data-stu-id="6a393-133">0</span></span> | <span data-ttu-id="6a393-134">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6a393-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="6a393-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a393-135">Remarks</span></span>

<span data-ttu-id="6a393-136">Esta função envolve uma chamada para o método [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)</span><span class="sxs-lookup"><span data-stu-id="6a393-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="6a393-137">Esta chamada de método `ptr` só é suportada se for uma definição de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="6a393-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="6a393-138">A manipulação do método não está disponível a partir de ponteiros [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="6a393-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="6a393-139">Os usuários não podem criar métodos com nomes que começam ou terminam com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="6a393-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="6a393-140">Isso é reservado para classes e propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="6a393-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="6a393-141">Para um método, os `in` parâmetros e `out` parâmetros são descritos como propriedades em objetos [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="6a393-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="6a393-142">Um `[in/out]` parâmetro pode ser definido adicionando a mesma propriedade `pInSignature` `pOutSignature` a ambos os objetos apontados pelos parâmetros e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6a393-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="6a393-143">Neste caso, as propriedades compartilham o mesmo valor de qualificação **de ID.**</span><span class="sxs-lookup"><span data-stu-id="6a393-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="6a393-144">Cada propriedade em um objeto `ReturnValue` de classe [__Parameters](/windows/desktop/WmiSdk/--parameters) que não seja deve ter um qualificador de **identificação,** um valor numérico baseado em zero que identifica a ordem em que os parâmetros aparecem.</span><span class="sxs-lookup"><span data-stu-id="6a393-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="6a393-145">Nenhum dos dois parâmetros pode ter o mesmo valor **de ID,** e nenhum valor **de ID** pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="6a393-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="6a393-146">Se ocorrer qualquer `PutMethod` condição, `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`a função retorna .</span><span class="sxs-lookup"><span data-stu-id="6a393-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="6a393-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a393-147">Example</span></span>

<span data-ttu-id="6a393-148">Por exemplo, consulte o método [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)</span><span class="sxs-lookup"><span data-stu-id="6a393-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a393-149">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a393-149">Requirements</span></span>  
 <span data-ttu-id="6a393-150">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a393-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a393-151">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6a393-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6a393-152">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6a393-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a393-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="6a393-153">See also</span></span>

- [<span data-ttu-id="6a393-154">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="6a393-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
