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
ms.openlocfilehash: 5b03ed6a68fbe288e93dedb4f425f1511563dfeb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102517"
---
# <a name="getnames-function"></a><span data-ttu-id="3fc17-103">Função GetNames</span><span class="sxs-lookup"><span data-stu-id="3fc17-103">GetNames function</span></span>
<span data-ttu-id="3fc17-104">Recupera um subconjunto ou todos os nomes das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc17-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="3fc17-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fc17-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="3fc17-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fc17-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3fc17-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="3fc17-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3fc17-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="3fc17-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="3fc17-109">no Um ponteiro para um `LPCWSTR` válido que especifica um nome de qualificador que opera como parte de um filtro.</span><span class="sxs-lookup"><span data-stu-id="3fc17-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="3fc17-110">Para obter mais informações, consulte a seção [comentários](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="3fc17-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="3fc17-111">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="3fc17-112">no Uma combinação de campos de bits.</span><span class="sxs-lookup"><span data-stu-id="3fc17-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="3fc17-113">Para obter mais informações, consulte a seção [comentários](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="3fc17-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="3fc17-114">no Um ponteiro para uma estrutura de `VARIANT` válida inicializada para um valor de filtro.</span><span class="sxs-lookup"><span data-stu-id="3fc17-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="3fc17-115">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="3fc17-116">fora Uma estrutura de `SAFEARRAY` que contém nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3fc17-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="3fc17-117">Na entrada, esse parâmetro deve ser sempre um ponteiro para `null`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="3fc17-118">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3fc17-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="3fc17-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3fc17-119">Return value</span></span>

<span data-ttu-id="3fc17-120">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="3fc17-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3fc17-121">Constante</span><span class="sxs-lookup"><span data-stu-id="3fc17-121">Constant</span></span>  |<span data-ttu-id="3fc17-122">Valor</span><span class="sxs-lookup"><span data-stu-id="3fc17-122">Value</span></span>  |<span data-ttu-id="3fc17-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fc17-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3fc17-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3fc17-124">0x80041001</span></span> | <span data-ttu-id="3fc17-125">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="3fc17-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3fc17-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3fc17-126">0x80041008</span></span> | <span data-ttu-id="3fc17-127">Um ou mais parâmetros não são válidos ou uma combinação incorreta de sinalizadores e parâmetros foi especificada.</span><span class="sxs-lookup"><span data-stu-id="3fc17-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3fc17-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3fc17-128">0x80041006</span></span> | <span data-ttu-id="3fc17-129">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="3fc17-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3fc17-130">0</span><span class="sxs-lookup"><span data-stu-id="3fc17-130">0</span></span> | <span data-ttu-id="3fc17-131">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3fc17-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3fc17-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fc17-132">Remarks</span></span>

