---
title: "Função CompareTo (referência de API não gerenciada)"
description: "A função CompareTo compara um objeto com outro objeto WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 038074b5bb3adc816caa226d3167395758d2ae57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="compareto-function"></a><span data-ttu-id="f5517-103">Função CompareTo</span><span class="sxs-lookup"><span data-stu-id="f5517-103">CompareTo function</span></span>
<span data-ttu-id="f5517-104">Compara a um objeto para outro objeto de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="f5517-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f5517-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5517-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f5517-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5517-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f5517-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="f5517-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f5517-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="f5517-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`flags`  
<span data-ttu-id="f5517-109">[in] Uma combinação bit a bit dos sinalizadores que especificam as características de objeto a serem considerados para a comparação.</span><span class="sxs-lookup"><span data-stu-id="f5517-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="f5517-110">Consulte o [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f5517-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="f5517-111">[in] O objeto para comparação.</span><span class="sxs-lookup"><span data-stu-id="f5517-111">[in] The object for comparison.</span></span> <span data-ttu-id="f5517-112">`pcompareTo`deve ser um válido [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância; ele não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f5517-112">`pcompareTo` must be a valid [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5517-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f5517-113">Return value</span></span>

<span data-ttu-id="f5517-114">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="f5517-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f5517-115">Constante</span><span class="sxs-lookup"><span data-stu-id="f5517-115">Constant</span></span>  |<span data-ttu-id="f5517-116">Valor</span><span class="sxs-lookup"><span data-stu-id="f5517-116">Value</span></span>  |<span data-ttu-id="f5517-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5517-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="f5517-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f5517-118">0x80041001</span></span> | <span data-ttu-id="f5517-119">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="f5517-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f5517-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f5517-120">0x80041008</span></span> | <span data-ttu-id="f5517-121">Um parâmetro é inválido.</span><span class="sxs-lookup"><span data-stu-id="f5517-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="f5517-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f5517-122">0x8004101d</span></span> | <span data-ttu-id="f5517-123">Uma segunda chamada para `BeginEnumeration` foi feita sem uma chamada intermediária para [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f5517-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f5517-124">0</span><span class="sxs-lookup"><span data-stu-id="f5517-124">0</span></span> | <span data-ttu-id="f5517-125">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f5517-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="f5517-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="f5517-126">0x40003</span></span> | <span data-ttu-id="f5517-127">Os objetos são diferentes.</span><span class="sxs-lookup"><span data-stu-id="f5517-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="f5517-128">0</span><span class="sxs-lookup"><span data-stu-id="f5517-128">0</span></span> | <span data-ttu-id="f5517-129">Os objetos são os mesmos, com base nos sinalizadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="f5517-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f5517-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5517-130">Remarks</span></span>

<span data-ttu-id="f5517-131">Essa função encapsula uma chamada para o [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="f5517-131">This function wraps a call to the [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f5517-132">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="f5517-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="f5517-133">Você pode especificar as características individuais envolvido na comparação com a especificação de uma combinação bit a bit dos sinalizadores a seguir:</span><span class="sxs-lookup"><span data-stu-id="f5517-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="f5517-134">Constante</span><span class="sxs-lookup"><span data-stu-id="f5517-134">Constant</span></span>  |<span data-ttu-id="f5517-135">Valor</span><span class="sxs-lookup"><span data-stu-id="f5517-135">Value</span></span>  |<span data-ttu-id="f5517-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5517-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="f5517-137">2</span><span class="sxs-lookup"><span data-stu-id="f5517-137">2</span></span> | <span data-ttu-id="f5517-138">Ignore o origem (o servidor e o namespace que de onde vieram).</span><span class="sxs-lookup"><span data-stu-id="f5517-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="f5517-139">1</span><span class="sxs-lookup"><span data-stu-id="f5517-139">1</span></span> | <span data-ttu-id="f5517-140">Ignorar todos os qualificadores (incluindo **chave** e **dinâmico**)</span><span class="sxs-lookup"><span data-stu-id="f5517-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="f5517-141">4</span><span class="sxs-lookup"><span data-stu-id="f5517-141">4</span></span> | <span data-ttu-id="f5517-142">Ignore valores padrão das propriedades.</span><span class="sxs-lookup"><span data-stu-id="f5517-142">Ignore default values of properties.</span></span> <span data-ttu-id="f5517-143">Esse sinalizador só se aplica a comparação de classes.</span><span class="sxs-lookup"><span data-stu-id="f5517-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="f5517-144">0x20</span><span class="sxs-lookup"><span data-stu-id="f5517-144">0x20</span></span> | <span data-ttu-id="f5517-145">Ignore tipos de qualificadores.</span><span class="sxs-lookup"><span data-stu-id="f5517-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="f5517-146">Este sinalizador ainda considera qualificadores, mas ignora diferenças de tipo, como regras de propagação e substituir as restrições.</span><span class="sxs-lookup"><span data-stu-id="f5517-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="f5517-147">0x10</span><span class="sxs-lookup"><span data-stu-id="f5517-147">0x10</span></span> | <span data-ttu-id="f5517-148">Ignore maiusculas e minúsculas na comparação de valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f5517-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="f5517-149">Isso se aplica a cadeias de caracteres e valores de qualificador.</span><span class="sxs-lookup"><span data-stu-id="f5517-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="f5517-150">A comparação de nomes de propriedade e qualificador sempre diferencia maiusculas de minúsculas, independentemente de se esse sinalizador é definido.</span><span class="sxs-lookup"><span data-stu-id="f5517-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="f5517-151">0x8</span><span class="sxs-lookup"><span data-stu-id="f5517-151">0x8</span></span> | <span data-ttu-id="f5517-152">Suponha que os objetos que estão sendo comparados são instâncias da mesma classe.</span><span class="sxs-lookup"><span data-stu-id="f5517-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="f5517-153">Consequentemente, esse sinalizador compara somente informações relacionadas à instância.</span><span class="sxs-lookup"><span data-stu-id="f5517-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="f5517-154">Use este sinalizadores para otimizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f5517-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="f5517-155">Se os objetos não são da mesma classe, os resultados são indefinidos.</span><span class="sxs-lookup"><span data-stu-id="f5517-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="f5517-156">Ou você pode especificar um único sinalizador composto da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f5517-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="f5517-157">Constante</span><span class="sxs-lookup"><span data-stu-id="f5517-157">Constant</span></span>  |<span data-ttu-id="f5517-158">Valor</span><span class="sxs-lookup"><span data-stu-id="f5517-158">Value</span></span>  |<span data-ttu-id="f5517-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5517-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="f5517-160">0</span><span class="sxs-lookup"><span data-stu-id="f5517-160">0</span></span> | <span data-ttu-id="f5517-161">Considere a possibilidade de todos os recursos na comparação.</span><span class="sxs-lookup"><span data-stu-id="f5517-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="f5517-162">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5517-162">Requirements</span></span>  
 <span data-ttu-id="f5517-163">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5517-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5517-164">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f5517-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f5517-165">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f5517-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5517-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5517-166">See also</span></span>  
[<span data-ttu-id="f5517-167">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="f5517-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
