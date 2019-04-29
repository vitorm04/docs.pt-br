---
title: Função QualifierSet_BeginEnumeration (referência de API não gerenciada)
description: A função QualifierSet_BeginEnumeration redefine um enumerador os qualificadores de um objeto.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597228"
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="16bf8-103">Função QualifierSet_BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="16bf8-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="16bf8-104">Redefine um enumerador dos qualificadores de um objeto para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="16bf8-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="16bf8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16bf8-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="16bf8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16bf8-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="16bf8-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="16bf8-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="16bf8-108">[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.</span><span class="sxs-lookup"><span data-stu-id="16bf8-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="16bf8-109">[in] Uma combinação bit a bit de sinalizadores ou valores descritos na [comentários](#remarks) seção que especifica os qualificadores a serem incluídos na enumeração.</span><span class="sxs-lookup"><span data-stu-id="16bf8-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="16bf8-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="16bf8-110">Return value</span></span>

<span data-ttu-id="16bf8-111">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="16bf8-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="16bf8-112">Constante</span><span class="sxs-lookup"><span data-stu-id="16bf8-112">Constant</span></span>  |<span data-ttu-id="16bf8-113">Valor</span><span class="sxs-lookup"><span data-stu-id="16bf8-113">Value</span></span>  |<span data-ttu-id="16bf8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="16bf8-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="16bf8-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="16bf8-115">0x80041008</span></span> | <span data-ttu-id="16bf8-116">O parâmetro `lFlags` não é válido.</span><span class="sxs-lookup"><span data-stu-id="16bf8-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="16bf8-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="16bf8-117">0x8004101d</span></span> | <span data-ttu-id="16bf8-118">Uma segunda chamada para `QualifierSet_BeginEnumeration` foi feita sem uma chamada intermediária para [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="16bf8-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="16bf8-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="16bf8-119">0x80041006</span></span> | <span data-ttu-id="16bf8-120">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="16bf8-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="16bf8-121">0</span><span class="sxs-lookup"><span data-stu-id="16bf8-121">0</span></span> | <span data-ttu-id="16bf8-122">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="16bf8-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="16bf8-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="16bf8-123">Remarks</span></span>

<span data-ttu-id="16bf8-124">Essa função encapsula uma chamada para o [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) método.</span><span class="sxs-lookup"><span data-stu-id="16bf8-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="16bf8-125">Para enumerar todos os qualificadores em um objeto, esse método deve ser chamado antes da primeira chamada para [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="16bf8-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="16bf8-126">A ordem na qual os qualificadores são enumerados é garantida para ser invariável para uma enumeração de determinado.</span><span class="sxs-lookup"><span data-stu-id="16bf8-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="16bf8-127">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="16bf8-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="16bf8-128">Constante</span><span class="sxs-lookup"><span data-stu-id="16bf8-128">Constant</span></span>  |<span data-ttu-id="16bf8-129">Valor</span><span class="sxs-lookup"><span data-stu-id="16bf8-129">Value</span></span>  |<span data-ttu-id="16bf8-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="16bf8-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="16bf8-131">0</span><span class="sxs-lookup"><span data-stu-id="16bf8-131">0</span></span> | <span data-ttu-id="16bf8-132">Retorne os nomes de todos os qualificadores.</span><span class="sxs-lookup"><span data-stu-id="16bf8-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="16bf8-133">0x10</span><span class="sxs-lookup"><span data-stu-id="16bf8-133">0x10</span></span> | <span data-ttu-id="16bf8-134">Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto.</span><span class="sxs-lookup"><span data-stu-id="16bf8-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="16bf8-135">Para uma propriedade: Retorne apenas os qualificadores específicos para a propriedade (incluindo substituições) e não os qualificadores propagados da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="16bf8-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="16bf8-136">Para uma instância: Retorne apenas os nomes específicos da instância qualificador.</span><span class="sxs-lookup"><span data-stu-id="16bf8-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="16bf8-137">Para uma classe: Retorne apenas qualificadores específicos à classe que está sendo derivada.</span><span class="sxs-lookup"><span data-stu-id="16bf8-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="16bf8-138">0x20</span><span class="sxs-lookup"><span data-stu-id="16bf8-138">0x20</span></span> | <span data-ttu-id="16bf8-139">Retornar apenas os nomes dos qualificadores propagados de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="16bf8-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="16bf8-140">Para uma propriedade: Retorno propagados apenas os qualificadores a essa propriedade de definição de classe e não os valores da propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="16bf8-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="16bf8-141">Para uma instância: Retorno apenas desses qualificadores propagados da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="16bf8-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="16bf8-142">Para uma classe: Retornar apenas os nomes de qualificador herdados de classes pai.</span><span class="sxs-lookup"><span data-stu-id="16bf8-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="16bf8-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16bf8-143">Requirements</span></span>

<span data-ttu-id="16bf8-144">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16bf8-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="16bf8-145">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="16bf8-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="16bf8-146">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="16bf8-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="16bf8-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16bf8-147">See also</span></span>

- [<span data-ttu-id="16bf8-148">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="16bf8-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)