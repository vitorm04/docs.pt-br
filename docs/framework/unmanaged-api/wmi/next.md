---
title: Próxima função (referência de API não gerenciada)
description: A função Next recupera a próxima Propriedade em uma enumeração.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95cea4cb3e7e7df2b6b52256a440b9a8d544f2db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798415"
---
# <a name="next-function"></a><span data-ttu-id="81753-103">Próxima função</span><span class="sxs-lookup"><span data-stu-id="81753-103">Next function</span></span>
<span data-ttu-id="81753-104">Recupera a próxima Propriedade em uma enumeração que começa com uma chamada para [BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="81753-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="81753-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81753-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="81753-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81753-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="81753-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="81753-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="81753-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="81753-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="81753-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="81753-109">[in] Reserved.</span></span> <span data-ttu-id="81753-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="81753-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="81753-111">fora Um novo `BSTR` que contém o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="81753-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="81753-112">Você pode definir esse parâmetro como `null` se o nome não for necessário.</span><span class="sxs-lookup"><span data-stu-id="81753-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="81753-113">fora Um `VARIANT` preenchido com o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="81753-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="81753-114">Você pode definir esse parâmetro como `null` se o valor não for necessário.</span><span class="sxs-lookup"><span data-stu-id="81753-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="81753-115">Se a função retornar um código de erro, `VARIANT` o passado `pVal` para será deixado sem modificações.</span><span class="sxs-lookup"><span data-stu-id="81753-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="81753-116">fora Um ponteiro para uma `CIMTYPE` variável (um `LONG` no qual o tipo da propriedade é colocado).</span><span class="sxs-lookup"><span data-stu-id="81753-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="81753-117">O valor dessa propriedade pode ser a `VT_NULL_VARIANT`; nesse caso, é necessário determinar o tipo real da propriedade.</span><span class="sxs-lookup"><span data-stu-id="81753-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="81753-118">Esse parâmetro também pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="81753-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="81753-119">fora `null`, ou um valor que recebe informações sobre a origem da propriedade.</span><span class="sxs-lookup"><span data-stu-id="81753-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="81753-120">Consulte a seção [Comentários] para obter os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="81753-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="81753-121">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="81753-121">Return value</span></span>

<span data-ttu-id="81753-122">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="81753-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="81753-123">Constante</span><span class="sxs-lookup"><span data-stu-id="81753-123">Constant</span></span>  |<span data-ttu-id="81753-124">Valor</span><span class="sxs-lookup"><span data-stu-id="81753-124">Value</span></span>  |<span data-ttu-id="81753-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="81753-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="81753-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="81753-126">0x80041001</span></span> | <span data-ttu-id="81753-127">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="81753-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="81753-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="81753-128">0x80041008</span></span> | <span data-ttu-id="81753-129">Um parâmetro é inválido.</span><span class="sxs-lookup"><span data-stu-id="81753-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="81753-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="81753-130">0x8004101d</span></span> | <span data-ttu-id="81753-131">Não havia nenhuma chamada para a [`BeginEnumeration`](beginenumeration.md) função.</span><span class="sxs-lookup"><span data-stu-id="81753-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="81753-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="81753-132">0x80041006</span></span> | <span data-ttu-id="81753-133">Não há memória suficiente disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="81753-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="81753-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="81753-134">0x80041015</span></span> | <span data-ttu-id="81753-135">A chamada de procedimento remoto entre o processo atual e o gerenciamento do Windows falhou.</span><span class="sxs-lookup"><span data-stu-id="81753-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="81753-136">0</span><span class="sxs-lookup"><span data-stu-id="81753-136">0</span></span> | <span data-ttu-id="81753-137">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="81753-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="81753-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="81753-138">0x40005</span></span> | <span data-ttu-id="81753-139">Não há mais propriedades na enumeração.</span><span class="sxs-lookup"><span data-stu-id="81753-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="81753-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="81753-140">Remarks</span></span>

<span data-ttu-id="81753-141">Essa função encapsula uma chamada para o método [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .</span><span class="sxs-lookup"><span data-stu-id="81753-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="81753-142">Esse método também retorna propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="81753-142">This method also returns system properties.</span></span>

<span data-ttu-id="81753-143">Se o tipo subjacente da propriedade for um caminho de objeto, uma data ou hora ou outro tipo especial, o tipo retornado não conterá informações suficientes.</span><span class="sxs-lookup"><span data-stu-id="81753-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="81753-144">O chamador deve examinar a `CIMTYPE` propriedade especificada para determinar se a propriedade é uma referência de objeto, uma data ou hora ou outro tipo especial.</span><span class="sxs-lookup"><span data-stu-id="81753-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="81753-145">Se `plFlavor` `LONG` não `null`for, o valor receberá informações sobre a origem da propriedade, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="81753-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="81753-146">Constante</span><span class="sxs-lookup"><span data-stu-id="81753-146">Constant</span></span>  |<span data-ttu-id="81753-147">Valor</span><span class="sxs-lookup"><span data-stu-id="81753-147">Value</span></span>  |<span data-ttu-id="81753-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="81753-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="81753-149">0x40</span><span class="sxs-lookup"><span data-stu-id="81753-149">0x40</span></span> | <span data-ttu-id="81753-150">A propriedade é uma propriedade padrão do sistema.</span><span class="sxs-lookup"><span data-stu-id="81753-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="81753-151">0x20</span><span class="sxs-lookup"><span data-stu-id="81753-151">0x20</span></span> | <span data-ttu-id="81753-152">Para uma classe: A propriedade é herdada da classe pai.</span><span class="sxs-lookup"><span data-stu-id="81753-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="81753-153">Para uma instância: A propriedade, embora herdada da classe pai, não foi modificada pela instância.</span><span class="sxs-lookup"><span data-stu-id="81753-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="81753-154">0</span><span class="sxs-lookup"><span data-stu-id="81753-154">0</span></span> | <span data-ttu-id="81753-155">Para uma classe: A propriedade pertence à classe derivada.</span><span class="sxs-lookup"><span data-stu-id="81753-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="81753-156">Para uma instância: A propriedade é modificada pela instância; ou seja, um valor foi fornecido ou um qualificador foi adicionado ou modificado.</span><span class="sxs-lookup"><span data-stu-id="81753-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="81753-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81753-157">Requirements</span></span>

<span data-ttu-id="81753-158">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81753-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="81753-159">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="81753-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="81753-160">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81753-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="81753-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81753-161">See also</span></span>

- [<span data-ttu-id="81753-162">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="81753-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
