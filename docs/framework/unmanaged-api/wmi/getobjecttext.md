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
ms.openlocfilehash: d34cb399ac0e8780c442eeb2e95cebfd0a22ca02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208313"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="bf762-103">Função GetObjectText</span><span class="sxs-lookup"><span data-stu-id="bf762-103">GetObjectText function</span></span>
<span data-ttu-id="bf762-104">Retorna um processamento textual do objeto na sintaxe do formato MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="bf762-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="bf762-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf762-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="bf762-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf762-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bf762-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="bf762-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bf762-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="bf762-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="bf762-109">[in] Normalmente 0.</span><span class="sxs-lookup"><span data-stu-id="bf762-109">[in] Normally 0.</span></span> <span data-ttu-id="bf762-110">Se `WBEM_FLAG_NO_FLAVORS` (ou 0x1) for especificado, qualificadores são incluídos sem propagação ou o tipo de informações.</span><span class="sxs-lookup"><span data-stu-id="bf762-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="bf762-111">[out] Um ponteiro para um `null` na entrada.</span><span class="sxs-lookup"><span data-stu-id="bf762-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="bf762-112">No retorno, alocadas recentemente `BSTR` que contém uma renderização de sintaxe MOF do objeto.</span><span class="sxs-lookup"><span data-stu-id="bf762-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="bf762-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bf762-113">Return value</span></span>

<span data-ttu-id="bf762-114">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="bf762-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bf762-115">Constante</span><span class="sxs-lookup"><span data-stu-id="bf762-115">Constant</span></span>  |<span data-ttu-id="bf762-116">Valor</span><span class="sxs-lookup"><span data-stu-id="bf762-116">Value</span></span>  |<span data-ttu-id="bf762-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf762-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="bf762-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bf762-118">0x80041001</span></span> | <span data-ttu-id="bf762-119">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="bf762-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bf762-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bf762-120">0x80041008</span></span> | <span data-ttu-id="bf762-121">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="bf762-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bf762-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bf762-122">0x80041006</span></span> | <span data-ttu-id="bf762-123">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="bf762-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bf762-124">0</span><span class="sxs-lookup"><span data-stu-id="bf762-124">0</span></span> | <span data-ttu-id="bf762-125">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bf762-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bf762-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf762-126">Remarks</span></span>

<span data-ttu-id="bf762-127">Essa função encapsula uma chamada para o [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) método.</span><span class="sxs-lookup"><span data-stu-id="bf762-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="bf762-128">O texto MOF retornado contém todas as informações sobre o objeto, mas apenas informações suficientes para que o compilador MOF ser capaz de recriar o objeto original.</span><span class="sxs-lookup"><span data-stu-id="bf762-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="bf762-129">Por exemplo, nenhum qualificadores propagadas ou propriedades da classe pai são incluídas.</span><span class="sxs-lookup"><span data-stu-id="bf762-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="bf762-130">O seguinte algoritmo é usado para reconstruir o texto dos parâmetros de um método:</span><span class="sxs-lookup"><span data-stu-id="bf762-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="bf762-131">O colocado no parâmetros são sequência na ordem de seus valores de identificador seguintes novamente.</span><span class="sxs-lookup"><span data-stu-id="bf762-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="bf762-132">Parâmetros que são especificados como `[in]` e `[out]` são combinados em um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bf762-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
`pstrObjectText` <span data-ttu-id="bf762-133">deve ser um ponteiro para um `null` quando a função é chamada; ele não deve apontar para uma cadeia de caracteres que é válida antes da chamada de método, porque o ponteiro não será desalocado.</span><span class="sxs-lookup"><span data-stu-id="bf762-133">must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf762-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf762-134">Requirements</span></span>  
<span data-ttu-id="bf762-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf762-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf762-136">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bf762-136">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="bf762-137">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bf762-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bf762-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf762-138">See also</span></span>

- [<span data-ttu-id="bf762-139">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="bf762-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
