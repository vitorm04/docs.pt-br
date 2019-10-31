---
title: Função GetMethodQualifierSet (referência de API não gerenciada)
description: A função GetMethodQualifierSet recupera o conjunto de qualificadores de um método.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1a36200fd214d013a10ed21c22e1f652de2cbf17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102571"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="7c2e9-103">Função GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="7c2e9-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="7c2e9-104">Recupera o qualificador definido para um método específico.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7c2e9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c2e9-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="7c2e9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c2e9-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="7c2e9-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="7c2e9-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="7c2e9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="7c2e9-109">no O nome do método.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-109">[in] The method  name.</span></span> <span data-ttu-id="7c2e9-110">`wszMethod` deve apontar para uma `LPCWSTR`válida.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="7c2e9-111">fora Recebe o ponteiro de interface que permite o acesso aos qualificadores do método.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="7c2e9-112">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="7c2e9-113">Se ocorrer um erro, um novo objeto não será retornado e o ponteiro será definido para apontar para `null`.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c2e9-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7c2e9-114">Return value</span></span>

<span data-ttu-id="7c2e9-115">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="7c2e9-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7c2e9-116">Constante</span><span class="sxs-lookup"><span data-stu-id="7c2e9-116">Constant</span></span>  |<span data-ttu-id="7c2e9-117">Valor</span><span class="sxs-lookup"><span data-stu-id="7c2e9-117">Value</span></span>  |<span data-ttu-id="7c2e9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c2e9-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="7c2e9-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7c2e9-119">0x80041002</span></span> | <span data-ttu-id="7c2e9-120">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7c2e9-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7c2e9-121">0x80041008</span></span> | <span data-ttu-id="7c2e9-122">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7c2e9-123">0</span><span class="sxs-lookup"><span data-stu-id="7c2e9-123">0</span></span> | <span data-ttu-id="7c2e9-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="7c2e9-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c2e9-125">Remarks</span></span>

<span data-ttu-id="7c2e9-126">Essa função encapsula uma chamada para o método [IWbemClassObject:: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="7c2e9-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="7c2e9-127">Uma chamada para essa função só terá suporte se o objeto atual for uma definição de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="7c2e9-128">A manipulação de método não está disponível para ponteiros [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que apontam para instâncias de CIM.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="7c2e9-129">Como cada método pode ter seus próprios qualificadores, o [ponteiro IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permite que o chamador adicione, edite ou exclua esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="7c2e9-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c2e9-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c2e9-130">Requirements</span></span>

<span data-ttu-id="7c2e9-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c2e9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7c2e9-132">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="7c2e9-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="7c2e9-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7c2e9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7c2e9-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c2e9-134">See also</span></span>

- [<span data-ttu-id="7c2e9-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="7c2e9-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
