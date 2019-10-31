---
title: Função QualifierSet_BeginEnumeration (referência de API não gerenciada)
description: A função QualifierSet_BeginEnumeration redefine um enumerador dos qualificadores de um objeto.
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
ms.openlocfilehash: 79edbd876fc9992f088b9adb159e005c735a72cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127319"
---
# <a name="qualifierset_beginenumeration-function"></a><span data-ttu-id="6ae53-103">Função QualifierSet_BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="6ae53-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="6ae53-104">Redefine um enumerador dos qualificadores de um objeto para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="6ae53-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6ae53-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ae53-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="6ae53-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ae53-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="6ae53-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="6ae53-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="6ae53-108">no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="6ae53-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="6ae53-109">no Uma combinação de bits de bit que indica os sinalizadores ou valores descritos na seção [comentários](#remarks) que especifica os qualificadores a serem incluídos na enumeração.</span><span class="sxs-lookup"><span data-stu-id="6ae53-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ae53-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6ae53-110">Return value</span></span>

<span data-ttu-id="6ae53-111">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="6ae53-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6ae53-112">Constante</span><span class="sxs-lookup"><span data-stu-id="6ae53-112">Constant</span></span>  |<span data-ttu-id="6ae53-113">Valor</span><span class="sxs-lookup"><span data-stu-id="6ae53-113">Value</span></span>  |<span data-ttu-id="6ae53-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ae53-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6ae53-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6ae53-115">0x80041008</span></span> | <span data-ttu-id="6ae53-116">O parâmetro `lFlags` não é válido.</span><span class="sxs-lookup"><span data-stu-id="6ae53-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="6ae53-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="6ae53-117">0x8004101d</span></span> | <span data-ttu-id="6ae53-118">Uma segunda chamada para `QualifierSet_BeginEnumeration` foi feita sem uma chamada intermediária para [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6ae53-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6ae53-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6ae53-119">0x80041006</span></span> | <span data-ttu-id="6ae53-120">Não há memória suficiente disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="6ae53-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6ae53-121">0</span><span class="sxs-lookup"><span data-stu-id="6ae53-121">0</span></span> | <span data-ttu-id="6ae53-122">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="6ae53-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6ae53-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ae53-123">Remarks</span></span>

<span data-ttu-id="6ae53-124">Essa função encapsula uma chamada para o método [IWbemQualifierSet:: BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .</span><span class="sxs-lookup"><span data-stu-id="6ae53-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="6ae53-125">Para enumerar todos os qualificadores em um objeto, esse método deve ser chamado antes da primeira chamada para [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="6ae53-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="6ae53-126">A ordem na qual os qualificadores são enumerados é garantida para ser invariável para uma determinada enumeração.</span><span class="sxs-lookup"><span data-stu-id="6ae53-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="6ae53-127">Os sinalizadores que podem ser passados como o argumento `lEnumFlags` são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="6ae53-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="6ae53-128">Constante</span><span class="sxs-lookup"><span data-stu-id="6ae53-128">Constant</span></span>  |<span data-ttu-id="6ae53-129">Valor</span><span class="sxs-lookup"><span data-stu-id="6ae53-129">Value</span></span>  |<span data-ttu-id="6ae53-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ae53-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="6ae53-131">0</span><span class="sxs-lookup"><span data-stu-id="6ae53-131">0</span></span> | <span data-ttu-id="6ae53-132">Retornar os nomes de todos os qualificadores.</span><span class="sxs-lookup"><span data-stu-id="6ae53-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="6ae53-133">0x10</span><span class="sxs-lookup"><span data-stu-id="6ae53-133">0x10</span></span> | <span data-ttu-id="6ae53-134">Retornar somente os nomes de qualificadores específicos para a propriedade ou objeto atual.</span><span class="sxs-lookup"><span data-stu-id="6ae53-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="6ae53-135">Para uma propriedade: retornar somente os qualificadores específicos à propriedade (incluindo substituições), e não os qualificadores propagados da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="6ae53-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="6ae53-136">Para uma instância: retornar apenas nomes de qualificador específicos da instância.</span><span class="sxs-lookup"><span data-stu-id="6ae53-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="6ae53-137">Para uma classe: retornar somente qualificadores específicos à classe que está sendo derivada.</span><span class="sxs-lookup"><span data-stu-id="6ae53-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="6ae53-138">0x20</span><span class="sxs-lookup"><span data-stu-id="6ae53-138">0x20</span></span> | <span data-ttu-id="6ae53-139">Retornar apenas os nomes dos qualificadores propagados de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="6ae53-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="6ae53-140">Para uma propriedade: retornar somente os qualificadores propagados para essa propriedade da definição de classe, e não os da própria propriedade.</span><span class="sxs-lookup"><span data-stu-id="6ae53-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="6ae53-141">Para uma instância: retornar somente os qualificadores propagados da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="6ae53-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="6ae53-142">Para uma classe: retorna somente os nomes de qualificador herdados das classes pai.</span><span class="sxs-lookup"><span data-stu-id="6ae53-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="6ae53-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ae53-143">Requirements</span></span>

<span data-ttu-id="6ae53-144">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ae53-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6ae53-145">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="6ae53-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6ae53-146">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae53-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6ae53-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ae53-147">See also</span></span>

- [<span data-ttu-id="6ae53-148">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="6ae53-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
