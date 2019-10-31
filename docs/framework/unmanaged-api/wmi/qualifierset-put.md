---
title: Função QualifierSet_Put (referência de API não gerenciada)
description: A função QualifierSet_Put grava o qualificador nomeado e seu valor.
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
ms.openlocfilehash: a35025c6d16455a51b7b22d822ba77337ddd894a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120229"
---
# <a name="qualifierset_put-function"></a><span data-ttu-id="1e1b4-103">Função QualifierSet_Put</span><span class="sxs-lookup"><span data-stu-id="1e1b4-103">QualifierSet_Put function</span></span>

<span data-ttu-id="1e1b4-104">Grava o qualificador nomeado e o valor.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="1e1b4-105">O novo qualificador substitui o valor anterior do mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="1e1b4-106">Se o qualificador não existir, ele será criado.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1e1b4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e1b4-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="1e1b4-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e1b4-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1e1b4-109">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1e1b4-110">no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="1e1b4-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="1e1b4-111">no O nome do qualificador a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="1e1b4-112">no Um ponteiro para um `VARIANT` válido que contém o qualificador para gravação.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="1e1b4-113">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="1e1b4-114">no Uma das constantes a seguir que define os tipos de qualificador desejado para este qualificador.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="1e1b4-115">O valor padrão é `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="1e1b4-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="1e1b4-116">Constante</span><span class="sxs-lookup"><span data-stu-id="1e1b4-116">Constant</span></span>  |<span data-ttu-id="1e1b4-117">Valor</span><span class="sxs-lookup"><span data-stu-id="1e1b4-117">Value</span></span>  |<span data-ttu-id="1e1b4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e1b4-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="1e1b4-119">0</span><span class="sxs-lookup"><span data-stu-id="1e1b4-119">0</span></span> | <span data-ttu-id="1e1b4-120">O qualificador pode ser substituído em uma classe ou instância derivada.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="1e1b4-121">**Esse é o valor padrão.**</span><span class="sxs-lookup"><span data-stu-id="1e1b4-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="1e1b4-122">1</span><span class="sxs-lookup"><span data-stu-id="1e1b4-122">1</span></span> | <span data-ttu-id="1e1b4-123">O qualificador é propagado para instâncias.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="1e1b4-124">2</span><span class="sxs-lookup"><span data-stu-id="1e1b4-124">2</span></span> | <span data-ttu-id="1e1b4-125">O qualificador é propagado para classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="1e1b4-126">0x10</span><span class="sxs-lookup"><span data-stu-id="1e1b4-126">0x10</span></span> | <span data-ttu-id="1e1b4-127">O qualificador não pode ser substituído em uma instância ou classe derivada.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="1e1b4-128">0x80</span><span class="sxs-lookup"><span data-stu-id="1e1b4-128">0x80</span></span> | <span data-ttu-id="1e1b4-129">O qualificador está localizado.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1e1b4-130">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1e1b4-130">Return value</span></span>

<span data-ttu-id="1e1b4-131">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="1e1b4-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1e1b4-132">Constante</span><span class="sxs-lookup"><span data-stu-id="1e1b4-132">Constant</span></span>  |<span data-ttu-id="1e1b4-133">Valor</span><span class="sxs-lookup"><span data-stu-id="1e1b4-133">Value</span></span>  |<span data-ttu-id="1e1b4-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e1b4-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="1e1b4-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="1e1b4-135">0x8004101f</span></span> | <span data-ttu-id="1e1b4-136">Houve uma tentativa inválida de especificar o qualificador de **chave** em uma propriedade que não pode ser uma chave.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="1e1b4-137">As chaves são especificadas na definição de classe para um objeto e não podem ser alteradas por instância.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-137">The keys are specified in the class definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1e1b4-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1e1b4-138">0x80041008</span></span> | <span data-ttu-id="1e1b4-139">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="1e1b4-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="1e1b4-140">0x80041029</span></span> | <span data-ttu-id="1e1b4-141">O parâmetro `pVal` não é de um tipo de qualificador legal.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="1e1b4-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="1e1b4-142">0x8004101a</span></span> | <span data-ttu-id="1e1b4-143">Não é possível chamar o método `QualifierSet_Put` no qualificador porque o objeto proprietário não permite substituições.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1e1b4-144">0</span><span class="sxs-lookup"><span data-stu-id="1e1b4-144">0</span></span> | <span data-ttu-id="1e1b4-145">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="1e1b4-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1e1b4-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e1b4-146">Remarks</span></span>

<span data-ttu-id="1e1b4-147">Essa função encapsula uma chamada para o método [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .</span><span class="sxs-lookup"><span data-stu-id="1e1b4-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1e1b4-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e1b4-148">Requirements</span></span>

<span data-ttu-id="1e1b4-149">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e1b4-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1e1b4-150">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="1e1b4-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="1e1b4-151">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1e1b4-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1e1b4-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e1b4-152">See also</span></span>

- [<span data-ttu-id="1e1b4-153">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="1e1b4-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