<span data-ttu-id="3fc17-133">Essa função encapsula uma chamada para o método [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .</span><span class="sxs-lookup"><span data-stu-id="3fc17-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="3fc17-134">O nome retornado é controlado por uma combinação de sinalizadores e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3fc17-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="3fc17-135">Por exemplo, a função pode retornar os nomes de todas as propriedades ou apenas os nomes das propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="3fc17-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="3fc17-136">O filtro primário é especificado no parâmetro `lFlags` e os outros parâmetros variam dependendo dele.</span><span class="sxs-lookup"><span data-stu-id="3fc17-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="3fc17-137">Os valores de sinalizador em `lFlags` são campos de bits</span><span class="sxs-lookup"><span data-stu-id="3fc17-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="3fc17-138">Os sinalizadores que podem ser passados como o argumento de `lEnumFlags` são campos de bits definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="3fc17-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="3fc17-139">Você pode combinar um sinalizador de cada grupo com qualquer sinalizador de qualquer outro grupo.</span><span class="sxs-lookup"><span data-stu-id="3fc17-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="3fc17-140">No entanto, os sinalizadores do mesmo grupo são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="3fc17-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="3fc17-141">Sinalizadores do grupo 1</span><span class="sxs-lookup"><span data-stu-id="3fc17-141">Group 1 flags</span></span> |<span data-ttu-id="3fc17-142">Valor</span><span class="sxs-lookup"><span data-stu-id="3fc17-142">Value</span></span>  |<span data-ttu-id="3fc17-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fc17-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="3fc17-144">0</span><span class="sxs-lookup"><span data-stu-id="3fc17-144">0</span></span> | <span data-ttu-id="3fc17-145">Retornar todos os nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3fc17-145">Return all property names.</span></span> <span data-ttu-id="3fc17-146">`strQualifierName` e `pQualifierVal` não são usados.</span><span class="sxs-lookup"><span data-stu-id="3fc17-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="3fc17-147">1</span><span class="sxs-lookup"><span data-stu-id="3fc17-147">1</span></span> | <span data-ttu-id="3fc17-148">Retornar apenas as propriedades que têm um qualificador do nome especificado pelo parâmetro `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="3fc17-149">Se esse sinalizador for usado, você deverá especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="3fc17-150">2</span><span class="sxs-lookup"><span data-stu-id="3fc17-150">2</span></span> |  <span data-ttu-id="3fc17-151">Retornar apenas propriedades que não têm um qualificador do nome especificado pelo parâmetro `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="3fc17-152">Se esse sinalizador for usado, você deverá especificar `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="3fc17-153">3</span><span class="sxs-lookup"><span data-stu-id="3fc17-153">3</span></span> | <span data-ttu-id="3fc17-154">Retorne apenas as propriedades que têm um qualificador do nome especificado pelo parâmetro `wszQualifierName` e também têm um valor idêntico ao especificado pela estrutura de `pQualifierVal`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="3fc17-155">Se esse sinalizador for usado, você deverá especificar um `wszQualifierName` e um `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="3fc17-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="3fc17-156">Sinalizadores do grupo 2</span><span class="sxs-lookup"><span data-stu-id="3fc17-156">Group 2 flags</span></span> |<span data-ttu-id="3fc17-157">Valor</span><span class="sxs-lookup"><span data-stu-id="3fc17-157">Value</span></span>  |<span data-ttu-id="3fc17-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fc17-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="3fc17-159">0x4</span><span class="sxs-lookup"><span data-stu-id="3fc17-159">0x4</span></span> | <span data-ttu-id="3fc17-160">Retornar somente os nomes das propriedades que definem as chaves.</span><span class="sxs-lookup"><span data-stu-id="3fc17-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="3fc17-161">0x8</span><span class="sxs-lookup"><span data-stu-id="3fc17-161">0x8</span></span> | <span data-ttu-id="3fc17-162">Retornar apenas nomes de propriedade que são referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc17-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="3fc17-163">Sinalizadores do grupo 3</span><span class="sxs-lookup"><span data-stu-id="3fc17-163">Group 3 flags</span></span> |<span data-ttu-id="3fc17-164">Valor</span><span class="sxs-lookup"><span data-stu-id="3fc17-164">Value</span></span>  |<span data-ttu-id="3fc17-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fc17-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="3fc17-166">0x10</span><span class="sxs-lookup"><span data-stu-id="3fc17-166">0x10</span></span> | <span data-ttu-id="3fc17-167">Retornar apenas os nomes de propriedade que pertencem à classe mais derivada.</span><span class="sxs-lookup"><span data-stu-id="3fc17-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="3fc17-168">Exclua as propriedades das classes pai.</span><span class="sxs-lookup"><span data-stu-id="3fc17-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="3fc17-169">0x20</span><span class="sxs-lookup"><span data-stu-id="3fc17-169">0x20</span></span> | <span data-ttu-id="3fc17-170">Retornar apenas os nomes de propriedade que pertencem às classes pai.</span><span class="sxs-lookup"><span data-stu-id="3fc17-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="3fc17-171">0x30</span><span class="sxs-lookup"><span data-stu-id="3fc17-171">0x30</span></span> | <span data-ttu-id="3fc17-172">Retornar apenas os nomes das propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="3fc17-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="3fc17-173">0x40</span><span class="sxs-lookup"><span data-stu-id="3fc17-173">0x40</span></span> | <span data-ttu-id="3fc17-174">Retornar apenas os nomes das propriedades que não são do sistema.</span><span class="sxs-lookup"><span data-stu-id="3fc17-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="3fc17-175">A função sempre aloca um novo `SAFEARRAY` se ele retorna `WBEM_S_NO_ERROR`e `pstrNames` é sempre definido para apontar para ele.</span><span class="sxs-lookup"><span data-stu-id="3fc17-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="3fc17-176">A matriz retornada pode ter 0 elementos se nenhuma propriedade corresponder aos filtros especificados.</span><span class="sxs-lookup"><span data-stu-id="3fc17-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="3fc17-177">Se a função retornar um valor diferente de `WBM_S_NO_ERROR`, uma nova estrutura de `SAFEARRAY` não será retornada.</span><span class="sxs-lookup"><span data-stu-id="3fc17-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="3fc17-178">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fc17-178">Requirements</span></span>  
 <span data-ttu-id="3fc17-179">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fc17-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc17-180">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="3fc17-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3fc17-181">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc17-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc17-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fc17-182">See also</span></span>

- [<span data-ttu-id="3fc17-183">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="3fc17-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
