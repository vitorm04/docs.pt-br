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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174947"
---
# <a name="getnames-function"></a><span data-ttu-id="0a659-103">Função GetNames</span><span class="sxs-lookup"><span data-stu-id="0a659-103">GetNames function</span></span>
<span data-ttu-id="0a659-104">Recupera um subconjunto ou todos os nomes das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="0a659-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0a659-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a659-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a><span data-ttu-id="0a659-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="0a659-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0a659-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="0a659-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0a659-108">[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="0a659-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="0a659-109">[em] Um ponteiro para `LPCWSTR` um válido que especifica um nome qualificador que funciona como parte de um filtro.</span><span class="sxs-lookup"><span data-stu-id="0a659-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="0a659-110">Para obter mais informações, consulte a seção [Observações.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="0a659-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="0a659-111">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="0a659-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="0a659-112">[em] Uma combinação de campos de bits.</span><span class="sxs-lookup"><span data-stu-id="0a659-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="0a659-113">Para obter mais informações, consulte a seção [Observações.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="0a659-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="0a659-114">`pQualifierValue`[em] Um ponteiro para `VARIANT` uma estrutura válida inicializada para um valor de filtro.</span><span class="sxs-lookup"><span data-stu-id="0a659-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="0a659-115">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="0a659-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="0a659-116">[fora] Uma `SAFEARRAY` estrutura que contém nomes de propriedades.</span><span class="sxs-lookup"><span data-stu-id="0a659-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="0a659-117">Na entrada, este parâmetro deve ser `null`sempre um ponteiro para .</span><span class="sxs-lookup"><span data-stu-id="0a659-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="0a659-118">Consulte a seção [Observações](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0a659-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a659-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0a659-119">Return value</span></span>

<span data-ttu-id="0a659-120">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="0a659-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0a659-121">Constante</span><span class="sxs-lookup"><span data-stu-id="0a659-121">Constant</span></span>  |<span data-ttu-id="0a659-122">Valor</span><span class="sxs-lookup"><span data-stu-id="0a659-122">Value</span></span>  |<span data-ttu-id="0a659-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a659-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="0a659-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0a659-124">0x80041001</span></span> | <span data-ttu-id="0a659-125">Houve um fracasso geral.</span><span class="sxs-lookup"><span data-stu-id="0a659-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0a659-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0a659-126">0x80041008</span></span> | <span data-ttu-id="0a659-127">Um ou mais parâmetros não são válidos ou uma combinação incorreta de sinalizadores e parâmetros foi especificada.</span><span class="sxs-lookup"><span data-stu-id="0a659-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0a659-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0a659-128">0x80041006</span></span> | <span data-ttu-id="0a659-129">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="0a659-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0a659-130">0</span><span class="sxs-lookup"><span data-stu-id="0a659-130">0</span></span> | <span data-ttu-id="0a659-131">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0a659-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0a659-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a659-132">Remarks</span></span>

<span data-ttu-id="0a659-133">Esta função envolve uma chamada para o método [IWbemClassObject::GetNames.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)</span><span class="sxs-lookup"><span data-stu-id="0a659-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="0a659-134">Os chamados retornados são controlados por uma combinação de bandeiras e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0a659-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="0a659-135">Por exemplo, a função pode retornar os nomes de todas as propriedades ou apenas os nomes das propriedades-chave.</span><span class="sxs-lookup"><span data-stu-id="0a659-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="0a659-136">O filtro primário é `lFlags` especificado no parâmetro, e os outros parâmetros variam dependendo dele.</span><span class="sxs-lookup"><span data-stu-id="0a659-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="0a659-137">Os valores `lFlags` da bandeira em são campos de bits</span><span class="sxs-lookup"><span data-stu-id="0a659-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="0a659-138">As bandeiras que podem `lEnumFlags` ser passadas como argumento são campos de bits definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-las como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="0a659-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="0a659-139">Você pode combinar uma bandeira de cada grupo com qualquer bandeira de qualquer outro grupo.</span><span class="sxs-lookup"><span data-stu-id="0a659-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="0a659-140">No entanto, bandeiras do mesmo grupo são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="0a659-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="0a659-141">Bandeiras do Grupo 1</span><span class="sxs-lookup"><span data-stu-id="0a659-141">Group 1 flags</span></span> |<span data-ttu-id="0a659-142">Valor</span><span class="sxs-lookup"><span data-stu-id="0a659-142">Value</span></span>  |<span data-ttu-id="0a659-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a659-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="0a659-144">0</span><span class="sxs-lookup"><span data-stu-id="0a659-144">0</span></span> | <span data-ttu-id="0a659-145">Devolva todos os nomes das propriedades.</span><span class="sxs-lookup"><span data-stu-id="0a659-145">Return all property names.</span></span> <span data-ttu-id="0a659-146">`strQualifierName`e `pQualifierVal` não são usados.</span><span class="sxs-lookup"><span data-stu-id="0a659-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="0a659-147">1</span><span class="sxs-lookup"><span data-stu-id="0a659-147">1</span></span> | <span data-ttu-id="0a659-148">Retornar somente propriedades que tenham um qualificador `strQualifierName` do nome especificado pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0a659-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="0a659-149">Se este sinalizador for usado, você deve especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="0a659-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="0a659-150">2</span><span class="sxs-lookup"><span data-stu-id="0a659-150">2</span></span> |  <span data-ttu-id="0a659-151">Retornar apenas propriedades que não possuem um qualificador `strQualifierName` do nome especificado pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0a659-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="0a659-152">Se este sinalizador for usado, você deve especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="0a659-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="0a659-153">3</span><span class="sxs-lookup"><span data-stu-id="0a659-153">3</span></span> | <span data-ttu-id="0a659-154">Retornar somente propriedades que tenham um qualificador `wszQualifierName` do nome especificado pelo parâmetro e `pQualifierVal` também tenham um valor idêntico ao especificado pela estrutura.</span><span class="sxs-lookup"><span data-stu-id="0a659-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="0a659-155">Se este sinalizador for usado, `wszQualifierName` você `pQualifierValue`deve especificar a e a .</span><span class="sxs-lookup"><span data-stu-id="0a659-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="0a659-156">Bandeiras do Grupo 2</span><span class="sxs-lookup"><span data-stu-id="0a659-156">Group 2 flags</span></span> |<span data-ttu-id="0a659-157">Valor</span><span class="sxs-lookup"><span data-stu-id="0a659-157">Value</span></span>  |<span data-ttu-id="0a659-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a659-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="0a659-159">0x4</span><span class="sxs-lookup"><span data-stu-id="0a659-159">0x4</span></span> | <span data-ttu-id="0a659-160">Devolva apenas os nomes das propriedades que definem as chaves.</span><span class="sxs-lookup"><span data-stu-id="0a659-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="0a659-161">0x8</span><span class="sxs-lookup"><span data-stu-id="0a659-161">0x8</span></span> | <span data-ttu-id="0a659-162">Devolva apenas nomes de propriedade que são referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="0a659-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="0a659-163">Bandeiras do Grupo 3</span><span class="sxs-lookup"><span data-stu-id="0a659-163">Group 3 flags</span></span> |<span data-ttu-id="0a659-164">Valor</span><span class="sxs-lookup"><span data-stu-id="0a659-164">Value</span></span>  |<span data-ttu-id="0a659-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a659-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="0a659-166">0x10</span><span class="sxs-lookup"><span data-stu-id="0a659-166">0x10</span></span> | <span data-ttu-id="0a659-167">Devolva apenas nomes de propriedades que pertencem à classe mais derivada.</span><span class="sxs-lookup"><span data-stu-id="0a659-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="0a659-168">Exclua propriedades das classes-mãe.</span><span class="sxs-lookup"><span data-stu-id="0a659-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="0a659-169">0x20</span><span class="sxs-lookup"><span data-stu-id="0a659-169">0x20</span></span> | <span data-ttu-id="0a659-170">Devolva apenas nomes de propriedades que pertencem às classes dos pais.</span><span class="sxs-lookup"><span data-stu-id="0a659-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="0a659-171">0x30</span><span class="sxs-lookup"><span data-stu-id="0a659-171">0x30</span></span> | <span data-ttu-id="0a659-172">Devolva apenas os nomes das propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="0a659-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="0a659-173">0x40</span><span class="sxs-lookup"><span data-stu-id="0a659-173">0x40</span></span> | <span data-ttu-id="0a659-174">Devolva apenas os nomes das propriedades não-sistema.</span><span class="sxs-lookup"><span data-stu-id="0a659-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="0a659-175">A função sempre aloca `SAFEARRAY` um `WBEM_S_NO_ERROR`novo `pstrNames` se retornar, e é sempre definida para apontar para ela.</span><span class="sxs-lookup"><span data-stu-id="0a659-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="0a659-176">A matriz retornada pode ter 0 elementos se nenhuma propriedade corresponder aos filtros especificados.</span><span class="sxs-lookup"><span data-stu-id="0a659-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="0a659-177">Se a função retornar `WBM_S_NO_ERROR`um valor `SAFEARRAY` diferente, uma nova estrutura não será devolvida.</span><span class="sxs-lookup"><span data-stu-id="0a659-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a659-178">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a659-178">Requirements</span></span>  
 <span data-ttu-id="0a659-179">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a659-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a659-180">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0a659-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0a659-181">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0a659-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a659-182">Confira também</span><span class="sxs-lookup"><span data-stu-id="0a659-182">See also</span></span>

- [<span data-ttu-id="0a659-183">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="0a659-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
