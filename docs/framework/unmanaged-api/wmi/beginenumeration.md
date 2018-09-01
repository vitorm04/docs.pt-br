---
title: Função BeginEnumeration (referência de API não gerenciada)
description: A função BeginEnumeration redefine um enumerador para o início da enumeração
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08406f7d93671b406b3c7cd8719a7a0e5e423184
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392351"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="1806c-103">Função BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="1806c-103">BeginEnumeration function</span></span>
<span data-ttu-id="1806c-104">Redefine um enumerador para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="1806c-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1806c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1806c-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="1806c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1806c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1806c-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="1806c-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="1806c-108">`ptr` [in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="1806c-108">`ptr` [in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="1806c-109">[in] Uma combinação bit a bit de sinalizadores ou valores descritos na [comentários](#remarks) seção que controla as propriedades incluídas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="1806c-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="1806c-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1806c-110">Return value</span></span>

<span data-ttu-id="1806c-111">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="1806c-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1806c-112">Constante</span><span class="sxs-lookup"><span data-stu-id="1806c-112">Constant</span></span>  |<span data-ttu-id="1806c-113">Valor</span><span class="sxs-lookup"><span data-stu-id="1806c-113">Value</span></span>  |<span data-ttu-id="1806c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1806c-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1806c-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1806c-115">0x80041008</span></span> | <span data-ttu-id="1806c-116">A combinação de sinalizadores no `lEnumFlags` é inválido ou inválido argumento foi especificado.</span><span class="sxs-lookup"><span data-stu-id="1806c-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="1806c-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="1806c-117">0x8004101d</span></span> | <span data-ttu-id="1806c-118">Uma segunda chamada para `BeginEnumeration` foi feita sem uma chamada intermediária para [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1806c-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1806c-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1806c-119">0x80041006</span></span> | <span data-ttu-id="1806c-120">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="1806c-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1806c-121">0</span><span class="sxs-lookup"><span data-stu-id="1806c-121">0</span></span> | <span data-ttu-id="1806c-122">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="1806c-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1806c-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="1806c-123">Remarks</span></span>

<span data-ttu-id="1806c-124">Essa função encapsula uma chamada para o [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) método.</span><span class="sxs-lookup"><span data-stu-id="1806c-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="1806c-125">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="1806c-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="1806c-126">Você pode combinar um sinalizador de cada grupo com qualquer sinalizador de nenhum outro grupo.</span><span class="sxs-lookup"><span data-stu-id="1806c-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="1806c-127">No entanto, os sinalizadores do mesmo grupo são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="1806c-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="1806c-128">**Grupo 1**</span><span class="sxs-lookup"><span data-stu-id="1806c-128">**Group 1**</span></span>

|<span data-ttu-id="1806c-129">Constante</span><span class="sxs-lookup"><span data-stu-id="1806c-129">Constant</span></span>  |<span data-ttu-id="1806c-130">Valor</span><span class="sxs-lookup"><span data-stu-id="1806c-130">Value</span></span>  |<span data-ttu-id="1806c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="1806c-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="1806c-132">0x4</span><span class="sxs-lookup"><span data-stu-id="1806c-132">0x4</span></span> | <span data-ttu-id="1806c-133">Incluem propriedades que constituem a chave somente.</span><span class="sxs-lookup"><span data-stu-id="1806c-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="1806c-134">0x8</span><span class="sxs-lookup"><span data-stu-id="1806c-134">0x8</span></span> | <span data-ttu-id="1806c-135">Incluem propriedades que são somente referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="1806c-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="1806c-136">**Grupo 2**</span><span class="sxs-lookup"><span data-stu-id="1806c-136">**Group 2**</span></span>

<span data-ttu-id="1806c-137">Constante</span><span class="sxs-lookup"><span data-stu-id="1806c-137">Constant</span></span>  |<span data-ttu-id="1806c-138">Valor</span><span class="sxs-lookup"><span data-stu-id="1806c-138">Value</span></span>  |<span data-ttu-id="1806c-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="1806c-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="1806c-140">0x30</span><span class="sxs-lookup"><span data-stu-id="1806c-140">0x30</span></span> | <span data-ttu-id="1806c-141">Limite a enumeração para apenas as propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="1806c-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="1806c-142">0x40</span><span class="sxs-lookup"><span data-stu-id="1806c-142">0x40</span></span> | <span data-ttu-id="1806c-143">Inclui propriedades locais e propagadas mas exclui as propriedades do sistema da enumeração.</span><span class="sxs-lookup"><span data-stu-id="1806c-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="1806c-144">Para classes:</span><span class="sxs-lookup"><span data-stu-id="1806c-144">For classes:</span></span>

<span data-ttu-id="1806c-145">Constante</span><span class="sxs-lookup"><span data-stu-id="1806c-145">Constant</span></span>  |<span data-ttu-id="1806c-146">Valor</span><span class="sxs-lookup"><span data-stu-id="1806c-146">Value</span></span>  |<span data-ttu-id="1806c-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="1806c-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="1806c-148">0x100</span><span class="sxs-lookup"><span data-stu-id="1806c-148">0x100</span></span> | <span data-ttu-id="1806c-149">Limite a enumeração a ser substituído na definição de classe de propriedades.</span><span class="sxs-lookup"><span data-stu-id="1806c-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="1806c-150">0x100</span><span class="sxs-lookup"><span data-stu-id="1806c-150">0x100</span></span> | <span data-ttu-id="1806c-151">Limite a enumeração para propriedades substituídas na definição de classe atual e novas propriedades definidas na classe.</span><span class="sxs-lookup"><span data-stu-id="1806c-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="1806c-152">0x300</span><span class="sxs-lookup"><span data-stu-id="1806c-152">0x300</span></span> | <span data-ttu-id="1806c-153">A máscara (em vez de um sinalizador) a ser aplicado em relação a um `lEnumFlags` valor para verificar se qualquer um dos `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` está definido.</span><span class="sxs-lookup"><span data-stu-id="1806c-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="1806c-154">0x10</span><span class="sxs-lookup"><span data-stu-id="1806c-154">0x10</span></span> | <span data-ttu-id="1806c-155">Limite a enumeração para propriedades que são definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="1806c-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="1806c-156">0x20</span><span class="sxs-lookup"><span data-stu-id="1806c-156">0x20</span></span> | <span data-ttu-id="1806c-157">Limite a enumeração para propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="1806c-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="1806c-158">Para instâncias:</span><span class="sxs-lookup"><span data-stu-id="1806c-158">For instances:</span></span>

<span data-ttu-id="1806c-159">Constante</span><span class="sxs-lookup"><span data-stu-id="1806c-159">Constant</span></span>  |<span data-ttu-id="1806c-160">Valor</span><span class="sxs-lookup"><span data-stu-id="1806c-160">Value</span></span>  |<span data-ttu-id="1806c-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="1806c-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="1806c-162">0x10</span><span class="sxs-lookup"><span data-stu-id="1806c-162">0x10</span></span> | <span data-ttu-id="1806c-163">Limite a enumeração para propriedades que são definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="1806c-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="1806c-164">0x20</span><span class="sxs-lookup"><span data-stu-id="1806c-164">0x20</span></span> | <span data-ttu-id="1806c-165">Limite a enumeração para propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="1806c-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |


## <a name="requirements"></a><span data-ttu-id="1806c-166">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1806c-166">Requirements</span></span>  
 <span data-ttu-id="1806c-167">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1806c-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1806c-168">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1806c-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1806c-169">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1806c-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1806c-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1806c-170">See also</span></span>  
[<span data-ttu-id="1806c-171">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="1806c-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
