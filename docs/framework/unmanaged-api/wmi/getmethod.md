---
title: Função GetMethod (referência de API não gerenciada)
description: A função GetMethod recupera informações sobre um método.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 48986f5ff1cbbb45840ec1a059aa86711848d717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102584"
---
# <a name="getmethod-function"></a><span data-ttu-id="c813e-103">Função GetMethod</span><span class="sxs-lookup"><span data-stu-id="c813e-103">GetMethod function</span></span>

<span data-ttu-id="c813e-104">Recupera informações sobre o método especifico.</span><span class="sxs-lookup"><span data-stu-id="c813e-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c813e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c813e-105">Syntax</span></span>

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a><span data-ttu-id="c813e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c813e-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="c813e-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="c813e-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="c813e-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="c813e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="c813e-109">no O nome do método.</span><span class="sxs-lookup"><span data-stu-id="c813e-109">[in] The method name.</span></span> <span data-ttu-id="c813e-110">Esse parâmetro não pode ser `null` e deve apontar para um `LPCWSTR`válido.</span><span class="sxs-lookup"><span data-stu-id="c813e-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="c813e-111">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="c813e-111">[in] Reserved.</span></span> <span data-ttu-id="c813e-112">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="c813e-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="c813e-113">fora Um ponteiro para o endereço de uma instância [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve os parâmetros in para o método.</span><span class="sxs-lookup"><span data-stu-id="c813e-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="c813e-114">Esse parâmetro será ignorado se for definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="c813e-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="c813e-115">fora Um ponteiro para o endereço de uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve os parâmetros de saída para o método.</span><span class="sxs-lookup"><span data-stu-id="c813e-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="c813e-116">Esse parâmetro será ignorado se for definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="c813e-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="c813e-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c813e-117">Return value</span></span>

<span data-ttu-id="c813e-118">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c813e-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c813e-119">Constante</span><span class="sxs-lookup"><span data-stu-id="c813e-119">Constant</span></span>  |<span data-ttu-id="c813e-120">Valor</span><span class="sxs-lookup"><span data-stu-id="c813e-120">Value</span></span>  |<span data-ttu-id="c813e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c813e-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="c813e-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c813e-122">0x80041002</span></span> | <span data-ttu-id="c813e-123">A propriedade especificada não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="c813e-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c813e-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c813e-124">0x80041006</span></span> | <span data-ttu-id="c813e-125">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="c813e-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c813e-126">0</span><span class="sxs-lookup"><span data-stu-id="c813e-126">0</span></span> | <span data-ttu-id="c813e-127">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c813e-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c813e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="c813e-128">Remarks</span></span>

<span data-ttu-id="c813e-129">Essa função encapsula uma chamada para o método [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="c813e-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="c813e-130">O gerenciamento do Windows pode definir o ponteiro [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) para `null` se o método não tiver parâmetros in.</span><span class="sxs-lookup"><span data-stu-id="c813e-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="c813e-131">Em `ppInSignature` e `ppOutSignature` descrevem os parâmetros in e out, respectivamente, como propriedades em uma instância `IWbemClassObject` da classe System [_Parameters](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="c813e-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="c813e-132">As propriedades em `ppInSignature` são nomeadas `Param`*n*, em que *n* é a posição do parâmetro na assinatura do método (como `Param1`, `Param2`, etc.).</span><span class="sxs-lookup"><span data-stu-id="c813e-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="c813e-133">As propriedades em `ppOutSignature` também são nomeadas `Param`*n*e o valor de retorno é nomeado `ReturnValue`.</span><span class="sxs-lookup"><span data-stu-id="c813e-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="c813e-134">Para obter mais informações e um exemplo, consulte [método IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="c813e-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="c813e-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c813e-135">Requirements</span></span>

<span data-ttu-id="c813e-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c813e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c813e-137">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="c813e-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="c813e-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c813e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c813e-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c813e-139">See also</span></span>

- [<span data-ttu-id="c813e-140">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c813e-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
