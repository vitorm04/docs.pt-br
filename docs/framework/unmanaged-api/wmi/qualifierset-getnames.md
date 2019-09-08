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
ms.openlocfilehash: 266462a5393c8e26aa2bc3f2ec8ab72d4410a431
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798299"
---
# <a name="qualifierset_getnames-function"></a><span data-ttu-id="c5bc5-103">Função QualifierSet_GetNames</span><span class="sxs-lookup"><span data-stu-id="c5bc5-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="c5bc5-104">Recupera os nomes de todos os qualificadores ou de determinados qualificadores que estão disponíveis a partir do objeto ou da propriedade atual.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c5bc5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5bc5-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="c5bc5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5bc5-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="c5bc5-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="c5bc5-108">no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="c5bc5-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="c5bc5-109">no Um dos seguintes sinalizadores ou valores que especifica quais nomes incluir na enumeração.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="c5bc5-110">Constante</span><span class="sxs-lookup"><span data-stu-id="c5bc5-110">Constant</span></span>  |<span data-ttu-id="c5bc5-111">Valor</span><span class="sxs-lookup"><span data-stu-id="c5bc5-111">Value</span></span>  |<span data-ttu-id="c5bc5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5bc5-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="c5bc5-113">0</span><span class="sxs-lookup"><span data-stu-id="c5bc5-113">0</span></span> | <span data-ttu-id="c5bc5-114">Retornar os nomes de todos os qualificadores.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c5bc5-115">0x10</span><span class="sxs-lookup"><span data-stu-id="c5bc5-115">0x10</span></span> | <span data-ttu-id="c5bc5-116">Retornar somente os nomes de qualificadores específicos para a propriedade ou objeto atual.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="c5bc5-117">Para uma propriedade: Retornar somente os qualificadores específicos para a propriedade (incluindo substituições) e não os qualificadores propagados da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="c5bc5-118">Para uma instância: Retornar apenas nomes de qualificador específicos da instância.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="c5bc5-119">Para uma classe: Retornar somente qualificadores específicos à classe que está sendo derivada.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="c5bc5-120">0x20</span><span class="sxs-lookup"><span data-stu-id="c5bc5-120">0x20</span></span> | <span data-ttu-id="c5bc5-121">Retornar apenas os nomes dos qualificadores propagados de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="c5bc5-122">Para uma propriedade: Retornar somente os qualificadores propagados para essa propriedade da definição de classe, e não os da própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="c5bc5-123">Para uma instância: Retornar somente os qualificadores propagados da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="c5bc5-124">Para uma classe: Retornar somente os nomes de qualificador herdados das classes pai.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="c5bc5-125">fora Um novo `SAFEARRAY` que contém os nomes solicitados.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="c5bc5-126">A matriz pode ter 0 elementos.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-126">The array can have 0 elements.</span></span> <span data-ttu-id="c5bc5-127">Se ocorrer um erro, um novo `SAFEARRAY` não será retornado.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="c5bc5-128">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c5bc5-128">Return value</span></span>

<span data-ttu-id="c5bc5-129">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c5bc5-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c5bc5-130">Constante</span><span class="sxs-lookup"><span data-stu-id="c5bc5-130">Constant</span></span>  |<span data-ttu-id="c5bc5-131">Valor</span><span class="sxs-lookup"><span data-stu-id="c5bc5-131">Value</span></span>  |<span data-ttu-id="c5bc5-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5bc5-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c5bc5-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c5bc5-133">0x80041008</span></span> | <span data-ttu-id="c5bc5-134">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c5bc5-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c5bc5-135">0x80041006</span></span> | <span data-ttu-id="c5bc5-136">Não há memória suficiente disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c5bc5-137">0</span><span class="sxs-lookup"><span data-stu-id="c5bc5-137">0</span></span> | <span data-ttu-id="c5bc5-138">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c5bc5-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5bc5-139">Remarks</span></span>

<span data-ttu-id="c5bc5-140">Essa função encapsula uma chamada para o método [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .</span><span class="sxs-lookup"><span data-stu-id="c5bc5-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="c5bc5-141">Depois de recuperar os nomes de qualificador, você pode acessar cada qualificador por nome chamando a função [QualifierSet_Get](qualifierset-get.md) .</span><span class="sxs-lookup"><span data-stu-id="c5bc5-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="c5bc5-142">Não é um erro para um determinado objeto ter zero qualificadores, portanto, o número de cadeias de `pstrNames` caracteres no retorno pode ser 0, mesmo que a função `WBEM_S_NO_ERROR`retorne.</span><span class="sxs-lookup"><span data-stu-id="c5bc5-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5bc5-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5bc5-143">Requirements</span></span>

<span data-ttu-id="c5bc5-144">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5bc5-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c5bc5-145">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c5bc5-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="c5bc5-146">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c5bc5-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c5bc5-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5bc5-147">See also</span></span>

- [<span data-ttu-id="c5bc5-148">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c5bc5-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
