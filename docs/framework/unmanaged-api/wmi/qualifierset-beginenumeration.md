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
ms.openlocfilehash: 2d20701237501834c611c4e498c39597cf275176
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518680"
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="2b4d0-103">Função QualifierSet_BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="2b4d0-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="2b4d0-104">Redefine um enumerador dos qualificadores de um objeto para o início da enumeração.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2b4d0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b4d0-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="2b4d0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b4d0-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="2b4d0-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="2b4d0-108">[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="2b4d0-109">[in] Uma combinação bit a bit de sinalizadores ou valores descritos na [comentários](#remarks) seção que especifica os qualificadores a serem incluídos na enumeração.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b4d0-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2b4d0-110">Return value</span></span>

<span data-ttu-id="2b4d0-111">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="2b4d0-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2b4d0-112">Constante</span><span class="sxs-lookup"><span data-stu-id="2b4d0-112">Constant</span></span>  |<span data-ttu-id="2b4d0-113">Valor</span><span class="sxs-lookup"><span data-stu-id="2b4d0-113">Value</span></span>  |<span data-ttu-id="2b4d0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b4d0-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2b4d0-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2b4d0-115">0x80041008</span></span> | <span data-ttu-id="2b4d0-116">O parâmetro `lFlags` não é válido.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="2b4d0-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2b4d0-117">0x8004101d</span></span> | <span data-ttu-id="2b4d0-118">Uma segunda chamada para `QualifierSet_BeginEnumeration` foi feita sem uma chamada intermediária para [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d0-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2b4d0-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2b4d0-119">0x80041006</span></span> | <span data-ttu-id="2b4d0-120">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2b4d0-121">0</span><span class="sxs-lookup"><span data-stu-id="2b4d0-121">0</span></span> | <span data-ttu-id="2b4d0-122">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2b4d0-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b4d0-123">Remarks</span></span>

<span data-ttu-id="2b4d0-124">Essa função encapsula uma chamada para o [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) método.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="2b4d0-125">Para enumerar todos os qualificadores em um objeto, esse método deve ser chamado antes da primeira chamada para [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d0-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="2b4d0-126">A ordem na qual os qualificadores são enumerados é garantida para ser invariável para uma enumeração de determinado.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="2b4d0-127">Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="2b4d0-128">Constante</span><span class="sxs-lookup"><span data-stu-id="2b4d0-128">Constant</span></span>  |<span data-ttu-id="2b4d0-129">Valor</span><span class="sxs-lookup"><span data-stu-id="2b4d0-129">Value</span></span>  |<span data-ttu-id="2b4d0-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b4d0-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="2b4d0-131">0</span><span class="sxs-lookup"><span data-stu-id="2b4d0-131">0</span></span> | <span data-ttu-id="2b4d0-132">Retorne os nomes de todos os qualificadores.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="2b4d0-133">0x10</span><span class="sxs-lookup"><span data-stu-id="2b4d0-133">0x10</span></span> | <span data-ttu-id="2b4d0-134">Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="2b4d0-135">Para uma propriedade: retornar apenas os qualificadores específica para a propriedade (incluindo substituições), e não os qualificadores propagadas da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="2b4d0-136">Para uma instância: retornar apenas os nomes de qualificador de específico da instância.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="2b4d0-137">Para uma classe: retornar apenas os qualificadores específica para o beiong de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="2b4d0-138">0x20</span><span class="sxs-lookup"><span data-stu-id="2b4d0-138">0x20</span></span> | <span data-ttu-id="2b4d0-139">Retornar apenas os nomes dos qualificadores propagados de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="2b4d0-140">Para uma propriedade: retorno propagados apenas os qualificadores a essa propriedade de definição de classe e não os valores da propriedade em si.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="2b4d0-141">Para uma instância: retorno apenas desses qualificadores propagados da definição da classe.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="2b4d0-142">Para uma classe: retornar apenas os nomes de qualificador herdados de classes pai.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2b4d0-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b4d0-143">Requirements</span></span>  
 <span data-ttu-id="2b4d0-144">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d0-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b4d0-145">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2b4d0-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2b4d0-146">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b4d0-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b4d0-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b4d0-147">See also</span></span>  
[<span data-ttu-id="2b4d0-148">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="2b4d0-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
