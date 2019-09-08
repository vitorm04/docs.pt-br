---
title: Função GetPropertyHandle (referência de API não gerenciada)
description: A função GetPropertyHandle retorna um identificador exclusivo que identifica uma propriedade.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d72b0da43971a74a08a249b19dfc0d446eeb5e6a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798547"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="4779e-103">Função GetPropertyHandle</span><span class="sxs-lookup"><span data-stu-id="4779e-103">GetPropertyHandle function</span></span>

<span data-ttu-id="4779e-104">Retorna um identificador exclusivo que reconhece uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="4779e-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="4779e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4779e-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="4779e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4779e-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="4779e-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="4779e-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="4779e-108">no Um ponteiro para uma instância de [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="4779e-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="4779e-109">no Uma cadeia de caracteres com o caractere codificado por nulo que contém o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4779e-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="4779e-110">fora Um ponteiro para um [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) membro de enumeração que representa o tipo CIM da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4779e-110">[out] A pointer to a [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="4779e-111">fora Um ponteiro para um inteiro que contém o identificador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4779e-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="4779e-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4779e-112">Return value</span></span>

<span data-ttu-id="4779e-113">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="4779e-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4779e-114">Constante</span><span class="sxs-lookup"><span data-stu-id="4779e-114">Constant</span></span>  |<span data-ttu-id="4779e-115">Valor</span><span class="sxs-lookup"><span data-stu-id="4779e-115">Value</span></span>  |<span data-ttu-id="4779e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4779e-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4779e-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4779e-117">0x80041002</span></span> | <span data-ttu-id="4779e-118">O nome de propriedade especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="4779e-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4779e-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4779e-119">0x80041008</span></span> | <span data-ttu-id="4779e-120">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="4779e-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="4779e-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="4779e-121">0x8004100c</span></span> | <span data-ttu-id="4779e-122">A propriedade solicitada é do tipo `CIM_OBJECT` is `CIM_ARRAY`ou.</span><span class="sxs-lookup"><span data-stu-id="4779e-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4779e-123">0</span><span class="sxs-lookup"><span data-stu-id="4779e-123">0</span></span> | <span data-ttu-id="4779e-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4779e-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="4779e-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="4779e-125">Remarks</span></span>

<span data-ttu-id="4779e-126">Essa função encapsula uma chamada para o método [IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) .</span><span class="sxs-lookup"><span data-stu-id="4779e-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="4779e-127">Você pode usar esse identificador para identificar Propriedades ao usar métodos [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) para ler ou gravar valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4779e-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="4779e-128">Os identificadores podem ser recuperados para propriedades de todos os `CIM_OBJECT` tipos `CIM_ARRAY`de dados diferentes de e.</span><span class="sxs-lookup"><span data-stu-id="4779e-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="4779e-129">Os identificadores retornados funcionam em todas as instâncias de uma classe.</span><span class="sxs-lookup"><span data-stu-id="4779e-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="4779e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4779e-130">Requirements</span></span>

<span data-ttu-id="4779e-131">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4779e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4779e-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4779e-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="4779e-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4779e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4779e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4779e-134">See also</span></span>

- [<span data-ttu-id="4779e-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="4779e-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
