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
ms.openlocfilehash: 4133145c7bea1fb3c018d809b9fea3de38270619
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127451"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="3dbd2-103">Função GetPropertyQualifierSet</span><span class="sxs-lookup"><span data-stu-id="3dbd2-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="3dbd2-104">Recupera o qualificador definido para uma propriedade específica.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3dbd2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3dbd2-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="3dbd2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3dbd2-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="3dbd2-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="3dbd2-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="3dbd2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="3dbd2-109">no O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-109">[in] The property  name.</span></span> <span data-ttu-id="3dbd2-110">`wszProperty` deve apontar para uma `LPCWSTR`válida.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="3dbd2-111">fora Recebe o ponteiro de interface que permite o acesso aos qualificadores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="3dbd2-112">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="3dbd2-113">Se ocorrer um erro, um novo objeto não será retornado e o ponteiro será definido para apontar para `null`.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="3dbd2-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3dbd2-114">Return value</span></span>

<span data-ttu-id="3dbd2-115">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="3dbd2-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3dbd2-116">Constante</span><span class="sxs-lookup"><span data-stu-id="3dbd2-116">Constant</span></span>  |<span data-ttu-id="3dbd2-117">Valor</span><span class="sxs-lookup"><span data-stu-id="3dbd2-117">Value</span></span>  |<span data-ttu-id="3dbd2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3dbd2-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3dbd2-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3dbd2-119">0x80041001</span></span> | <span data-ttu-id="3dbd2-120">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="3dbd2-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="3dbd2-121">0x80041002</span></span> | <span data-ttu-id="3dbd2-122">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3dbd2-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3dbd2-123">0x80041006</span></span> | <span data-ttu-id="3dbd2-124">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3dbd2-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3dbd2-125">0x80041008</span></span> | <span data-ttu-id="3dbd2-126">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="3dbd2-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="3dbd2-127">0x80041030</span></span> | <span data-ttu-id="3dbd2-128">A função tenta obter qualificadores de uma propriedade do sistema.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3dbd2-129">0</span><span class="sxs-lookup"><span data-stu-id="3dbd2-129">0</span></span> | <span data-ttu-id="3dbd2-130">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="3dbd2-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="3dbd2-131">Remarks</span></span>

<span data-ttu-id="3dbd2-132">Essa função encapsula uma chamada para o método [IWbemClassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="3dbd2-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="3dbd2-133">Uma chamada para essa função só terá suporte se o objeto atual for uma definição de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="3dbd2-134">A manipulação de método não está disponível para ponteiros [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que apontam para instâncias de CIM.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="3dbd2-135">Como cada método pode ter seus próprios qualificadores, o [ponteiro IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permite que o chamador adicione, edite ou exclua esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="3dbd2-136">Como as propriedades do sistema não têm nenhum qualificador, a função retorna `WBEM_E_SYSTEM_PROPERTY` se você tentar obter um ponteiro [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) para uma propriedade do sistema.</span><span class="sxs-lookup"><span data-stu-id="3dbd2-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="3dbd2-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3dbd2-137">Requirements</span></span>

<span data-ttu-id="3dbd2-138">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dbd2-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3dbd2-139">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="3dbd2-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="3dbd2-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3dbd2-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3dbd2-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dbd2-141">See also</span></span>

- [<span data-ttu-id="3dbd2-142">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="3dbd2-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
