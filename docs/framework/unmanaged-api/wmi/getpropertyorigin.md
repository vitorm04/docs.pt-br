---
title: Função GetPropertyOrigin (referência de API não gerenciada)
description: A função GetPropertyOrigin determina a classe na qual uma propriedade é declarada.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c2d0f23f3dd2d52f73f09c32d4e3118a9ed5ea3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798487"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="7870b-103">Função GetPropertyOrigin</span><span class="sxs-lookup"><span data-stu-id="7870b-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="7870b-104">Determina a classe na qual uma propriedade é declarada.</span><span class="sxs-lookup"><span data-stu-id="7870b-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7870b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7870b-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="7870b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7870b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="7870b-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="7870b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="7870b-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="7870b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="7870b-109">no O nome da Propriedade do objeto cuja classe proprietária está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="7870b-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="7870b-110">fora Recebe o nome da classe que possui a propriedade.</span><span class="sxs-lookup"><span data-stu-id="7870b-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="7870b-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7870b-111">Return value</span></span>

<span data-ttu-id="7870b-112">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="7870b-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7870b-113">Constante</span><span class="sxs-lookup"><span data-stu-id="7870b-113">Constant</span></span>  |<span data-ttu-id="7870b-114">Valor</span><span class="sxs-lookup"><span data-stu-id="7870b-114">Value</span></span>  |<span data-ttu-id="7870b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="7870b-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="7870b-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="7870b-116">0x80041001</span></span> | <span data-ttu-id="7870b-117">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="7870b-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="7870b-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7870b-118">0x80041002</span></span> | <span data-ttu-id="7870b-119">A propriedade especificada não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="7870b-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7870b-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7870b-120">0x80041008</span></span> | <span data-ttu-id="7870b-121">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="7870b-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7870b-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7870b-122">0x80041006</span></span> | <span data-ttu-id="7870b-123">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="7870b-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7870b-124">0</span><span class="sxs-lookup"><span data-stu-id="7870b-124">0</span></span> | <span data-ttu-id="7870b-125">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="7870b-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="7870b-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="7870b-126">Remarks</span></span>

<span data-ttu-id="7870b-127">Essa função encapsula uma chamada para o método [IWbemClassObject:: GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) .</span><span class="sxs-lookup"><span data-stu-id="7870b-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="7870b-128">Como uma classe pode herdar propriedades de uma ou mais classes base, os desenvolvedores geralmente desejam determinar a propriedade na qual um determinado método é definido.</span><span class="sxs-lookup"><span data-stu-id="7870b-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="7870b-129">O `pstrClassName` parâmetro não deve apontar para um válido `BSTR` antes que a função seja chamada porque esse é `out` um parâmetro; esse ponteiro não é desalocado depois que a função retorna.</span><span class="sxs-lookup"><span data-stu-id="7870b-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="7870b-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7870b-130">Requirements</span></span>

<span data-ttu-id="7870b-131">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7870b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7870b-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7870b-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="7870b-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7870b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7870b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7870b-134">See also</span></span>

- [<span data-ttu-id="7870b-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="7870b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
