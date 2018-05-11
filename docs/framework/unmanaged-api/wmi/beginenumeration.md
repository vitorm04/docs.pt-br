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
ms.openlocfilehash: 9699f0cfc4e9fdb989337681b164cc1e703c1e60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="beginenumeration-function"></a><span data-ttu-id="34768-103">Função BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="34768-103">BeginEnumeration function</span></span>
<span data-ttu-id="34768-104">Redefine um enumerador para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="34768-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="34768-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34768-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="34768-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34768-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="34768-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="34768-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="34768-108">`ptr` [in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="34768-108">`ptr` [in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="34768-109">[in] Uma combinação bit a bit de sinalizadores ou valores descritos no [comentários](#remarks) seção que controla as propriedades incluídas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="34768-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="34768-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="34768-110">Return value</span></span>

<span data-ttu-id="34768-111">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="34768-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="34768-112">Constante</span><span class="sxs-lookup"><span data-stu-id="34768-112">Constant</span></span>  |<span data-ttu-id="34768-113">Valor</span><span class="sxs-lookup"><span data-stu-id="34768-113">Value</span></span>  |<span data-ttu-id="34768-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="34768-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="34768-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="34768-115">0x80041008</span></span> | <span data-ttu-id="34768-116">A combinação de sinalizadores no `lEnumFlags` é inválido ou inválido argumento foi especificado.</span><span class="sxs-lookup"><span data-stu-id="34768-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="34768-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="34768-117">0x8004101d</span></span> | <span data-ttu-id="34768-118">Uma segunda chamada para `BeginEnumeration` foi feita sem uma chamada intermediária para [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="34768-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="34768-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="34768-119">0x80041006</span></span> | <span data-ttu-id="34768-120">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="34768-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="34768-121">0</span><span class="sxs-lookup"><span data-stu-id="34768-121">0</span></span> | <span data-ttu-id="34768-122">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="34768-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="34768-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="34768-123">Remarks</span></span>

<span data-ttu-id="34768-124">Essa função encapsula uma chamada para o [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) método.</span><span class="sxs-lookup"><span data-stu-id="34768-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="34768-125">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="34768-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="34768-126">Você pode combinar um sinalizador de cada grupo com qualquer sinalizador de nenhum outro grupo.</span><span class="sxs-lookup"><span data-stu-id="34768-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="34768-127">No entanto, os sinalizadores do mesmo grupo são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="34768-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="34768-128">**Grupo 1**</span><span class="sxs-lookup"><span data-stu-id="34768-128">**Group 1**</span></span>

|<span data-ttu-id="34768-129">Constante</span><span class="sxs-lookup"><span data-stu-id="34768-129">Constant</span></span>  |<span data-ttu-id="34768-130">Valor</span><span class="sxs-lookup"><span data-stu-id="34768-130">Value</span></span>  |<span data-ttu-id="34768-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="34768-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="34768-132">0x4</span><span class="sxs-lookup"><span data-stu-id="34768-132">0x4</span></span> | <span data-ttu-id="34768-133">Incluem propriedades que constituem a chave somente.</span><span class="sxs-lookup"><span data-stu-id="34768-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="34768-134">0x8</span><span class="sxs-lookup"><span data-stu-id="34768-134">0x8</span></span> | <span data-ttu-id="34768-135">Incluem propriedades que são somente referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="34768-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="34768-136">**Grupo 2**</span><span class="sxs-lookup"><span data-stu-id="34768-136">**Group 2**</span></span>

<span data-ttu-id="34768-137">Constante</span><span class="sxs-lookup"><span data-stu-id="34768-137">Constant</span></span>  |<span data-ttu-id="34768-138">Valor</span><span class="sxs-lookup"><span data-stu-id="34768-138">Value</span></span>  |<span data-ttu-id="34768-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="34768-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="34768-140">0x30</span><span class="sxs-lookup"><span data-stu-id="34768-140">0x30</span></span> | <span data-ttu-id="34768-141">Limite a enumeração para apenas as propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="34768-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="34768-142">0x40</span><span class="sxs-lookup"><span data-stu-id="34768-142">0x40</span></span> | <span data-ttu-id="34768-143">Incluir propriedades de locais e propagadas mas excluir propriedades de sistema a partir da enumeração.</span><span class="sxs-lookup"><span data-stu-id="34768-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="34768-144">Para classes:</span><span class="sxs-lookup"><span data-stu-id="34768-144">For classes:</span></span>

<span data-ttu-id="34768-145">Constante</span><span class="sxs-lookup"><span data-stu-id="34768-145">Constant</span></span>  |<span data-ttu-id="34768-146">Valor</span><span class="sxs-lookup"><span data-stu-id="34768-146">Value</span></span>  |<span data-ttu-id="34768-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="34768-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="34768-148">0x100</span><span class="sxs-lookup"><span data-stu-id="34768-148">0x100</span></span> | <span data-ttu-id="34768-149">Limite a enumeração de propriedades substituídas na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="34768-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="34768-150">0x100</span><span class="sxs-lookup"><span data-stu-id="34768-150">0x100</span></span> | <span data-ttu-id="34768-151">Limite a enumeração de propriedades substituídas na definição de classe atual e novas propriedades definidas na classe.</span><span class="sxs-lookup"><span data-stu-id="34768-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="34768-152">0x300</span><span class="sxs-lookup"><span data-stu-id="34768-152">0x300</span></span> | <span data-ttu-id="34768-153">A máscara (em vez de um sinalizador) para aplicar em relação a um `lEnumFlags` valor para verificar se `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` está definido.</span><span class="sxs-lookup"><span data-stu-id="34768-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="34768-154">0x10</span><span class="sxs-lookup"><span data-stu-id="34768-154">0x10</span></span> | <span data-ttu-id="34768-155">Limite a enumeração de propriedades que são definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="34768-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="34768-156">0x20</span><span class="sxs-lookup"><span data-stu-id="34768-156">0x20</span></span> | <span data-ttu-id="34768-157">Limite a enumeração de propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="34768-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="34768-158">Para instâncias:</span><span class="sxs-lookup"><span data-stu-id="34768-158">For instances:</span></span>

<span data-ttu-id="34768-159">Constante</span><span class="sxs-lookup"><span data-stu-id="34768-159">Constant</span></span>  |<span data-ttu-id="34768-160">Valor</span><span class="sxs-lookup"><span data-stu-id="34768-160">Value</span></span>  |<span data-ttu-id="34768-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="34768-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="34768-162">0x10</span><span class="sxs-lookup"><span data-stu-id="34768-162">0x10</span></span> | <span data-ttu-id="34768-163">Limite a enumeração de propriedades que são definidas ou modificadas na própria classe.</span><span class="sxs-lookup"><span data-stu-id="34768-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="34768-164">0x20</span><span class="sxs-lookup"><span data-stu-id="34768-164">0x20</span></span> | <span data-ttu-id="34768-165">Limite a enumeração de propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="34768-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |


## <a name="requirements"></a><span data-ttu-id="34768-166">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34768-166">Requirements</span></span>  
 <span data-ttu-id="34768-167">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34768-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34768-168">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="34768-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="34768-169">**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="34768-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34768-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34768-170">See also</span></span>  
[<span data-ttu-id="34768-171">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="34768-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
