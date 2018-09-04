---
title: Função QualifierSet_Put (referência de API não gerenciada)
description: A função QualifierSet_Put grava qualificador nomeado e seu valor.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b2e1b08d1091e482c6b02fe015a58219ff80768
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517555"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="77cba-103">Função QualifierSet_Put</span><span class="sxs-lookup"><span data-stu-id="77cba-103">QualifierSet_Put function</span></span>
<span data-ttu-id="77cba-104">Grava o qualificador nomeado e o valor.</span><span class="sxs-lookup"><span data-stu-id="77cba-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="77cba-105">O novo qualificador substitui o valor anterior do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="77cba-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="77cba-106">Se o qualificador não existir, ele é criado.</span><span class="sxs-lookup"><span data-stu-id="77cba-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="77cba-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77cba-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="77cba-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77cba-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="77cba-109">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="77cba-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="77cba-110">[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.</span><span class="sxs-lookup"><span data-stu-id="77cba-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="77cba-111">[in] O nome do qualificador de escrever.</span><span class="sxs-lookup"><span data-stu-id="77cba-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="77cba-112">`pVal` [in] Um ponteiro para um válido `VARIANT` que contém o qualificador de escrever.</span><span class="sxs-lookup"><span data-stu-id="77cba-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="77cba-113">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="77cba-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="77cba-114">`lFlavor` [in] Uma das seguintes constantes que define os tipos de qualificador desejado para esse qualificador.</span><span class="sxs-lookup"><span data-stu-id="77cba-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="77cba-115">O valor padrão é `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="77cba-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="77cba-116">Constante</span><span class="sxs-lookup"><span data-stu-id="77cba-116">Constant</span></span>  |<span data-ttu-id="77cba-117">Valor</span><span class="sxs-lookup"><span data-stu-id="77cba-117">Value</span></span>  |<span data-ttu-id="77cba-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="77cba-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="77cba-119">0</span><span class="sxs-lookup"><span data-stu-id="77cba-119">0</span></span> | <span data-ttu-id="77cba-120">O qualificador pode ser substituído em uma classe derivada ou instância.</span><span class="sxs-lookup"><span data-stu-id="77cba-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="77cba-121">**Esse é o valor padrão.**</span><span class="sxs-lookup"><span data-stu-id="77cba-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="77cba-122">1</span><span class="sxs-lookup"><span data-stu-id="77cba-122">1</span></span> | <span data-ttu-id="77cba-123">O qualificador é propagado para instâncias.</span><span class="sxs-lookup"><span data-stu-id="77cba-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="77cba-124">2</span><span class="sxs-lookup"><span data-stu-id="77cba-124">2</span></span> | <span data-ttu-id="77cba-125">O qualificador é propagado para classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="77cba-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="77cba-126">' WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="77cba-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="77cba-127">0x10</span><span class="sxs-lookup"><span data-stu-id="77cba-127">0x10</span></span> | <span data-ttu-id="77cba-128">O qualificador não pode ser substituído em uma instância ou classe derivada.</span><span class="sxs-lookup"><span data-stu-id="77cba-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="77cba-129">' WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="77cba-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="77cba-130">0x80</span><span class="sxs-lookup"><span data-stu-id="77cba-130">0x80</span></span> | <span data-ttu-id="77cba-131">O qualificador é localizado.</span><span class="sxs-lookup"><span data-stu-id="77cba-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="77cba-132">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="77cba-132">Return value</span></span>

<span data-ttu-id="77cba-133">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="77cba-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="77cba-134">Constante</span><span class="sxs-lookup"><span data-stu-id="77cba-134">Constant</span></span>  |<span data-ttu-id="77cba-135">Valor</span><span class="sxs-lookup"><span data-stu-id="77cba-135">Value</span></span>  |<span data-ttu-id="77cba-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="77cba-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="77cba-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="77cba-137">0x8004101f</span></span> | <span data-ttu-id="77cba-138">Houve uma tentativa inválida de especificar o **chave** qualificador em uma propriedade que não pode ser uma chave.</span><span class="sxs-lookup"><span data-stu-id="77cba-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="77cba-139">As chaves são especificadas om o c; a definição de ass para um objeto e não podem ser alterados em uma base por instância.</span><span class="sxs-lookup"><span data-stu-id="77cba-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="77cba-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="77cba-140">0x80041008</span></span> | <span data-ttu-id="77cba-141">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="77cba-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="77cba-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="77cba-142">0x80041029</span></span> | <span data-ttu-id="77cba-143">O `pVal` parâmetro não é de um tipo de Qualificador legal.</span><span class="sxs-lookup"><span data-stu-id="77cba-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="77cba-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="77cba-144">0x8004101a</span></span> | <span data-ttu-id="77cba-145">Não é possível chamar o `QualifierSet_Put` no qualificador porque o objeto proprietário não permite substituições de método.</span><span class="sxs-lookup"><span data-stu-id="77cba-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="77cba-146">0</span><span class="sxs-lookup"><span data-stu-id="77cba-146">0</span></span> | <span data-ttu-id="77cba-147">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="77cba-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="77cba-148">Comentários</span><span class="sxs-lookup"><span data-stu-id="77cba-148">Remarks</span></span>

<span data-ttu-id="77cba-149">Essa função encapsula uma chamada para o [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) método.</span><span class="sxs-lookup"><span data-stu-id="77cba-149">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="77cba-150">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77cba-150">Requirements</span></span>  
 <span data-ttu-id="77cba-151">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77cba-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77cba-152">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="77cba-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="77cba-153">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="77cba-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cba-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77cba-154">See also</span></span>  
[<span data-ttu-id="77cba-155">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="77cba-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
