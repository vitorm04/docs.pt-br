---
title: Função CompareTo (referência de API não gerenciada)
description: A função CompareTo compara um objeto com outro objeto WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d210795016cd2e0179b902a224ca0c62f4ac01f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128706"
---
# <a name="compareto-function"></a><span data-ttu-id="39d3c-103">Função CompareTo</span><span class="sxs-lookup"><span data-stu-id="39d3c-103">CompareTo function</span></span>

<span data-ttu-id="39d3c-104">Compara um objeto a outro objeto de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="39d3c-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="39d3c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39d3c-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="39d3c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39d3c-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="39d3c-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="39d3c-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="39d3c-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="39d3c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="39d3c-109">no Uma combinação de bits de bit que especifica as características do objeto a serem consideradas para a comparação.</span><span class="sxs-lookup"><span data-stu-id="39d3c-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="39d3c-110">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="39d3c-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="39d3c-111">no O objeto para comparação.</span><span class="sxs-lookup"><span data-stu-id="39d3c-111">[in] The object for comparison.</span></span> <span data-ttu-id="39d3c-112">`pCompareTo` deve ser uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) válida; Não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="39d3c-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="39d3c-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="39d3c-113">Return value</span></span>

<span data-ttu-id="39d3c-114">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="39d3c-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="39d3c-115">Constante</span><span class="sxs-lookup"><span data-stu-id="39d3c-115">Constant</span></span>  |<span data-ttu-id="39d3c-116">Valor</span><span class="sxs-lookup"><span data-stu-id="39d3c-116">Value</span></span>  |<span data-ttu-id="39d3c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="39d3c-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="39d3c-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="39d3c-118">0x80041001</span></span> | <span data-ttu-id="39d3c-119">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="39d3c-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="39d3c-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="39d3c-120">0x80041008</span></span> | <span data-ttu-id="39d3c-121">Um parâmetro é inválido.</span><span class="sxs-lookup"><span data-stu-id="39d3c-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="39d3c-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="39d3c-122">0x8004101d</span></span> | <span data-ttu-id="39d3c-123">Uma segunda chamada para `BeginEnumeration` foi feita sem uma chamada intermediária para [`EndEnumeration`](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="39d3c-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="39d3c-124">0</span><span class="sxs-lookup"><span data-stu-id="39d3c-124">0</span></span> | <span data-ttu-id="39d3c-125">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="39d3c-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="39d3c-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="39d3c-126">0x40003</span></span> | <span data-ttu-id="39d3c-127">Os objetos são diferentes.</span><span class="sxs-lookup"><span data-stu-id="39d3c-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="39d3c-128">0</span><span class="sxs-lookup"><span data-stu-id="39d3c-128">0</span></span> | <span data-ttu-id="39d3c-129">Os objetos são os mesmos com base nos sinalizadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="39d3c-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="39d3c-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="39d3c-130">Remarks</span></span>

<span data-ttu-id="39d3c-131">Essa função encapsula uma chamada para o método [IWbemClassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .</span><span class="sxs-lookup"><span data-stu-id="39d3c-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="39d3c-132">Os sinalizadores que podem ser passados como o argumento `lEnumFlags` são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="39d3c-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="39d3c-133">Você pode especificar as características individuais envolvidas na comparação, especificando uma combinação bit a bit dos seguintes sinalizadores:</span><span class="sxs-lookup"><span data-stu-id="39d3c-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="39d3c-134">Constante</span><span class="sxs-lookup"><span data-stu-id="39d3c-134">Constant</span></span>  |<span data-ttu-id="39d3c-135">Valor</span><span class="sxs-lookup"><span data-stu-id="39d3c-135">Value</span></span>  |<span data-ttu-id="39d3c-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="39d3c-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="39d3c-137">2</span><span class="sxs-lookup"><span data-stu-id="39d3c-137">2</span></span> | <span data-ttu-id="39d3c-138">Ignorar a origem (o servidor e o namespace do qual vieram).</span><span class="sxs-lookup"><span data-stu-id="39d3c-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="39d3c-139">1</span><span class="sxs-lookup"><span data-stu-id="39d3c-139">1</span></span> | <span data-ttu-id="39d3c-140">Ignorar todos os qualificadores (incluindo **chave** e **dinâmica**)</span><span class="sxs-lookup"><span data-stu-id="39d3c-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="39d3c-141">4</span><span class="sxs-lookup"><span data-stu-id="39d3c-141">4</span></span> | <span data-ttu-id="39d3c-142">Ignorar valores padrão de propriedades.</span><span class="sxs-lookup"><span data-stu-id="39d3c-142">Ignore default values of properties.</span></span> <span data-ttu-id="39d3c-143">Esse sinalizador se aplica somente à comparação de classes.</span><span class="sxs-lookup"><span data-stu-id="39d3c-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="39d3c-144">0x20</span><span class="sxs-lookup"><span data-stu-id="39d3c-144">0x20</span></span> | <span data-ttu-id="39d3c-145">Ignore os tipos de qualificador.</span><span class="sxs-lookup"><span data-stu-id="39d3c-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="39d3c-146">Esse sinalizador ainda usa qualificadores em conta, mas ignora as distinções de flavor, como regras de propagação e restrições de substituição.</span><span class="sxs-lookup"><span data-stu-id="39d3c-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="39d3c-147">0x10</span><span class="sxs-lookup"><span data-stu-id="39d3c-147">0x10</span></span> | <span data-ttu-id="39d3c-148">Ignorar maiúsculas na comparação de valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="39d3c-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="39d3c-149">Isso se aplica tanto a cadeias de caracteres quanto a valores de qualificador.</span><span class="sxs-lookup"><span data-stu-id="39d3c-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="39d3c-150">A comparação dos nomes de propriedade e qualificador sempre diferencia maiúsculas de minúsculas, independentemente de o sinalizador ser definido ou não.</span><span class="sxs-lookup"><span data-stu-id="39d3c-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="39d3c-151">0x8</span><span class="sxs-lookup"><span data-stu-id="39d3c-151">0x8</span></span> | <span data-ttu-id="39d3c-152">Suponha que os objetos que estão sendo comparados sejam instâncias da mesma classe.</span><span class="sxs-lookup"><span data-stu-id="39d3c-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="39d3c-153">Consequentemente, esse sinalizador compara apenas informações relacionadas à instância.</span><span class="sxs-lookup"><span data-stu-id="39d3c-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="39d3c-154">Use esses sinalizadores para otimizar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="39d3c-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="39d3c-155">Se os objetos não são da mesma classe, os resultados são indefinidos.</span><span class="sxs-lookup"><span data-stu-id="39d3c-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="39d3c-156">Ou você pode especificar um único sinalizador composto da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="39d3c-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="39d3c-157">Constante</span><span class="sxs-lookup"><span data-stu-id="39d3c-157">Constant</span></span>  |<span data-ttu-id="39d3c-158">Valor</span><span class="sxs-lookup"><span data-stu-id="39d3c-158">Value</span></span>  |<span data-ttu-id="39d3c-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="39d3c-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="39d3c-160">0</span><span class="sxs-lookup"><span data-stu-id="39d3c-160">0</span></span> | <span data-ttu-id="39d3c-161">Considere todos os recursos na comparação.</span><span class="sxs-lookup"><span data-stu-id="39d3c-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="39d3c-162">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39d3c-162">Requirements</span></span>

<span data-ttu-id="39d3c-163">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39d3c-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="39d3c-164">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="39d3c-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="39d3c-165">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="39d3c-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="39d3c-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39d3c-166">See also</span></span>

- [<span data-ttu-id="39d3c-167">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="39d3c-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
