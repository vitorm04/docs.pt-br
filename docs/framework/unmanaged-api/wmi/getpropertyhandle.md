---
title: "Função GetPropertyHandle (referência de API não gerenciada)"
description: "A função GetPropertyHandle retorna um identificador exclusivo que uma propriedade de identidades."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3af852fb4b9899a7937f288ffb65d8ca84e4aef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="e06a6-103">Função GetPropertyHandle</span><span class="sxs-lookup"><span data-stu-id="e06a6-103">GetPropertyHandle function</span></span>
<span data-ttu-id="e06a6-104">Retorna um identificador exclusivo que identifica uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="e06a6-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e06a6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e06a6-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a><span data-ttu-id="e06a6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e06a6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e06a6-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="e06a6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e06a6-108">[in] Um ponteiro para um [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="e06a6-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`wszPropertyName`  
<span data-ttu-id="e06a6-109">[in] Uma cadeia terminada em nulo de characaters UTF16 codificado que contém o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e06a6-109">[in] A null-terminated string of UTF16-encoded characaters that contains the property name.</span></span>   

`pType`  
<span data-ttu-id="e06a6-110">[out] Um ponteiro para um [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) membro de enumeração que representa o tipo CIM da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e06a6-110">[out] A pointer to a [`CIMTYPE`](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`   
<span data-ttu-id="e06a6-111">[out] Um ponteiro para um inteiro que contém o identificador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e06a6-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="e06a6-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e06a6-112">Return value</span></span>

<span data-ttu-id="e06a6-113">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="e06a6-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e06a6-114">Constante</span><span class="sxs-lookup"><span data-stu-id="e06a6-114">Constant</span></span>  |<span data-ttu-id="e06a6-115">Valor</span><span class="sxs-lookup"><span data-stu-id="e06a6-115">Value</span></span>  |<span data-ttu-id="e06a6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e06a6-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e06a6-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e06a6-117">0x80041002</span></span> | <span data-ttu-id="e06a6-118">O nome da propriedade especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="e06a6-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e06a6-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e06a6-119">0x80041008</span></span> | <span data-ttu-id="e06a6-120">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="e06a6-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="e06a6-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="e06a6-121">0x8004100c</span></span> | <span data-ttu-id="e06a6-122">A propriedade solicitada é do tipo são `CIM_OBJECT` ou `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="e06a6-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e06a6-123">0</span><span class="sxs-lookup"><span data-stu-id="e06a6-123">0</span></span> | <span data-ttu-id="e06a6-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e06a6-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e06a6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="e06a6-125">Remarks</span></span>

<span data-ttu-id="e06a6-126">Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="e06a6-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e06a6-127">Você pode usar esse identificador para identificar as propriedades ao usar [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) métodos para ler ou gravar valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e06a6-127">You can use this handle to identify properties when using  [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) methods to read or write property values.</span></span>

<span data-ttu-id="e06a6-128">Identificadores podem ser recuperados para propriedades de todos os tipos de dados diferente de `CIM_OBJECT` e `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="e06a6-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="e06a6-129">Retornado trabalho identificadores em todas as instâncias de uma classe.</span><span class="sxs-lookup"><span data-stu-id="e06a6-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="e06a6-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e06a6-130">Requirements</span></span>  
<span data-ttu-id="e06a6-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e06a6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e06a6-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e06a6-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e06a6-133">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e06a6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06a6-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e06a6-134">See also</span></span>  
[<span data-ttu-id="e06a6-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="e06a6-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
