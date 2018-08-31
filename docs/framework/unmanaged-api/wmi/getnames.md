---
title: Função GetNames (referência de API não gerenciada)
description: A função GetNames recupera os nomes das propriedades de um objeto.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f53174bf060938d5a55cbd196944ac11916d59cd
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258105"
---
# <a name="getnames-function"></a><span data-ttu-id="b8f56-103">Função GetNames</span><span class="sxs-lookup"><span data-stu-id="b8f56-103">GetNames function</span></span>
<span data-ttu-id="b8f56-104">Recupera um subconjunto ou todos os nomes das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="b8f56-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b8f56-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8f56-105">Syntax</span></span>  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="b8f56-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8f56-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b8f56-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="b8f56-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b8f56-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="b8f56-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="b8f56-109">[in] Um ponteiro para um válido `LPCWSTR` que especifica um nome do qualificador que opera como parte de um filtro.</span><span class="sxs-lookup"><span data-stu-id="b8f56-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="b8f56-110">Para obter mais informações, consulte o [comentários](#remarks) seção.</span><span class="sxs-lookup"><span data-stu-id="b8f56-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="b8f56-111">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="b8f56-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="b8f56-112">[in] Uma combinação de campos de bits.</span><span class="sxs-lookup"><span data-stu-id="b8f56-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="b8f56-113">Para obter mais informações, consulte o [comentários](#remarks) seção.</span><span class="sxs-lookup"><span data-stu-id="b8f56-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="b8f56-114">[in] Um ponteiro para um válido `VARIANT` estrutura inicializada com um valor de filtro.</span><span class="sxs-lookup"><span data-stu-id="b8f56-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="b8f56-115">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="b8f56-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="b8f56-116">[out] Um `SAFEARRAY` estrutura que contém os nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b8f56-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="b8f56-117">Na entrada, esse parâmetro sempre deve ser um ponteiro para `null`.</span><span class="sxs-lookup"><span data-stu-id="b8f56-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="b8f56-118">Consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b8f56-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b8f56-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b8f56-119">Return value</span></span>

<span data-ttu-id="b8f56-120">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="b8f56-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b8f56-121">Constante</span><span class="sxs-lookup"><span data-stu-id="b8f56-121">Constant</span></span>  |<span data-ttu-id="b8f56-122">Valor</span><span class="sxs-lookup"><span data-stu-id="b8f56-122">Value</span></span>  |<span data-ttu-id="b8f56-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8f56-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="b8f56-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b8f56-124">0x80041001</span></span> | <span data-ttu-id="b8f56-125">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="b8f56-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b8f56-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b8f56-126">0x80041008</span></span> | <span data-ttu-id="b8f56-127">Um ou mais parâmetros não são válidos, ou uma combinação incorreta de parâmetros e sinalizadores foi especificada.</span><span class="sxs-lookup"><span data-stu-id="b8f56-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b8f56-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b8f56-128">0x80041006</span></span> | <span data-ttu-id="b8f56-129">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="b8f56-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b8f56-130">0</span><span class="sxs-lookup"><span data-stu-id="b8f56-130">0</span></span> | <span data-ttu-id="b8f56-131">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b8f56-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b8f56-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8f56-132">Remarks</span></span>

<span data-ttu-id="b8f56-133">Essa função encapsula uma chamada para o [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) método.</span><span class="sxs-lookup"><span data-stu-id="b8f56-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="b8f56-134">Nomeado retornados é controlado por uma combinação de sinalizadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b8f56-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="b8f56-135">Por exemplo, a função pode retornar os nomes de todas as propriedades ou apenas os nomes das propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="b8f56-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="b8f56-136">O filtro primário é especificado no `lFlags` variam de parâmetro e os outros parâmetros depender dele.</span><span class="sxs-lookup"><span data-stu-id="b8f56-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="b8f56-137">O sinalizador de valores em `lFlags` são campos de bits</span><span class="sxs-lookup"><span data-stu-id="b8f56-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="b8f56-138">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são campos de bits que são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="b8f56-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="b8f56-139">Você pode combinar um sinalizador de cada grupo com qualquer sinalizador de nenhum outro grupo.</span><span class="sxs-lookup"><span data-stu-id="b8f56-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="b8f56-140">No entanto, os sinalizadores do mesmo grupo são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="b8f56-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="b8f56-141">Sinalizadores de grupo 1</span><span class="sxs-lookup"><span data-stu-id="b8f56-141">Group 1 flags</span></span> |<span data-ttu-id="b8f56-142">Valor</span><span class="sxs-lookup"><span data-stu-id="b8f56-142">Value</span></span>  |<span data-ttu-id="b8f56-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8f56-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="b8f56-144">0</span><span class="sxs-lookup"><span data-stu-id="b8f56-144">0</span></span> | <span data-ttu-id="b8f56-145">Retorne todos os nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b8f56-145">Return all property names.</span></span> <span data-ttu-id="b8f56-146">`strQualifierName` e `pQualifierVal` são utilizados.</span><span class="sxs-lookup"><span data-stu-id="b8f56-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="b8f56-147">1</span><span class="sxs-lookup"><span data-stu-id="b8f56-147">1</span></span> | <span data-ttu-id="b8f56-148">Retornar somente as propriedades que têm um qualificador do nome especificado pelo `strQualifierName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b8f56-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="b8f56-149">Se esse sinalizador é usado, você deve especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="b8f56-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="b8f56-150">2</span><span class="sxs-lookup"><span data-stu-id="b8f56-150">2</span></span> |  <span data-ttu-id="b8f56-151">Retornar somente as propriedades que não tem um qualificador do nome especificado pelo `strQualifierName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b8f56-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="b8f56-152">Se esse sinalizador é usado, você deve especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="b8f56-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="b8f56-153">3</span><span class="sxs-lookup"><span data-stu-id="b8f56-153">3</span></span> | <span data-ttu-id="b8f56-154">Retorne apenas as propriedades que têm um qualificador do nome especificado pelo `wszQualifierName` parâmetro e também ter um valor idêntico àquele especificado pelo `pQualifierVal` estrutura.</span><span class="sxs-lookup"><span data-stu-id="b8f56-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="b8f56-155">Se este sinalizador é usado, você deve especificar uma `wszQualifierName` e um `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="b8f56-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="b8f56-156">Sinalizadores de grupo 2</span><span class="sxs-lookup"><span data-stu-id="b8f56-156">Group 2 flags</span></span> |<span data-ttu-id="b8f56-157">Valor</span><span class="sxs-lookup"><span data-stu-id="b8f56-157">Value</span></span>  |<span data-ttu-id="b8f56-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8f56-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="b8f56-159">0x4</span><span class="sxs-lookup"><span data-stu-id="b8f56-159">0x4</span></span> | <span data-ttu-id="b8f56-160">Retorne apenas os nomes de propriedades que definem as chaves.</span><span class="sxs-lookup"><span data-stu-id="b8f56-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="b8f56-161">0x8</span><span class="sxs-lookup"><span data-stu-id="b8f56-161">0x8</span></span> | <span data-ttu-id="b8f56-162">Retorno apenas nomes de propriedade que são referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="b8f56-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="b8f56-163">Grupo 3 sinalizadores</span><span class="sxs-lookup"><span data-stu-id="b8f56-163">Group 3 flags</span></span> |<span data-ttu-id="b8f56-164">Valor</span><span class="sxs-lookup"><span data-stu-id="b8f56-164">Value</span></span>  |<span data-ttu-id="b8f56-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8f56-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="b8f56-166">0x10</span><span class="sxs-lookup"><span data-stu-id="b8f56-166">0x10</span></span> | <span data-ttu-id="b8f56-167">Retorne apenas os nomes de propriedade que pertencem à classe mais derivada.</span><span class="sxs-lookup"><span data-stu-id="b8f56-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="b8f56-168">Exclua propriedades das classes pai.</span><span class="sxs-lookup"><span data-stu-id="b8f56-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="b8f56-169">0x20</span><span class="sxs-lookup"><span data-stu-id="b8f56-169">0x20</span></span> | <span data-ttu-id="b8f56-170">Retorne apenas os nomes de propriedades que pertencem às classes pai.</span><span class="sxs-lookup"><span data-stu-id="b8f56-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="b8f56-171">0x30</span><span class="sxs-lookup"><span data-stu-id="b8f56-171">0x30</span></span> | <span data-ttu-id="b8f56-172">Retorne apenas os nomes de propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="b8f56-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="b8f56-173">0x40</span><span class="sxs-lookup"><span data-stu-id="b8f56-173">0x40</span></span> | <span data-ttu-id="b8f56-174">Retorne apenas os nomes das propriedades não são do sistema.</span><span class="sxs-lookup"><span data-stu-id="b8f56-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="b8f56-175">A função sempre aloca um novo `SAFEARRAY` se ele retornar `WBEM_S_NO_ERROR`, e `pstrNames` é sempre definido para apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="b8f56-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="b8f56-176">A matriz retornada pode ter elementos 0 se nenhuma propriedade corresponde aos filtros especificados.</span><span class="sxs-lookup"><span data-stu-id="b8f56-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="b8f56-177">Se a função retorna um valor diferente de `WBM_S_NO_ERROR`, um novo `SAFEARRAY` estrutura não é retornada.</span><span class="sxs-lookup"><span data-stu-id="b8f56-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="b8f56-178">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8f56-178">Requirements</span></span>  
 <span data-ttu-id="b8f56-179">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8f56-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8f56-180">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b8f56-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b8f56-181">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8f56-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f56-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8f56-182">See also</span></span>  
[<span data-ttu-id="b8f56-183">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b8f56-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
