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
ms.openlocfilehash: a3c42129835f9b30bed493a0992d49d7e2a458e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798173"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="75350-103">Função WritePropertyValue</span><span class="sxs-lookup"><span data-stu-id="75350-103">WritePropertyValue function</span></span>
<span data-ttu-id="75350-104">Grava um número especificado de bytes em uma propriedade identificada por um identificador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="75350-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="75350-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75350-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="75350-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75350-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="75350-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="75350-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="75350-108">no Um ponteiro para uma instância de [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="75350-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="75350-109">no Um inteiro que contém o identificador que identifica essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="75350-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="75350-110">O identificador pode ser recuperado chamando a função [GetPropertyHandle](getpropertyhandle.md) .</span><span class="sxs-lookup"><span data-stu-id="75350-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="75350-111">no O número de bytes que estão sendo gravados na propriedade.</span><span class="sxs-lookup"><span data-stu-id="75350-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="75350-112">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="75350-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="75350-113">fora Um ponteiro para a matriz de bytes que contém os dados.</span><span class="sxs-lookup"><span data-stu-id="75350-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="75350-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="75350-114">Return value</span></span>

<span data-ttu-id="75350-115">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="75350-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="75350-116">Constante</span><span class="sxs-lookup"><span data-stu-id="75350-116">Constant</span></span>  |<span data-ttu-id="75350-117">Valor</span><span class="sxs-lookup"><span data-stu-id="75350-117">Value</span></span>  |<span data-ttu-id="75350-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="75350-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="75350-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="75350-119">0x80041008</span></span> | <span data-ttu-id="75350-120">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="75350-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="75350-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="75350-121">0x80041005</span></span> | <span data-ttu-id="75350-122">Ocorreu uma incompatibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="75350-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="75350-123">0</span><span class="sxs-lookup"><span data-stu-id="75350-123">0</span></span> | <span data-ttu-id="75350-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="75350-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="75350-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="75350-125">Remarks</span></span>

<span data-ttu-id="75350-126">Essa função encapsula uma chamada para o método [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .</span><span class="sxs-lookup"><span data-stu-id="75350-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="75350-127">Use essa função para definir a cadeia de caracteres e todos`DWORD` os outros`QWORD` dados não ou não.</span><span class="sxs-lookup"><span data-stu-id="75350-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="75350-128">Para valores de propriedade que não `lNumBytes` são de cadeia de caracteres, deve ser o tamanho de dados correto do tipo de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="75350-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="75350-129">Para valores de propriedade de `lNumBytes` cadeia de caracteres, deve ser o comprimento da cadeia de caracteres especificada em bytes, e a cadeia de caracteres deve ser de um comprimento par em bytes e ser seguida de um caractere de terminação nula.</span><span class="sxs-lookup"><span data-stu-id="75350-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="75350-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75350-130">Requirements</span></span>  
<span data-ttu-id="75350-131">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75350-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75350-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="75350-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="75350-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75350-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75350-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75350-134">See also</span></span>

- [<span data-ttu-id="75350-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="75350-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
