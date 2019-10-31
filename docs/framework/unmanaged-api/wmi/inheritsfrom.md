---
title: Função InheritsFrom (referência de API não gerenciada)
description: A função InheritsFrom determina se uma classe ou instância deriva de uma classe pai específica.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6bda63377251e3a208dfb1620896535ccdf8ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127424"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="5d7df-103">Função InheritsFrom</span><span class="sxs-lookup"><span data-stu-id="5d7df-103">InheritsFrom function</span></span>
<span data-ttu-id="5d7df-104">Determina se a classe ou instância atual é derivada de uma classe pai especificada.</span><span class="sxs-lookup"><span data-stu-id="5d7df-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5d7df-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d7df-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="5d7df-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d7df-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5d7df-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="5d7df-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5d7df-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="5d7df-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="5d7df-109">no O nome da classe.</span><span class="sxs-lookup"><span data-stu-id="5d7df-109">[in] The name of the class.</span></span> <span data-ttu-id="5d7df-110">`wszAncestor` deve apontar para uma `LPCWSTR`válida.</span><span class="sxs-lookup"><span data-stu-id="5d7df-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d7df-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5d7df-111">Return value</span></span>

<span data-ttu-id="5d7df-112">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="5d7df-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5d7df-113">Constante</span><span class="sxs-lookup"><span data-stu-id="5d7df-113">Constant</span></span>  |<span data-ttu-id="5d7df-114">Valor</span><span class="sxs-lookup"><span data-stu-id="5d7df-114">Value</span></span>  |<span data-ttu-id="5d7df-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d7df-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5d7df-116">0</span><span class="sxs-lookup"><span data-stu-id="5d7df-116">0</span></span> | <span data-ttu-id="5d7df-117">O objeto atual é herdado de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="5d7df-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="5d7df-118">1</span><span class="sxs-lookup"><span data-stu-id="5d7df-118">1</span></span> | <span data-ttu-id="5d7df-119">O objeto atual não herda de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="5d7df-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5d7df-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5d7df-120">0x80041008</span></span> | <span data-ttu-id="5d7df-121">`wszAncestor` é `null`.</span><span class="sxs-lookup"><span data-stu-id="5d7df-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="5d7df-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d7df-122">Remarks</span></span>

<span data-ttu-id="5d7df-123">Essa função encapsula uma chamada para o método [IWbemClassObject:: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) .</span><span class="sxs-lookup"><span data-stu-id="5d7df-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d7df-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d7df-124">Requirements</span></span>  
 <span data-ttu-id="5d7df-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d7df-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d7df-126">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="5d7df-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5d7df-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5d7df-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7df-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d7df-128">See also</span></span>

- [<span data-ttu-id="5d7df-129">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="5d7df-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
