---
title: Função WritePropertyValue (referência de API não gerenciada)
description: A função WritePropertyValue grava bytes em uma propriedade.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a98103367f497b18f9b8fbd61a37abf9816b8356
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107933"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="b5a62-103">Função WritePropertyValue</span><span class="sxs-lookup"><span data-stu-id="b5a62-103">WritePropertyValue function</span></span>
<span data-ttu-id="b5a62-104">Grava um número especificado de bytes em uma propriedade identificada por um identificador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b5a62-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b5a62-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5a62-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="b5a62-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5a62-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b5a62-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="b5a62-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b5a62-108">[in] Um ponteiro para um [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instância.</span><span class="sxs-lookup"><span data-stu-id="b5a62-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="b5a62-109">[in] Um inteiro que contém o identificador que identifica esta propriedade.</span><span class="sxs-lookup"><span data-stu-id="b5a62-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="b5a62-110">O identificador pode ser recuperado chamando o [GetPropertyHandle](getpropertyhandle.md) função.</span><span class="sxs-lookup"><span data-stu-id="b5a62-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="b5a62-111">[in] O número de bytes que está sendo gravado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="b5a62-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="b5a62-112">Consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b5a62-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="b5a62-113">[out] Um ponteiro para a matriz de bytes que contém os dados.</span><span class="sxs-lookup"><span data-stu-id="b5a62-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="b5a62-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b5a62-114">Return value</span></span>

<span data-ttu-id="b5a62-115">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="b5a62-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b5a62-116">Constante</span><span class="sxs-lookup"><span data-stu-id="b5a62-116">Constant</span></span>  |<span data-ttu-id="b5a62-117">Valor</span><span class="sxs-lookup"><span data-stu-id="b5a62-117">Value</span></span>  |<span data-ttu-id="b5a62-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5a62-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b5a62-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b5a62-119">0x80041008</span></span> | <span data-ttu-id="b5a62-120">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="b5a62-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="b5a62-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="b5a62-121">0x80041005</span></span> | <span data-ttu-id="b5a62-122">Ocorreu uma incompatibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="b5a62-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b5a62-123">0</span><span class="sxs-lookup"><span data-stu-id="b5a62-123">0</span></span> | <span data-ttu-id="b5a62-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b5a62-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b5a62-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5a62-125">Remarks</span></span>

<span data-ttu-id="b5a62-126">Essa função encapsula uma chamada para o [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) método.</span><span class="sxs-lookup"><span data-stu-id="b5a62-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="b5a62-127">Use essa função para definir a cadeia de caracteres e todos os outros não -`DWORD` ou não-`QWORD` dados.</span><span class="sxs-lookup"><span data-stu-id="b5a62-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="b5a62-128">Para valores de propriedade não cadeia de caracteres, `lNumBytes` deve ser o tamanho dos dados corretos do tipo de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="b5a62-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="b5a62-129">Para valores de propriedade de cadeia de caracteres, `lNumBytes` deve ser o comprimento da cadeia de caracteres especificada em bytes e a cadeia de caracteres em si deve ser de um mesmo comprimento em bytes e ser seguida por um caractere nulo de terminação.</span><span class="sxs-lookup"><span data-stu-id="b5a62-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5a62-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5a62-130">Requirements</span></span>  
<span data-ttu-id="b5a62-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5a62-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a62-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b5a62-132">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="b5a62-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b5a62-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5a62-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5a62-134">See also</span></span>

- [<span data-ttu-id="b5a62-135">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b5a62-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
