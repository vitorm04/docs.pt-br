---
title: "Função InheritsFrom (referência de API não gerenciada)"
description: "A função InheritsFrom determina se uma classe ou instância deriva de uma classe pai específico."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: InheritsFrom
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: InheritsFrom
helpviewer_keywords: InheritsFrom function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aedeec76f4fabb2f6bd32d7d06eb5a1a5734534e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="81706-103">Função InheritsFrom</span><span class="sxs-lookup"><span data-stu-id="81706-103">InheritsFrom function</span></span>
<span data-ttu-id="81706-104">Determina se a classe ou instância atual é derivada de uma classe pai especificada.</span><span class="sxs-lookup"><span data-stu-id="81706-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="81706-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81706-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="81706-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81706-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="81706-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="81706-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="81706-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="81706-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="81706-109">[in] O nome da classe.</span><span class="sxs-lookup"><span data-stu-id="81706-109">[in] The name of the class.</span></span> <span data-ttu-id="81706-110">`wszAncestor`deve apontar para um válida `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="81706-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="81706-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="81706-111">Return value</span></span>

<span data-ttu-id="81706-112">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="81706-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="81706-113">Constante</span><span class="sxs-lookup"><span data-stu-id="81706-113">Constant</span></span>  |<span data-ttu-id="81706-114">Valor</span><span class="sxs-lookup"><span data-stu-id="81706-114">Value</span></span>  |<span data-ttu-id="81706-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="81706-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="81706-116">0</span><span class="sxs-lookup"><span data-stu-id="81706-116">0</span></span> | <span data-ttu-id="81706-117">O objeto atual herda de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="81706-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="81706-118">1</span><span class="sxs-lookup"><span data-stu-id="81706-118">1</span></span> | <span data-ttu-id="81706-119">O objeto atual não herda de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="81706-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="81706-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="81706-120">0x80041008</span></span> | <span data-ttu-id="81706-121">`wszAncestor` é `null`.</span><span class="sxs-lookup"><span data-stu-id="81706-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="81706-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="81706-122">Remarks</span></span>

<span data-ttu-id="81706-123">Essa função encapsula uma chamada para o [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="81706-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="81706-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81706-124">Requirements</span></span>  
 <span data-ttu-id="81706-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81706-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81706-126">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="81706-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="81706-127">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81706-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81706-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81706-128">See also</span></span>  
[<span data-ttu-id="81706-129">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="81706-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
