---
title: "Função GetMethodQualifierSet (referência de API não gerenciada)"
description: "A função GetMethodQualifierSet recupera o conjunto do qualificador do método."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79a19d3bb40dd4d435bd7cf97eb0b4071020648e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="e84b9-103">Função GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="e84b9-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="e84b9-104">Recupera o qualificador definido para um método específico.</span><span class="sxs-lookup"><span data-stu-id="e84b9-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e84b9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e84b9-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="e84b9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e84b9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e84b9-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="e84b9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e84b9-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="e84b9-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="e84b9-109">[in] O nome do método.</span><span class="sxs-lookup"><span data-stu-id="e84b9-109">[in] The method  name.</span></span> <span data-ttu-id="e84b9-110">`wszMethod`deve apontar para um válida `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="e84b9-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="e84b9-111">[out] Recebe o ponteiro de interface que permite acessar os qualificadores do método.</span><span class="sxs-lookup"><span data-stu-id="e84b9-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="e84b9-112">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="e84b9-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="e84b9-113">Se ocorrer um erro, um novo objeto não é retornado e o ponteiro é definido para apontar para `null`.</span><span class="sxs-lookup"><span data-stu-id="e84b9-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e84b9-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e84b9-114">Return value</span></span>

<span data-ttu-id="e84b9-115">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="e84b9-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e84b9-116">Constante</span><span class="sxs-lookup"><span data-stu-id="e84b9-116">Constant</span></span>  |<span data-ttu-id="e84b9-117">Valor</span><span class="sxs-lookup"><span data-stu-id="e84b9-117">Value</span></span>  |<span data-ttu-id="e84b9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e84b9-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e84b9-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e84b9-119">0x80041002</span></span> | <span data-ttu-id="e84b9-120">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="e84b9-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e84b9-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e84b9-121">0x80041008</span></span> | <span data-ttu-id="e84b9-122">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="e84b9-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e84b9-123">0</span><span class="sxs-lookup"><span data-stu-id="e84b9-123">0</span></span> | <span data-ttu-id="e84b9-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e84b9-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e84b9-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="e84b9-125">Remarks</span></span>

<span data-ttu-id="e84b9-126">Essa função encapsula uma chamada para o [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="e84b9-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="e84b9-127">Uma chamada para essa função tem suporte apenas se o objeto atual é uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="e84b9-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="e84b9-128">Manipulação de método não está disponível para [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="e84b9-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="e84b9-129">Como cada método pode ter seus próprio qualificadores de [IWbemQualifierSet ponteiro](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permite que o chamador adicionar, editar ou excluir esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="e84b9-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="e84b9-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e84b9-130">Requirements</span></span>  
<span data-ttu-id="e84b9-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e84b9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e84b9-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e84b9-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e84b9-133">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e84b9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e84b9-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e84b9-134">See also</span></span>  
[<span data-ttu-id="e84b9-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="e84b9-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
