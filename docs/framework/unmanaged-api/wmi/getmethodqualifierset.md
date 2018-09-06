---
title: Função GetMethodQualifierSet (referência de API não gerenciada)
description: A função GetMethodQualifierSet recupera o conjunto de qualificador de um método.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a363591f5db7a2dbcba1147df35d8c023c9b0707
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724715"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="f571f-103">Função GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="f571f-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="f571f-104">Recupera o qualificador definido para um método específico.</span><span class="sxs-lookup"><span data-stu-id="f571f-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f571f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f571f-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="f571f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f571f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f571f-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="f571f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f571f-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="f571f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`  
<span data-ttu-id="f571f-109">[in] O nome do método.</span><span class="sxs-lookup"><span data-stu-id="f571f-109">[in] The method  name.</span></span> <span data-ttu-id="f571f-110">`wszMethod` deve apontar para um válido `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="f571f-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="f571f-111">[out] Recebe o ponteiro de interface que permite o acesso para os qualificadores do método.</span><span class="sxs-lookup"><span data-stu-id="f571f-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="f571f-112">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f571f-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="f571f-113">Se ocorrer um erro, um novo objeto não é retornado e o ponteiro é definido para apontar para `null`.</span><span class="sxs-lookup"><span data-stu-id="f571f-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f571f-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f571f-114">Return value</span></span>

<span data-ttu-id="f571f-115">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="f571f-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f571f-116">Constante</span><span class="sxs-lookup"><span data-stu-id="f571f-116">Constant</span></span>  |<span data-ttu-id="f571f-117">Valor</span><span class="sxs-lookup"><span data-stu-id="f571f-117">Value</span></span>  |<span data-ttu-id="f571f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f571f-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="f571f-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f571f-119">0x80041002</span></span> | <span data-ttu-id="f571f-120">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="f571f-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f571f-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f571f-121">0x80041008</span></span> | <span data-ttu-id="f571f-122">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="f571f-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f571f-123">0</span><span class="sxs-lookup"><span data-stu-id="f571f-123">0</span></span> | <span data-ttu-id="f571f-124">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f571f-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f571f-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="f571f-125">Remarks</span></span>

<span data-ttu-id="f571f-126">Essa função encapsula uma chamada para o [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) método.</span><span class="sxs-lookup"><span data-stu-id="f571f-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span> 

<span data-ttu-id="f571f-127">Uma chamada para essa função tem suporte apenas se o objeto atual é uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="f571f-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="f571f-128">Manipulação de método não está disponível para [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="f571f-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters that point to CIM instances.</span></span>

<span data-ttu-id="f571f-129">Porque cada método pode ter seus próprio qualificadores, o [IWbemQualifierSet ponteiro](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permite que o chamador adicionar, editar ou excluir esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="f571f-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="f571f-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f571f-130">Requirements</span></span>  
<span data-ttu-id="f571f-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f571f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f571f-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f571f-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f571f-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f571f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f571f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f571f-134">See also</span></span>  
[<span data-ttu-id="f571f-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="f571f-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
