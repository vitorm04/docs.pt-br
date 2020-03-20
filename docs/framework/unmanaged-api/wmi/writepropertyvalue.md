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
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174830"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="3d637-103">Função WritePropertyValue</span><span class="sxs-lookup"><span data-stu-id="3d637-103">WritePropertyValue function</span></span>
<span data-ttu-id="3d637-104">Grava um número especificado de bytes em uma propriedade identificada por um identificador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3d637-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3d637-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d637-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="3d637-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d637-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3d637-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="3d637-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3d637-108">[em] Um ponteiro para uma instância [IWbemObjectAccess.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)</span><span class="sxs-lookup"><span data-stu-id="3d637-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="3d637-109">[em] Um inteiro que contém a alça que identifica esta propriedade.</span><span class="sxs-lookup"><span data-stu-id="3d637-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="3d637-110">A alça pode ser recuperada chamando a função [GetPropertyHandle.](getpropertyhandle.md)</span><span class="sxs-lookup"><span data-stu-id="3d637-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="3d637-111">[em] O número de bytes sendo escritos para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="3d637-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="3d637-112">Consulte a seção [Observações](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3d637-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="3d637-113">`pHandle`[fora] Um ponteiro para a matriz de bytes que contém os dados.</span><span class="sxs-lookup"><span data-stu-id="3d637-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="3d637-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3d637-114">Return value</span></span>

<span data-ttu-id="3d637-115">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="3d637-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3d637-116">Constante</span><span class="sxs-lookup"><span data-stu-id="3d637-116">Constant</span></span>  |<span data-ttu-id="3d637-117">Valor</span><span class="sxs-lookup"><span data-stu-id="3d637-117">Value</span></span>  |<span data-ttu-id="3d637-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d637-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3d637-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3d637-119">0x80041008</span></span> | <span data-ttu-id="3d637-120">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="3d637-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="3d637-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="3d637-121">0x80041005</span></span> | <span data-ttu-id="3d637-122">Ocorreu uma incompatibilidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="3d637-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3d637-123">0</span><span class="sxs-lookup"><span data-stu-id="3d637-123">0</span></span> | <span data-ttu-id="3d637-124">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="3d637-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3d637-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d637-125">Remarks</span></span>

<span data-ttu-id="3d637-126">Esta função envolve uma chamada para o método [IWbemClassObject::WritePropertyValue.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)</span><span class="sxs-lookup"><span data-stu-id="3d637-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="3d637-127">Use esta função para definir string`DWORD` e`QWORD` todos os outros dados não ou não.</span><span class="sxs-lookup"><span data-stu-id="3d637-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="3d637-128">Para valores de `lNumBytes` propriedade não string, deve ser o tamanho correto dos dados do tipo de propriedade especificado.</span><span class="sxs-lookup"><span data-stu-id="3d637-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="3d637-129">Para valores `lNumBytes` de propriedade de seqüência, deve ser o comprimento da seqüência especificada em bytes, e a seqüência em si deve ser de um comprimento uniforme em bytes e ser seguida com um caractere de rescisão nula.</span><span class="sxs-lookup"><span data-stu-id="3d637-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d637-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d637-130">Requirements</span></span>  
<span data-ttu-id="3d637-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d637-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d637-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3d637-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3d637-133">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3d637-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d637-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="3d637-134">See also</span></span>

- [<span data-ttu-id="3d637-135">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="3d637-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
