---
title: Função GetObjectText (referência de API não gerenciada)
description: A função GetObjectText retorna um processamento textual de um objeto na sintaxe MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746488"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="51b84-103">Função GetObjectText</span><span class="sxs-lookup"><span data-stu-id="51b84-103">GetObjectText function</span></span>
<span data-ttu-id="51b84-104">Retorna um processamento textual do objeto na sintaxe do formato MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="51b84-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="51b84-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51b84-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="51b84-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51b84-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="51b84-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="51b84-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="51b84-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="51b84-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="51b84-109">[in] Normalmente 0.</span><span class="sxs-lookup"><span data-stu-id="51b84-109">[in] Normally 0.</span></span> <span data-ttu-id="51b84-110">Se `WBEM_FLAG_NO_FLAVORS` (ou 0x1) for especificado, qualificadores são incluídos sem propagação ou o tipo de informações.</span><span class="sxs-lookup"><span data-stu-id="51b84-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="51b84-111">[out] Um ponteiro para um `null` na entrada.</span><span class="sxs-lookup"><span data-stu-id="51b84-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="51b84-112">No retorno, alocadas recentemente `BSTR` que contém uma renderização de sintaxe MOF do objeto.</span><span class="sxs-lookup"><span data-stu-id="51b84-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="51b84-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="51b84-113">Return value</span></span>

<span data-ttu-id="51b84-114">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="51b84-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="51b84-115">Constante</span><span class="sxs-lookup"><span data-stu-id="51b84-115">Constant</span></span>  |<span data-ttu-id="51b84-116">Valor</span><span class="sxs-lookup"><span data-stu-id="51b84-116">Value</span></span>  |<span data-ttu-id="51b84-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="51b84-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="51b84-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="51b84-118">0x80041001</span></span> | <span data-ttu-id="51b84-119">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="51b84-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="51b84-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="51b84-120">0x80041008</span></span> | <span data-ttu-id="51b84-121">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="51b84-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="51b84-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="51b84-122">0x80041006</span></span> | <span data-ttu-id="51b84-123">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="51b84-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="51b84-124">0</span><span class="sxs-lookup"><span data-stu-id="51b84-124">0</span></span> | <span data-ttu-id="51b84-125">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="51b84-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="51b84-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="51b84-126">Remarks</span></span>

<span data-ttu-id="51b84-127">Essa função encapsula uma chamada para o [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) método.</span><span class="sxs-lookup"><span data-stu-id="51b84-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="51b84-128">O texto MOF retornado contém todas as informações sobre o objeto, mas apenas informações suficientes para que o compilador MOF ser capaz de recriar o objeto original.</span><span class="sxs-lookup"><span data-stu-id="51b84-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="51b84-129">Por exemplo, nenhum qualificadores propagadas ou propriedades da classe pai são incluídas.</span><span class="sxs-lookup"><span data-stu-id="51b84-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="51b84-130">O seguinte algoritmo é usado para reconstruir o texto dos parâmetros de um método:</span><span class="sxs-lookup"><span data-stu-id="51b84-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="51b84-131">O colocado no parâmetros são sequência na ordem de seus valores de identificador seguintes novamente.</span><span class="sxs-lookup"><span data-stu-id="51b84-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="51b84-132">Parâmetros que são especificados como `[in]` e `[out]` são combinados em um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="51b84-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="51b84-133">`pstrObjectText` deve ser um ponteiro para um `null` quando a função é chamada; ele não deve apontar para uma cadeia de caracteres que é válida antes da chamada de método, porque o ponteiro não será desalocado.</span><span class="sxs-lookup"><span data-stu-id="51b84-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="51b84-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51b84-134">Requirements</span></span>  
<span data-ttu-id="51b84-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b84-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b84-136">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="51b84-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="51b84-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="51b84-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b84-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51b84-138">See also</span></span>

- [<span data-ttu-id="51b84-139">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="51b84-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
