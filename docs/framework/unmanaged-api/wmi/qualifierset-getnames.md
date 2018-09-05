---
title: Função QualifierSet_GetNames (referência de API não gerenciada)
description: A função QualifierSet_GetNames recupera os nomes de qualificadores de um objeto ou propriedade.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84059c5e5542e13b1d4fc4efcfc4c7f418db391e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672116"
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="c69b9-103">Função QualifierSet_GetNames</span><span class="sxs-lookup"><span data-stu-id="c69b9-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="c69b9-104">Recupera os nomes de todos os qualificadores ou de certas qualificadores que estão disponíveis no objeto atual ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="c69b9-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c69b9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c69b9-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="c69b9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c69b9-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="c69b9-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="c69b9-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="c69b9-108">[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.</span><span class="sxs-lookup"><span data-stu-id="c69b9-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="c69b9-109">[in] Um dos seguintes sinalizadores ou valores que especifica quais nomes a serem incluídos na enumeração.</span><span class="sxs-lookup"><span data-stu-id="c69b9-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="c69b9-110">Constante</span><span class="sxs-lookup"><span data-stu-id="c69b9-110">Constant</span></span>  |<span data-ttu-id="c69b9-111">Valor</span><span class="sxs-lookup"><span data-stu-id="c69b9-111">Value</span></span>  |<span data-ttu-id="c69b9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c69b9-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="c69b9-113">0</span><span class="sxs-lookup"><span data-stu-id="c69b9-113">0</span></span> | <span data-ttu-id="c69b9-114">Retorne os nomes de todos os qualificadores.</span><span class="sxs-lookup"><span data-stu-id="c69b9-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c69b9-115">0x10</span><span class="sxs-lookup"><span data-stu-id="c69b9-115">0x10</span></span> | <span data-ttu-id="c69b9-116">Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto.</span><span class="sxs-lookup"><span data-stu-id="c69b9-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="c69b9-117">Para uma propriedade: retornar apenas os qualificadores específica para a propriedade (incluindo substituições), e não os qualificadores propagadas da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="c69b9-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="c69b9-118">Para uma instância: retornar apenas os nomes de qualificador de específico da instância.</span><span class="sxs-lookup"><span data-stu-id="c69b9-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="c69b9-119">Para uma classe: retornar apenas os qualificadores específica para o beiong de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c69b9-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="c69b9-120">0x20</span><span class="sxs-lookup"><span data-stu-id="c69b9-120">0x20</span></span> | <span data-ttu-id="c69b9-121">Retornar apenas os nomes dos qualificadores propagados de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="c69b9-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="c69b9-122">Para uma propriedade: retorno propagados apenas os qualificadores a essa propriedade de definição de classe e não os valores da propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="c69b9-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="c69b9-123">Para uma instância: retorno apenas desses qualificadores propagados da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="c69b9-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="c69b9-124">Para uma classe: retornar apenas os nomes de qualificador herdados de classes pai.</span><span class="sxs-lookup"><span data-stu-id="c69b9-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="c69b9-125">`pstrNames` [out] Um novo `SAFEARRAY` que contém os nomes solicitados.</span><span class="sxs-lookup"><span data-stu-id="c69b9-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="c69b9-126">A matriz pode ter 0 elementos.</span><span class="sxs-lookup"><span data-stu-id="c69b9-126">The array can have 0 elements.</span></span> <span data-ttu-id="c69b9-127">Se ocorrer um erro, um novo `SAFEARRAY` não será retornado.</span><span class="sxs-lookup"><span data-stu-id="c69b9-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="c69b9-128">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c69b9-128">Return value</span></span>

<span data-ttu-id="c69b9-129">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c69b9-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c69b9-130">Constante</span><span class="sxs-lookup"><span data-stu-id="c69b9-130">Constant</span></span>  |<span data-ttu-id="c69b9-131">Valor</span><span class="sxs-lookup"><span data-stu-id="c69b9-131">Value</span></span>  |<span data-ttu-id="c69b9-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="c69b9-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c69b9-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c69b9-133">0x80041008</span></span> | <span data-ttu-id="c69b9-134">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="c69b9-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c69b9-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c69b9-135">0x80041006</span></span> | <span data-ttu-id="c69b9-136">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="c69b9-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c69b9-137">0</span><span class="sxs-lookup"><span data-stu-id="c69b9-137">0</span></span> | <span data-ttu-id="c69b9-138">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c69b9-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c69b9-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="c69b9-139">Remarks</span></span>

<span data-ttu-id="c69b9-140">Essa função encapsula uma chamada para o [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) método.</span><span class="sxs-lookup"><span data-stu-id="c69b9-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="c69b9-141">Depois de recuperar os nomes de qualificador, você pode acessar cada qualificador por nome, chamando o [QualifierSet_Get](qualifierset-get.md) função.</span><span class="sxs-lookup"><span data-stu-id="c69b9-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="c69b9-142">Não é um erro para um determinado objeto ter qualificadores de zero, portanto, o número de cadeias de caracteres em `pstrNames` após o retorno pode ser 0, mesmo que a função retorna `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="c69b9-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c69b9-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c69b9-143">Requirements</span></span>  
 <span data-ttu-id="c69b9-144">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c69b9-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c69b9-145">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c69b9-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c69b9-146">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c69b9-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69b9-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c69b9-147">See also</span></span>  
[<span data-ttu-id="c69b9-148">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c69b9-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
