---
title: "Função GetMethod (referência de API não gerenciada)"
description: "A função GetMethod recupera informações sobre um método."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f22a2dfa7aae411cac960cbad2017718df8057e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getmethod-function"></a><span data-ttu-id="a18dd-103">Função GetMethod</span><span class="sxs-lookup"><span data-stu-id="a18dd-103">GetMethod function</span></span>
<span data-ttu-id="a18dd-104">Recupera informações sobre o método especificado.</span><span class="sxs-lookup"><span data-stu-id="a18dd-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a18dd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a18dd-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="a18dd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a18dd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a18dd-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="a18dd-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a18dd-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="a18dd-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="a18dd-109">[in] O nome do método.</span><span class="sxs-lookup"><span data-stu-id="a18dd-109">[in] The method name.</span></span> <span data-ttu-id="a18dd-110">Esse parâmetro não pode ser `null` e deve apontar para um válida `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="a18dd-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="a18dd-111">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="a18dd-111">[in] Reserved.</span></span> <span data-ttu-id="a18dd-112">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="a18dd-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="a18dd-113">[out] Um ponteiro para o endereço de um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) que descreve o paramteers em para o método de instância.</span><span class="sxs-lookup"><span data-stu-id="a18dd-113">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="a18dd-114">Esse parâmetro é ignorado se for definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="a18dd-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="a18dd-115">[out] Um ponteiro para o endereço de um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) que descreve os parâmetros de saída para o método de instância.</span><span class="sxs-lookup"><span data-stu-id="a18dd-115">[out] A pointer to the address of an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="a18dd-116">Esse parâmetro é ignorado se for definido como `null`.</span><span class="sxs-lookup"><span data-stu-id="a18dd-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a18dd-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a18dd-117">Return value</span></span>

<span data-ttu-id="a18dd-118">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="a18dd-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a18dd-119">Constante</span><span class="sxs-lookup"><span data-stu-id="a18dd-119">Constant</span></span>  |<span data-ttu-id="a18dd-120">Valor</span><span class="sxs-lookup"><span data-stu-id="a18dd-120">Value</span></span>  |<span data-ttu-id="a18dd-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a18dd-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a18dd-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a18dd-122">0x80041002</span></span> | <span data-ttu-id="a18dd-123">A propriedade especificada não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="a18dd-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a18dd-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a18dd-124">0x80041006</span></span> | <span data-ttu-id="a18dd-125">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="a18dd-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a18dd-126">0</span><span class="sxs-lookup"><span data-stu-id="a18dd-126">0</span></span> | <span data-ttu-id="a18dd-127">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a18dd-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a18dd-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a18dd-128">Remarks</span></span>

<span data-ttu-id="a18dd-129">Essa função encapsula uma chamada para o [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="a18dd-129">This function wraps a call to the [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a18dd-130">Gerenciamento do Windows pode definir o [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponteiro para `null` se o método não tem em parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a18dd-130">Windows Management can set the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="a18dd-131">Em `ppInSignature` e `ppOutSignature` descrevem in e out parâmetros, respectivamente, como propriedades em um `IWbemClassObject` instância da classe system [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a18dd-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx).</span></span> <span data-ttu-id="a18dd-132">As propriedades na `ppInsignature` são nomeados **Param***n*, onde  *n*  é a posição do parâmetro na assinatura de método (por exemplo, como `Param1`, `Param2`, etc.).</span><span class="sxs-lookup"><span data-stu-id="a18dd-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="a18dd-133">As propriedades na `ppOutSignature` também são chamadas de **Param***n*, e o valor de retorno é denominado **ReturnValue**.</span><span class="sxs-lookup"><span data-stu-id="a18dd-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="a18dd-134">Para obter mais informações e um exemplo, consulte [IWbemClassObject::GetMethod método](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a18dd-134">For more information and an example, see [IWbemClassObject::GetMethod method](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="a18dd-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a18dd-135">Requirements</span></span>  
<span data-ttu-id="a18dd-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a18dd-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a18dd-137">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a18dd-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a18dd-138">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a18dd-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18dd-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a18dd-139">See also</span></span>  
[<span data-ttu-id="a18dd-140">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="a18dd-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
