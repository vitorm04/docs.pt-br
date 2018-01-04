---
title: "Função GetNames (referência de API não gerenciada)"
description: "A função GetNames recupera os nomes das propriedades de um objeto."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetNames
helpviewer_keywords: GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80284900c318a3776168b781ce2e0e5e4a68f96d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getnames-function"></a><span data-ttu-id="e5e64-103">Função GetNames</span><span class="sxs-lookup"><span data-stu-id="e5e64-103">GetNames function</span></span>
<span data-ttu-id="e5e64-104">Recupera um subconjunto ou todos os nomes das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="e5e64-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e5e64-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5e64-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="e5e64-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5e64-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e5e64-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="e5e64-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e5e64-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="e5e64-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="e5e64-109">[in] Um ponteiro para um válida `LPCWSTR` que especifica um nome de qualificador que funciona como parte de um filtro.</span><span class="sxs-lookup"><span data-stu-id="e5e64-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="e5e64-110">Para obter mais informações, consulte o [comentários](#remarks) seção.</span><span class="sxs-lookup"><span data-stu-id="e5e64-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="e5e64-111">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e5e64-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="e5e64-112">[in] Uma combinação de campos de bits.</span><span class="sxs-lookup"><span data-stu-id="e5e64-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="e5e64-113">Para obter mais informações, consulte o [comentários](#remarks) seção.</span><span class="sxs-lookup"><span data-stu-id="e5e64-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="e5e64-114">[in] Um ponteiro para um válida `VARIANT` estrutura inicializada com um valor de filtro.</span><span class="sxs-lookup"><span data-stu-id="e5e64-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="e5e64-115">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e5e64-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="e5e64-116">[out] Um `SAFEARRAY` estrutura que contém os nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5e64-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="e5e64-117">Na entrada, esse parâmetro sempre deve ser um ponteiro para `null`.</span><span class="sxs-lookup"><span data-stu-id="e5e64-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="e5e64-118">Consulte o [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e5e64-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e5e64-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e5e64-119">Return value</span></span>

<span data-ttu-id="e5e64-120">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="e5e64-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e5e64-121">Constante</span><span class="sxs-lookup"><span data-stu-id="e5e64-121">Constant</span></span>  |<span data-ttu-id="e5e64-122">Valor</span><span class="sxs-lookup"><span data-stu-id="e5e64-122">Value</span></span>  |<span data-ttu-id="e5e64-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5e64-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e5e64-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e5e64-124">0x80041001</span></span> | <span data-ttu-id="e5e64-125">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="e5e64-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e5e64-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e5e64-126">0x80041008</span></span> | <span data-ttu-id="e5e64-127">Um ou mais parâmetros não são válidos ou foi especificada uma combinação incorreta de sinalizadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e5e64-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e5e64-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e5e64-128">0x80041006</span></span> | <span data-ttu-id="e5e64-129">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="e5e64-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e5e64-130">0</span><span class="sxs-lookup"><span data-stu-id="e5e64-130">0</span></span> | <span data-ttu-id="e5e64-131">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e5e64-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e5e64-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5e64-132">Remarks</span></span>

<span data-ttu-id="e5e64-133">Essa função encapsula uma chamada para o [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="e5e64-133">This function wraps a call to the [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e5e64-134">Nomeado retornados é controlado por uma combinação de sinalizadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e5e64-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="e5e64-135">Por exemplo, a função pode retornar os nomes de todas as propriedades ou apenas os nomes das propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="e5e64-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="e5e64-136">O filtro primário for especificado no `lFlags` parâmetro e os outros parâmetros variam dependendo-lo.</span><span class="sxs-lookup"><span data-stu-id="e5e64-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="e5e64-137">O sinalizador de valores em `lFlags` são campos de bits</span><span class="sxs-lookup"><span data-stu-id="e5e64-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="e5e64-138">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são campos de bits são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="e5e64-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="e5e64-139">Você pode combinar um sinalizador de cada grupo com qualquer sinalizador de nenhum outro grupo.</span><span class="sxs-lookup"><span data-stu-id="e5e64-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="e5e64-140">No entanto, os sinalizadores do mesmo grupo são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="e5e64-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="e5e64-141">Sinalizadores de grupo 1</span><span class="sxs-lookup"><span data-stu-id="e5e64-141">Group 1 flags</span></span> |<span data-ttu-id="e5e64-142">Valor</span><span class="sxs-lookup"><span data-stu-id="e5e64-142">Value</span></span>  |<span data-ttu-id="e5e64-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5e64-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="e5e64-144">0</span><span class="sxs-lookup"><span data-stu-id="e5e64-144">0</span></span> | <span data-ttu-id="e5e64-145">Retorne todos os nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5e64-145">Return all property names.</span></span> <span data-ttu-id="e5e64-146">`strQualifierName`e `pQualifierVal` são utilizadas.</span><span class="sxs-lookup"><span data-stu-id="e5e64-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="e5e64-147">1</span><span class="sxs-lookup"><span data-stu-id="e5e64-147">1</span></span> | <span data-ttu-id="e5e64-148">Retornar somente as propriedades que têm um qualificador do nome especificado pelo `strQualifierName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e5e64-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e5e64-149">Se este sinalizador é usado, você deve especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="e5e64-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="e5e64-150">2</span><span class="sxs-lookup"><span data-stu-id="e5e64-150">2</span></span> |  <span data-ttu-id="e5e64-151">Retornar somente as propriedades que não têm um qualificador do nome especificado pelo `strQualifierName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e5e64-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e5e64-152">Se este sinalizador é usado, você deve especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="e5e64-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="e5e64-153">3</span><span class="sxs-lookup"><span data-stu-id="e5e64-153">3</span></span> | <span data-ttu-id="e5e64-154">Retornar apenas as propriedades que têm um qualificador do nome especificado pelo `wszQualifierName` parâmetro e também ter um valor idêntico ao especificado pelo `pQualifierVal` estrutura.</span><span class="sxs-lookup"><span data-stu-id="e5e64-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="e5e64-155">Se esse sinalizador for usado, você deve especificar ambos um `wszQualifierName` e um `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="e5e64-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="e5e64-156">Sinalizadores de grupo 2</span><span class="sxs-lookup"><span data-stu-id="e5e64-156">Group 2 flags</span></span> |<span data-ttu-id="e5e64-157">Valor</span><span class="sxs-lookup"><span data-stu-id="e5e64-157">Value</span></span>  |<span data-ttu-id="e5e64-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5e64-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="e5e64-159">0x4</span><span class="sxs-lookup"><span data-stu-id="e5e64-159">0x4</span></span> | <span data-ttu-id="e5e64-160">Retorne apenas os nomes de propriedades que definem as chaves.</span><span class="sxs-lookup"><span data-stu-id="e5e64-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="e5e64-161">0x8</span><span class="sxs-lookup"><span data-stu-id="e5e64-161">0x8</span></span> | <span data-ttu-id="e5e64-162">Retorno apenas nomes de propriedades que são referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="e5e64-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="e5e64-163">Grupo 3 sinalizadores</span><span class="sxs-lookup"><span data-stu-id="e5e64-163">Group 3 flags</span></span> |<span data-ttu-id="e5e64-164">Valor</span><span class="sxs-lookup"><span data-stu-id="e5e64-164">Value</span></span>  |<span data-ttu-id="e5e64-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5e64-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="e5e64-166">0x10</span><span class="sxs-lookup"><span data-stu-id="e5e64-166">0x10</span></span> | <span data-ttu-id="e5e64-167">Retorne apenas os nomes de propriedade que pertencem à classe mais derivada.</span><span class="sxs-lookup"><span data-stu-id="e5e64-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="e5e64-168">Exclua propriedades das classes pai.</span><span class="sxs-lookup"><span data-stu-id="e5e64-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="e5e64-169">0x20</span><span class="sxs-lookup"><span data-stu-id="e5e64-169">0x20</span></span> | <span data-ttu-id="e5e64-170">Retorne apenas os nomes de propriedade que pertencem às classes pai.</span><span class="sxs-lookup"><span data-stu-id="e5e64-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="e5e64-171">0x30</span><span class="sxs-lookup"><span data-stu-id="e5e64-171">0x30</span></span> | <span data-ttu-id="e5e64-172">Retorne apenas os nomes das propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5e64-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="e5e64-173">0x40</span><span class="sxs-lookup"><span data-stu-id="e5e64-173">0x40</span></span> | <span data-ttu-id="e5e64-174">Retorne apenas os nomes das propriedades não são do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5e64-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="e5e64-175">A função sempre aloca um novo `SAFEARRAY` se ele retorna `WBEM_S_NO_ERROR`, e `pstrNames` é sempre definido para apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="e5e64-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="e5e64-176">A matriz retornada pode ter elementos 0 se não há propriedades correspondem aos filtros especificados.</span><span class="sxs-lookup"><span data-stu-id="e5e64-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="e5e64-177">Se a função retorna um valor diferente de `WBM_S_NO_ERROR`, um novo `SAFEARRAY` estrutura não é retornada.</span><span class="sxs-lookup"><span data-stu-id="e5e64-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="e5e64-178">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5e64-178">Requirements</span></span>  
 <span data-ttu-id="e5e64-179">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5e64-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e64-180">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e5e64-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e5e64-181">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e64-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e64-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5e64-182">See also</span></span>  
[<span data-ttu-id="e5e64-183">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="e5e64-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
