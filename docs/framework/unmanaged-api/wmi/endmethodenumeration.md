---
title: "Função EndMethodEnumeration (referência de API não gerenciada)"
description: "A função EndMethodEnumeration encerra uma sequência de enumeração de método."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1379adbce449ac3255c359249b0296da96a659a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="8a1c4-103">Função EndMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="8a1c4-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="8a1c4-104">Encerra uma sequência de enumeração iniciada com uma chamada para o [BeginMethodEnumeration função](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8a1c4-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8a1c4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a1c4-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="8a1c4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a1c4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8a1c4-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8a1c4-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a1c4-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8a1c4-109">Return value</span></span>

<span data-ttu-id="8a1c4-110">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="8a1c4-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8a1c4-111">Constante</span><span class="sxs-lookup"><span data-stu-id="8a1c4-111">Constant</span></span>  |<span data-ttu-id="8a1c4-112">Valor</span><span class="sxs-lookup"><span data-stu-id="8a1c4-112">Value</span></span>  |<span data-ttu-id="8a1c4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a1c4-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="8a1c4-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="8a1c4-114">0x8004101d</span></span> | <span data-ttu-id="8a1c4-115">Ocorreu um erro interno.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8a1c4-116">0</span><span class="sxs-lookup"><span data-stu-id="8a1c4-116">0</span></span> | <span data-ttu-id="8a1c4-117">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8a1c4-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a1c4-118">Remarks</span></span>

<span data-ttu-id="8a1c4-119">Essa função encapsula uma chamada para o [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="8a1c4-120">O chamador começa a sequência de enumeração usando [BeginMethodEnumeration função](beginmethodenumeration.md)e, em seguida, chama o [NextMethod função](nextmethod.md )até que o método retornará `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="8a1c4-121">O chamador opcionalmente conclui a sequência chamando `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="8a1c4-122">O chamador pode encerrar a enumeração antecipada chamando `EndMethodEnumeration` a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="8a1c4-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a1c4-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a1c4-123">Requirements</span></span>  
 <span data-ttu-id="8a1c4-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a1c4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a1c4-125">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8a1c4-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8a1c4-126">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8a1c4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1c4-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a1c4-127">See also</span></span>  
[<span data-ttu-id="8a1c4-128">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="8a1c4-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
