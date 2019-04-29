---
title: Função GetPropertyOrigin (referência de API não gerenciada)
description: A função GetPropertyOrigin determina a classe em que uma propriedade é declarada.
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
ms.openlocfilehash: 42e5cd6ee438b33fd07fd7c3242cc3c2a6513dd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723247"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="edb25-103">Função GetPropertyOrigin</span><span class="sxs-lookup"><span data-stu-id="edb25-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="edb25-104">Determina a classe na qual uma propriedade é declarada.</span><span class="sxs-lookup"><span data-stu-id="edb25-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="edb25-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edb25-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="edb25-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="edb25-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="edb25-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="edb25-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="edb25-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="edb25-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="edb25-109">[in] O nome da propriedade para o objeto cuja classe proprietária está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="edb25-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="edb25-110">[out] Recebe o nome da classe que é proprietário da propriedade.</span><span class="sxs-lookup"><span data-stu-id="edb25-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="edb25-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="edb25-111">Return value</span></span>

<span data-ttu-id="edb25-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="edb25-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="edb25-113">Constante</span><span class="sxs-lookup"><span data-stu-id="edb25-113">Constant</span></span>  |<span data-ttu-id="edb25-114">Valor</span><span class="sxs-lookup"><span data-stu-id="edb25-114">Value</span></span>  |<span data-ttu-id="edb25-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="edb25-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="edb25-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="edb25-116">0x80041001</span></span> | <span data-ttu-id="edb25-117">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="edb25-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="edb25-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="edb25-118">0x80041002</span></span> | <span data-ttu-id="edb25-119">A propriedade especificada não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="edb25-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="edb25-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="edb25-120">0x80041008</span></span> | <span data-ttu-id="edb25-121">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="edb25-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="edb25-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="edb25-122">0x80041006</span></span> | <span data-ttu-id="edb25-123">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="edb25-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="edb25-124">0</span><span class="sxs-lookup"><span data-stu-id="edb25-124">0</span></span> | <span data-ttu-id="edb25-125">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="edb25-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="edb25-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="edb25-126">Remarks</span></span>

<span data-ttu-id="edb25-127">Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) método.</span><span class="sxs-lookup"><span data-stu-id="edb25-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="edb25-128">Porque uma classe pode herdar as propriedades de um ou mais classes base, os desenvolvedores geralmente querem determinar a propriedade na qual um determinado método está definido.</span><span class="sxs-lookup"><span data-stu-id="edb25-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="edb25-129">O `pstrClassName` parâmetro não deve apontar para um válido `BSTR` antes da função é chamada como esta é uma `out` parâmetro; esse ponteiro não é desalocado depois que a função retorna.</span><span class="sxs-lookup"><span data-stu-id="edb25-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="edb25-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="edb25-130">Requirements</span></span>

<span data-ttu-id="edb25-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edb25-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="edb25-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="edb25-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="edb25-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="edb25-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="edb25-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edb25-134">See also</span></span>

- [<span data-ttu-id="edb25-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="edb25-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)