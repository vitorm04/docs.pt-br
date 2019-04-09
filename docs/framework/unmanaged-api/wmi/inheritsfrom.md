---
title: Função InheritsFrom (referência de API não gerenciada)
description: A função InheritsFrom determina se uma classe ou instância derivada de uma classe pai específico.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d2af1b41f47a3906c0e573c104847aa3ff36cf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158425"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="8b47e-103">Função InheritsFrom</span><span class="sxs-lookup"><span data-stu-id="8b47e-103">InheritsFrom function</span></span>
<span data-ttu-id="8b47e-104">Determina se a classe ou instância atual é derivada de uma classe pai especificada.</span><span class="sxs-lookup"><span data-stu-id="8b47e-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8b47e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b47e-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="8b47e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b47e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8b47e-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="8b47e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8b47e-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="8b47e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="8b47e-109">[in] O nome da classe.</span><span class="sxs-lookup"><span data-stu-id="8b47e-109">[in] The name of the class.</span></span> `wszAncestor` <span data-ttu-id="8b47e-110">deve apontar para um válido `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="8b47e-110">must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="8b47e-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8b47e-111">Return value</span></span>

<span data-ttu-id="8b47e-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="8b47e-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8b47e-113">Constante</span><span class="sxs-lookup"><span data-stu-id="8b47e-113">Constant</span></span>  |<span data-ttu-id="8b47e-114">Valor</span><span class="sxs-lookup"><span data-stu-id="8b47e-114">Value</span></span>  |<span data-ttu-id="8b47e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b47e-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="8b47e-116">0</span><span class="sxs-lookup"><span data-stu-id="8b47e-116">0</span></span> | <span data-ttu-id="8b47e-117">O objeto atual herda `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="8b47e-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="8b47e-118">1</span><span class="sxs-lookup"><span data-stu-id="8b47e-118">1</span></span> | <span data-ttu-id="8b47e-119">O objeto atual não herda de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="8b47e-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8b47e-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8b47e-120">0x80041008</span></span> | `wszAncestor` <span data-ttu-id="8b47e-121">is `null`.</span><span class="sxs-lookup"><span data-stu-id="8b47e-121">is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="8b47e-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b47e-122">Remarks</span></span>

<span data-ttu-id="8b47e-123">Essa função encapsula uma chamada para o [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) método.</span><span class="sxs-lookup"><span data-stu-id="8b47e-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b47e-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b47e-124">Requirements</span></span>  
 <span data-ttu-id="8b47e-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b47e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b47e-126">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8b47e-126">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="8b47e-127">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8b47e-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b47e-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b47e-128">See also</span></span>

- [<span data-ttu-id="8b47e-129">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="8b47e-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
