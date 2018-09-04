---
title: Função GetMethod (referência de API não gerenciada)
description: A função GetMethod recupera informações sobre um método.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a913de0ff20fba51295fd8282b58e3953be9bba2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554863"
---
# <a name="getmethod-function"></a><span data-ttu-id="d8bdf-103">Função GetMethod</span><span class="sxs-lookup"><span data-stu-id="d8bdf-103">GetMethod function</span></span>
<span data-ttu-id="d8bdf-104">Recupera informações sobre o método especifico.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d8bdf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8bdf-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="d8bdf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8bdf-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d8bdf-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d8bdf-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="d8bdf-109">[in] O nome do método.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-109">[in] The method name.</span></span> <span data-ttu-id="d8bdf-110">Esse parâmetro não pode ser `null` e deve apontar para um válido `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="d8bdf-111">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-111">[in] Reserved.</span></span> <span data-ttu-id="d8bdf-112">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="d8bdf-113">[out] Um ponteiro para o endereço de um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve o paramteers em para o método de instância.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="d8bdf-114">Esse parâmetro será ignorado se ele for definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="d8bdf-115">[out] Um ponteiro para o endereço de um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve os parâmetros de saída para o método de instância.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="d8bdf-116">Esse parâmetro será ignorado se ele for definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="d8bdf-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d8bdf-117">Return value</span></span>

<span data-ttu-id="d8bdf-118">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="d8bdf-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d8bdf-119">Constante</span><span class="sxs-lookup"><span data-stu-id="d8bdf-119">Constant</span></span>  |<span data-ttu-id="d8bdf-120">Valor</span><span class="sxs-lookup"><span data-stu-id="d8bdf-120">Value</span></span>  |<span data-ttu-id="d8bdf-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8bdf-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="d8bdf-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d8bdf-122">0x80041002</span></span> | <span data-ttu-id="d8bdf-123">A propriedade especificada não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d8bdf-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d8bdf-124">0x80041006</span></span> | <span data-ttu-id="d8bdf-125">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d8bdf-126">0</span><span class="sxs-lookup"><span data-stu-id="d8bdf-126">0</span></span> | <span data-ttu-id="d8bdf-127">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d8bdf-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8bdf-128">Remarks</span></span>

<span data-ttu-id="d8bdf-129">Essa função encapsula uma chamada para o [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) método.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="d8bdf-130">Gerenciamento do Windows pode definir as [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponteiro para `null` se o método não tem em parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="d8bdf-131">Na `ppInSignature` e `ppOutSignature` descrevem em parâmetros e out, respectivamente, como propriedades em um `IWbemClassObject` instância da classe system [parametry](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="d8bdf-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="d8bdf-132">As propriedades na `ppInsignature` são denominados **Param * * * n*, onde *n* é a posição do parâmetro na assinatura do método (como `Param1`, `Param2`, etc.).</span><span class="sxs-lookup"><span data-stu-id="d8bdf-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="d8bdf-133">As propriedades na `ppOutSignature` também são nomeados **Param * * * n*, e o valor de retorno é denominado **ReturnValue**.</span><span class="sxs-lookup"><span data-stu-id="d8bdf-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="d8bdf-134">Para obter mais informações e um exemplo, consulte [IWbemClassObject::GetMethod método](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="d8bdf-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="d8bdf-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8bdf-135">Requirements</span></span>  
<span data-ttu-id="d8bdf-136">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8bdf-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8bdf-137">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d8bdf-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d8bdf-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8bdf-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bdf-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8bdf-139">See also</span></span>  
[<span data-ttu-id="d8bdf-140">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="d8bdf-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
