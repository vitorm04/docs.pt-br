---
title: Função GetPropertyQualifierSet (referência de API não gerenciada)
description: A função GetPropertyQualifierSet recupera o qualificador definido para uma propriedade.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 588c56c80cc55df3689178875a9a0500cd0ca7b8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636400"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="e5b54-103">Função GetPropertyQualifierSet</span><span class="sxs-lookup"><span data-stu-id="e5b54-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="e5b54-104">Recupera o qualificador definido para uma propriedade específica.</span><span class="sxs-lookup"><span data-stu-id="e5b54-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e5b54-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5b54-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="e5b54-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5b54-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e5b54-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="e5b54-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e5b54-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="e5b54-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="e5b54-109">[in] O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5b54-109">[in] The property  name.</span></span> <span data-ttu-id="e5b54-110">`wszProperty` deve apontar para um válido `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="e5b54-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="e5b54-111">[out] Recebe o ponteiro de interface que permite o acesso para os qualificadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5b54-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="e5b54-112">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e5b54-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="e5b54-113">Se ocorrer um erro, um novo objeto não é retornado e o ponteiro é definido para apontar para `null`.</span><span class="sxs-lookup"><span data-stu-id="e5b54-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5b54-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e5b54-114">Return value</span></span>

<span data-ttu-id="e5b54-115">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="e5b54-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e5b54-116">Constante</span><span class="sxs-lookup"><span data-stu-id="e5b54-116">Constant</span></span>  |<span data-ttu-id="e5b54-117">Valor</span><span class="sxs-lookup"><span data-stu-id="e5b54-117">Value</span></span>  |<span data-ttu-id="e5b54-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5b54-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e5b54-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e5b54-119">0x80041001</span></span> | <span data-ttu-id="e5b54-120">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="e5b54-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="e5b54-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e5b54-121">0x80041002</span></span> | <span data-ttu-id="e5b54-122">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="e5b54-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e5b54-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e5b54-123">0x80041006</span></span> | <span data-ttu-id="e5b54-124">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="e5b54-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e5b54-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e5b54-125">0x80041008</span></span> | <span data-ttu-id="e5b54-126">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="e5b54-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="e5b54-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="e5b54-127">0x80041030</span></span> | <span data-ttu-id="e5b54-128">A função tenta obter qualificadores de uma propriedade do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5b54-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e5b54-129">0</span><span class="sxs-lookup"><span data-stu-id="e5b54-129">0</span></span> | <span data-ttu-id="e5b54-130">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e5b54-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e5b54-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5b54-131">Remarks</span></span>

<span data-ttu-id="e5b54-132">Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) método.</span><span class="sxs-lookup"><span data-stu-id="e5b54-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="e5b54-133">Uma chamada para essa função tem suporte apenas se o objeto atual é uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="e5b54-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="e5b54-134">Manipulação de método não está disponível para [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponteiros que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="e5b54-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="e5b54-135">Porque cada método pode ter seus próprio qualificadores, o [IWbemQualifierSet ponteiro](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permite que o chamador adicionar, editar ou excluir esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="e5b54-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="e5b54-136">Como as propriedades do sistema não têm nenhum qualificador, a função retornará `WBEM_E_SYSTEM_PROPERTY` se você tentar obter uma [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) ponteiro para uma propriedade do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5b54-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5b54-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5b54-137">Requirements</span></span>

<span data-ttu-id="e5b54-138">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b54-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e5b54-139">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e5b54-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e5b54-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b54-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e5b54-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5b54-141">See also</span></span>

- [<span data-ttu-id="e5b54-142">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="e5b54-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
