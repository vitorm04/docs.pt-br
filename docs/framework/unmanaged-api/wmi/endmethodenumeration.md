---
title: Função EndMethodEnumeration (referência de API não gerenciada)
description: A função EndMethodEnumeration encerra uma sequência de enumeração de método.
ms.date: 11/06/2017
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
ms.openlocfilehash: 42ee188c2a622d0bed2985e56e49997d2934686f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873296"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="152ab-103">Função EndMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="152ab-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="152ab-104">Encerra uma sequência de enumeração iniciada com uma chamada para o [função BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="152ab-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="152ab-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="152ab-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="152ab-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="152ab-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="152ab-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="152ab-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="152ab-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="152ab-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="152ab-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="152ab-109">Return value</span></span>

<span data-ttu-id="152ab-110">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="152ab-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="152ab-111">Constante</span><span class="sxs-lookup"><span data-stu-id="152ab-111">Constant</span></span>  |<span data-ttu-id="152ab-112">Valor</span><span class="sxs-lookup"><span data-stu-id="152ab-112">Value</span></span>  |<span data-ttu-id="152ab-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="152ab-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="152ab-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="152ab-114">0x8004101d</span></span> | <span data-ttu-id="152ab-115">Ocorreu um erro interno.</span><span class="sxs-lookup"><span data-stu-id="152ab-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="152ab-116">0</span><span class="sxs-lookup"><span data-stu-id="152ab-116">0</span></span> | <span data-ttu-id="152ab-117">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="152ab-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="152ab-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="152ab-118">Remarks</span></span>

<span data-ttu-id="152ab-119">Essa função encapsula uma chamada para o [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) método.</span><span class="sxs-lookup"><span data-stu-id="152ab-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="152ab-120">O chamador começa a sequência de enumeração usando [função BeginMethodEnumeration](beginmethodenumeration.md)e, em seguida, chama o [função NextMethod](nextmethod.md )até que o método retorne `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="152ab-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="152ab-121">O chamador, opcionalmente, conclui a sequência chamando `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="152ab-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="152ab-122">O chamador pode encerrar a enumeração cedo chamando `EndMethodEnumeration` a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="152ab-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="152ab-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="152ab-123">Requirements</span></span>  
 <span data-ttu-id="152ab-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="152ab-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152ab-125">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="152ab-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="152ab-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="152ab-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152ab-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="152ab-127">See also</span></span>  
[<span data-ttu-id="152ab-128">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="152ab-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
