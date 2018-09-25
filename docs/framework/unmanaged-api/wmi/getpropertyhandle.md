---
title: Função GetPropertyHandle (referência de API não gerenciada)
description: A função GetPropertyHandle retorna um identificador exclusivo que uma propriedade de identidades.
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
ms.openlocfilehash: 94171b0708c97eb7510e916e451ed03645d706f3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109729"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="ac67e-103">Função GetPropertyHandle</span><span class="sxs-lookup"><span data-stu-id="ac67e-103">GetPropertyHandle function</span></span>
<span data-ttu-id="ac67e-104">Retorna um identificador exclusivo que reconhece uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="ac67e-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="ac67e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac67e-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a><span data-ttu-id="ac67e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac67e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ac67e-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="ac67e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ac67e-108">[in] Um ponteiro para um [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instância.</span><span class="sxs-lookup"><span data-stu-id="ac67e-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`  
<span data-ttu-id="ac67e-109">[in] Uma cadeia terminada em nulo de characaters codificada em UTF16 que contém o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ac67e-109">[in] A null-terminated string of UTF16-encoded characaters that contains the property name.</span></span>   

`pType`  
<span data-ttu-id="ac67e-110">[out] Um ponteiro para um [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) membro de enumeração que representa o tipo CIM da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ac67e-110">[out] A pointer to a [`CIMTYPE`](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`   
<span data-ttu-id="ac67e-111">[out] Um ponteiro para um inteiro que contém o identificador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="ac67e-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="ac67e-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ac67e-112">Return value</span></span>

<span data-ttu-id="ac67e-113">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="ac67e-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ac67e-114">Constante</span><span class="sxs-lookup"><span data-stu-id="ac67e-114">Constant</span></span>  |<span data-ttu-id="ac67e-115">Valor</span><span class="sxs-lookup"><span data-stu-id="ac67e-115">Value</span></span>  |<span data-ttu-id="ac67e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac67e-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ac67e-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ac67e-117">0x80041002</span></span> | <span data-ttu-id="ac67e-118">Nome da propriedade especificada não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="ac67e-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ac67e-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ac67e-119">0x80041008</span></span> | <span data-ttu-id="ac67e-120">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="ac67e-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="ac67e-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="ac67e-121">0x8004100c</span></span> | <span data-ttu-id="ac67e-122">A propriedade solicitada é do tipo são `CIM_OBJECT` ou `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="ac67e-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ac67e-123">0</span><span class="sxs-lookup"><span data-stu-id="ac67e-123">0</span></span> | <span data-ttu-id="ac67e-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ac67e-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ac67e-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac67e-125">Remarks</span></span>

<span data-ttu-id="ac67e-126">Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) método.</span><span class="sxs-lookup"><span data-stu-id="ac67e-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="ac67e-127">Você pode usar esse identificador para identificar as propriedades ao usar [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) métodos para ler ou gravar valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="ac67e-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="ac67e-128">Identificadores podem ser recuperados para propriedades de todos os tipos de dados diferente de `CIM_OBJECT` e `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="ac67e-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="ac67e-129">Retornou o trabalho de identificadores em todas as instâncias de uma classe.</span><span class="sxs-lookup"><span data-stu-id="ac67e-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac67e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac67e-130">Requirements</span></span>  
<span data-ttu-id="ac67e-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac67e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac67e-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ac67e-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ac67e-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ac67e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac67e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac67e-134">See also</span></span>  
[<span data-ttu-id="ac67e-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="ac67e-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
