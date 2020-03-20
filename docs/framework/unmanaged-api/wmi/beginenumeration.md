---
title: Função startEnumeration (referência de API não gerenciada)
description: A função StartEnumeration redefine um enumerador para o início da enumeração
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176871"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="bc25e-103">Função BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="bc25e-103">BeginEnumeration function</span></span>
<span data-ttu-id="bc25e-104">Redefine um enumerador de volta ao início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc25e-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bc25e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc25e-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="bc25e-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc25e-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="bc25e-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="bc25e-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="bc25e-108">[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="bc25e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="bc25e-109">[em] Uma combinação bitwise dos sinalizadores ou valores descritos na seção Observações que [controla](#remarks) as propriedades incluídas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc25e-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc25e-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bc25e-110">Return value</span></span>

<span data-ttu-id="bc25e-111">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="bc25e-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bc25e-112">Constante</span><span class="sxs-lookup"><span data-stu-id="bc25e-112">Constant</span></span>  |<span data-ttu-id="bc25e-113">Valor</span><span class="sxs-lookup"><span data-stu-id="bc25e-113">Value</span></span>  |<span data-ttu-id="bc25e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc25e-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bc25e-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bc25e-115">0x80041008</span></span> | <span data-ttu-id="bc25e-116">A combinação de `lEnumFlags` sinalizadores em é inválida, ou um argumento inválido foi especificado.</span><span class="sxs-lookup"><span data-stu-id="bc25e-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="bc25e-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="bc25e-117">0x8004101d</span></span> | <span data-ttu-id="bc25e-118">Uma segunda `BeginEnumeration` chamada foi feita sem [`EndEnumeration`](endenumeration.md)uma chamada intervindo para .</span><span class="sxs-lookup"><span data-stu-id="bc25e-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bc25e-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bc25e-119">0x80041006</span></span> | <span data-ttu-id="bc25e-120">Não há memória suficiente disponível para começar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc25e-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bc25e-121">0</span><span class="sxs-lookup"><span data-stu-id="bc25e-121">0</span></span> | <span data-ttu-id="bc25e-122">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="bc25e-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bc25e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc25e-123">Remarks</span></span>

<span data-ttu-id="bc25e-124">Esta função envolve uma chamada para o [método IWbemClassObject::BeginEnumeration.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="bc25e-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="bc25e-125">As bandeiras que podem `lEnumFlags` ser passadas à medida que o argumento são definidas no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-las como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="bc25e-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="bc25e-126">Você pode combinar uma bandeira de cada grupo com qualquer bandeira de qualquer outro grupo.</span><span class="sxs-lookup"><span data-stu-id="bc25e-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="bc25e-127">No entanto, bandeiras do mesmo grupo são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="bc25e-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="bc25e-128">**Grupo 1**</span><span class="sxs-lookup"><span data-stu-id="bc25e-128">**Group 1**</span></span>

|<span data-ttu-id="bc25e-129">Constante</span><span class="sxs-lookup"><span data-stu-id="bc25e-129">Constant</span></span>  |<span data-ttu-id="bc25e-130">Valor</span><span class="sxs-lookup"><span data-stu-id="bc25e-130">Value</span></span>  |<span data-ttu-id="bc25e-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc25e-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="bc25e-132">0x4</span><span class="sxs-lookup"><span data-stu-id="bc25e-132">0x4</span></span> | <span data-ttu-id="bc25e-133">Inclua propriedades que constituem apenas a chave.</span><span class="sxs-lookup"><span data-stu-id="bc25e-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="bc25e-134">0x8</span><span class="sxs-lookup"><span data-stu-id="bc25e-134">0x8</span></span> | <span data-ttu-id="bc25e-135">Inclua propriedades que são apenas referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="bc25e-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="bc25e-136">**Grupo 2**</span><span class="sxs-lookup"><span data-stu-id="bc25e-136">**Group 2**</span></span>

<span data-ttu-id="bc25e-137">Constante</span><span class="sxs-lookup"><span data-stu-id="bc25e-137">Constant</span></span>  |<span data-ttu-id="bc25e-138">Valor</span><span class="sxs-lookup"><span data-stu-id="bc25e-138">Value</span></span>  |<span data-ttu-id="bc25e-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc25e-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="bc25e-140">0x30</span><span class="sxs-lookup"><span data-stu-id="bc25e-140">0x30</span></span> | <span data-ttu-id="bc25e-141">Limitar a enumeração apenas às propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="bc25e-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="bc25e-142">0x40</span><span class="sxs-lookup"><span data-stu-id="bc25e-142">0x40</span></span> | <span data-ttu-id="bc25e-143">Inclua propriedades locais e propagadas, mas exclua propriedades do sistema da enumeração.</span><span class="sxs-lookup"><span data-stu-id="bc25e-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="bc25e-144">Para aulas:</span><span class="sxs-lookup"><span data-stu-id="bc25e-144">For classes:</span></span>

<span data-ttu-id="bc25e-145">Constante</span><span class="sxs-lookup"><span data-stu-id="bc25e-145">Constant</span></span>  |<span data-ttu-id="bc25e-146">Valor</span><span class="sxs-lookup"><span data-stu-id="bc25e-146">Value</span></span>  |<span data-ttu-id="bc25e-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc25e-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="bc25e-148">0x100</span><span class="sxs-lookup"><span data-stu-id="bc25e-148">0x100</span></span> | <span data-ttu-id="bc25e-149">Limitar a enumeração a propriedades substituídas na definição da classe.</span><span class="sxs-lookup"><span data-stu-id="bc25e-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="bc25e-150">0x100</span><span class="sxs-lookup"><span data-stu-id="bc25e-150">0x100</span></span> | <span data-ttu-id="bc25e-151">Limitar a enumeração a propriedades substituídas na definição de classe atual e a novas propriedades definidas na classe.</span><span class="sxs-lookup"><span data-stu-id="bc25e-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="bc25e-152">0x300</span><span class="sxs-lookup"><span data-stu-id="bc25e-152">0x300</span></span> | <span data-ttu-id="bc25e-153">Uma máscara (em vez de um `lEnumFlags` sinalizador) para `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` aplicar contra um valor para verificar se está ou está definido.</span><span class="sxs-lookup"><span data-stu-id="bc25e-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="bc25e-154">0x10</span><span class="sxs-lookup"><span data-stu-id="bc25e-154">0x10</span></span> | <span data-ttu-id="bc25e-155">Limitar a enumeração a propriedades definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="bc25e-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="bc25e-156">0x20</span><span class="sxs-lookup"><span data-stu-id="bc25e-156">0x20</span></span> | <span data-ttu-id="bc25e-157">Limitar a enumeração a propriedades herdadas das classes básicas.</span><span class="sxs-lookup"><span data-stu-id="bc25e-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="bc25e-158">Para exemplos:</span><span class="sxs-lookup"><span data-stu-id="bc25e-158">For instances:</span></span>

<span data-ttu-id="bc25e-159">Constante</span><span class="sxs-lookup"><span data-stu-id="bc25e-159">Constant</span></span>  |<span data-ttu-id="bc25e-160">Valor</span><span class="sxs-lookup"><span data-stu-id="bc25e-160">Value</span></span>  |<span data-ttu-id="bc25e-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc25e-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="bc25e-162">0x10</span><span class="sxs-lookup"><span data-stu-id="bc25e-162">0x10</span></span> | <span data-ttu-id="bc25e-163">Limitar a enumeração a propriedades definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="bc25e-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="bc25e-164">0x20</span><span class="sxs-lookup"><span data-stu-id="bc25e-164">0x20</span></span> | <span data-ttu-id="bc25e-165">Limitar a enumeração a propriedades herdadas das classes básicas.</span><span class="sxs-lookup"><span data-stu-id="bc25e-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="bc25e-166">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc25e-166">Requirements</span></span>  
 <span data-ttu-id="bc25e-167">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc25e-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc25e-168">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bc25e-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bc25e-169">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bc25e-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc25e-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc25e-170">See also</span></span>

- [<span data-ttu-id="bc25e-171">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="bc25e-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
