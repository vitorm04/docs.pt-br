---
title: Obter função (referência de API não gerenciada)
description: A função Get recupera o valor da propriedade especificada.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 265d3edbd3175eebcf6fd35be24f5b66144c960f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037949"
---
# <a name="get-function"></a><span data-ttu-id="db57a-103">Função Get</span><span class="sxs-lookup"><span data-stu-id="db57a-103">Get function</span></span>

<span data-ttu-id="db57a-104">Recupera o valor da propriedade especificada, se existir.</span><span class="sxs-lookup"><span data-stu-id="db57a-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="db57a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db57a-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a><span data-ttu-id="db57a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db57a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="db57a-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="db57a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="db57a-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="db57a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="db57a-109">no O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="db57a-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="db57a-110">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="db57a-110">[in] Reserved.</span></span> <span data-ttu-id="db57a-111">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="db57a-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="db57a-112">fora Se a função retornar com êxito, conterá o valor da `wszName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="db57a-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="db57a-113">O `pval` argumento recebe o tipo e o valor corretos para o qualificador.</span><span class="sxs-lookup"><span data-stu-id="db57a-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="db57a-114">fora Se a função retornar com êxito, conterá uma [constante do tipo CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) que indica o tipo de propriedade.</span><span class="sxs-lookup"><span data-stu-id="db57a-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="db57a-115">Seu valor também pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="db57a-115">Its value can also be `null`.</span></span> 

`plFlavor`\
<span data-ttu-id="db57a-116">fora Se a função retornar com êxito, o receberá informações sobre a origem da propriedade.</span><span class="sxs-lookup"><span data-stu-id="db57a-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="db57a-117">Seu valor pode ser `null`ou uma das seguintes constantes WBEM_FLAVOR_TYPE definidas no arquivo de cabeçalho *WbemCli. h* :</span><span class="sxs-lookup"><span data-stu-id="db57a-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="db57a-118">Constante</span><span class="sxs-lookup"><span data-stu-id="db57a-118">Constant</span></span>  |<span data-ttu-id="db57a-119">Valor</span><span class="sxs-lookup"><span data-stu-id="db57a-119">Value</span></span>  |<span data-ttu-id="db57a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="db57a-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="db57a-121">0x40</span><span class="sxs-lookup"><span data-stu-id="db57a-121">0x40</span></span> | <span data-ttu-id="db57a-122">A propriedade é uma propriedade padrão do sistema.</span><span class="sxs-lookup"><span data-stu-id="db57a-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="db57a-123">0x20</span><span class="sxs-lookup"><span data-stu-id="db57a-123">0x20</span></span> | <span data-ttu-id="db57a-124">Para uma classe: A propriedade é herdada da classe pai.</span><span class="sxs-lookup"><span data-stu-id="db57a-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="db57a-125">Para uma instância: A propriedade, embora herdada da classe pai, não foi modificada pela instância.</span><span class="sxs-lookup"><span data-stu-id="db57a-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="db57a-126">0</span><span class="sxs-lookup"><span data-stu-id="db57a-126">0</span></span> | <span data-ttu-id="db57a-127">Para uma classe: A propriedade pertence à classe derivada.</span><span class="sxs-lookup"><span data-stu-id="db57a-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="db57a-128">Para uma instância: A propriedade é modificada pela instância; ou seja, um valor foi fornecido ou um qualificador foi adicionado ou modificado.</span><span class="sxs-lookup"><span data-stu-id="db57a-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="db57a-129">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="db57a-129">Return value</span></span>

<span data-ttu-id="db57a-130">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="db57a-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="db57a-131">Constante</span><span class="sxs-lookup"><span data-stu-id="db57a-131">Constant</span></span>  |<span data-ttu-id="db57a-132">Valor</span><span class="sxs-lookup"><span data-stu-id="db57a-132">Value</span></span>  |<span data-ttu-id="db57a-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="db57a-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="db57a-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="db57a-134">0x80041001</span></span> | <span data-ttu-id="db57a-135">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="db57a-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="db57a-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="db57a-136">0x80041008</span></span> | <span data-ttu-id="db57a-137">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="db57a-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="db57a-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="db57a-138">0x80041002</span></span> | <span data-ttu-id="db57a-139">A propriedade especificada não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="db57a-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="db57a-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="db57a-140">0x80041006</span></span> | <span data-ttu-id="db57a-141">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="db57a-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="db57a-142">0</span><span class="sxs-lookup"><span data-stu-id="db57a-142">0</span></span> | <span data-ttu-id="db57a-143">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="db57a-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="db57a-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="db57a-144">Remarks</span></span>

<span data-ttu-id="db57a-145">Essa função encapsula uma chamada para o método [IWbemClassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .</span><span class="sxs-lookup"><span data-stu-id="db57a-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="db57a-146">A `Get` função também pode retornar propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="db57a-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="db57a-147">O argumento recebe o tipo e o valor corretos para o qualificador e a função [VariantInit com](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) `pVal`</span><span class="sxs-lookup"><span data-stu-id="db57a-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="db57a-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db57a-148">Requirements</span></span>

 <span data-ttu-id="db57a-149">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db57a-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="db57a-150">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="db57a-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="db57a-151">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="db57a-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="db57a-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db57a-152">See also</span></span>

- [<span data-ttu-id="db57a-153">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="db57a-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
