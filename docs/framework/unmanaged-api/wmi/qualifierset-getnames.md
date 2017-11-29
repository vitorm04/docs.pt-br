---
title: "Função QualifierSet_GetNames (referência de API não gerenciada)"
description: "A função QualifierSet_GetNames recupera os nomes de qualificadores de um objeto ou propriedade."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_GetNames
helpviewer_keywords: QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b87518bdc1f6ac19eb48991538be5904fdb63f1f
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="02a0d-103">Função QualifierSet_GetNames</span><span class="sxs-lookup"><span data-stu-id="02a0d-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="02a0d-104">Recupera os nomes de todos os qualificadores ou de certos qualificadores disponíveis do objeto atual ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="02a0d-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="02a0d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02a0d-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="02a0d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02a0d-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="02a0d-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="02a0d-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="02a0d-108">[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="02a0d-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="02a0d-109">[in] Um dos seguintes sinalizadores ou valores que especifica os nomes a serem incluídos na enumeração.</span><span class="sxs-lookup"><span data-stu-id="02a0d-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="02a0d-110">Constante</span><span class="sxs-lookup"><span data-stu-id="02a0d-110">Constant</span></span>  |<span data-ttu-id="02a0d-111">Valor</span><span class="sxs-lookup"><span data-stu-id="02a0d-111">Value</span></span>  |<span data-ttu-id="02a0d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="02a0d-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="02a0d-113">0</span><span class="sxs-lookup"><span data-stu-id="02a0d-113">0</span></span> | <span data-ttu-id="02a0d-114">Retorne os nomes de todos os qualificadores.</span><span class="sxs-lookup"><span data-stu-id="02a0d-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="02a0d-115">0x10</span><span class="sxs-lookup"><span data-stu-id="02a0d-115">0x10</span></span> | <span data-ttu-id="02a0d-116">Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto.</span><span class="sxs-lookup"><span data-stu-id="02a0d-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="02a0d-117">Para uma propriedade: retornar apenas os qualificadores específica para a propriedade (incluindo substituições), e não os qualificadores propagadas da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="02a0d-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="02a0d-118">Para uma instância: retornar apenas os nomes de qualificador específicos da instância.</span><span class="sxs-lookup"><span data-stu-id="02a0d-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="02a0d-119">Para uma classe: retornar somente qualificadores específico para o beiong de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="02a0d-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="02a0d-120">0x20</span><span class="sxs-lookup"><span data-stu-id="02a0d-120">0x20</span></span> | <span data-ttu-id="02a0d-121">Retornar apenas os nomes dos qualificadores propagados de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="02a0d-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="02a0d-122">Para uma propriedade: retorno apenas os qualificadores propagados para essa propriedade de definição de classe e não os da própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="02a0d-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="02a0d-123">Para uma instância: retornar apenas os qualificadores propagados da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="02a0d-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="02a0d-124">Para uma classe: retornar apenas os nomes de qualificador herdados de classes pai.</span><span class="sxs-lookup"><span data-stu-id="02a0d-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="02a0d-125">`pstrNames`[out] Um novo `SAFEARRAY` que contém os nomes solicitados.</span><span class="sxs-lookup"><span data-stu-id="02a0d-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="02a0d-126">A matriz pode ter elementos 0.</span><span class="sxs-lookup"><span data-stu-id="02a0d-126">The array can have 0 elements.</span></span> <span data-ttu-id="02a0d-127">Se ocorrer um erro, um novo `SAFEARRAY` não é retornado.</span><span class="sxs-lookup"><span data-stu-id="02a0d-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="02a0d-128">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="02a0d-128">Return value</span></span>

<span data-ttu-id="02a0d-129">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="02a0d-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="02a0d-130">Constante</span><span class="sxs-lookup"><span data-stu-id="02a0d-130">Constant</span></span>  |<span data-ttu-id="02a0d-131">Valor</span><span class="sxs-lookup"><span data-stu-id="02a0d-131">Value</span></span>  |<span data-ttu-id="02a0d-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="02a0d-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="02a0d-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="02a0d-133">0x80041008</span></span> | <span data-ttu-id="02a0d-134">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="02a0d-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="02a0d-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="02a0d-135">0x80041006</span></span> | <span data-ttu-id="02a0d-136">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="02a0d-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="02a0d-137">0</span><span class="sxs-lookup"><span data-stu-id="02a0d-137">0</span></span> | <span data-ttu-id="02a0d-138">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="02a0d-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="02a0d-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="02a0d-139">Remarks</span></span>

<span data-ttu-id="02a0d-140">Essa função encapsula uma chamada para o [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="02a0d-140">This function wraps a call to the [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="02a0d-141">Depois de recuperar os nomes de qualificador, você pode acessar cada qualificador por nome, chamando o [QualifierSet_Get](qualifierset-get.md) função.</span><span class="sxs-lookup"><span data-stu-id="02a0d-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="02a0d-142">Não é um erro para um determinado objeto ter qualificadores de zero, então o número de cadeias de caracteres em `pstrNames` no retorno pode ser 0, mesmo que a função retornará `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="02a0d-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="02a0d-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02a0d-143">Requirements</span></span>  
 <span data-ttu-id="02a0d-144">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02a0d-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02a0d-145">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="02a0d-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="02a0d-146">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="02a0d-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a0d-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02a0d-147">See also</span></span>  
[<span data-ttu-id="02a0d-148">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="02a0d-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
