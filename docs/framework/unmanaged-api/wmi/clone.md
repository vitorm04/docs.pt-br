---
title: Função clone (referência de API não gerenciada)
description: A função de Clone retorna um novo objeto que é um clone completo da atual.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cd87cb619ef2dc1e0548c7553585b7e51e94c4f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924769"
---
# <a name="clone-function"></a><span data-ttu-id="0214e-103">Função clone</span><span class="sxs-lookup"><span data-stu-id="0214e-103">Clone function</span></span>
<span data-ttu-id="0214e-104">Retorna um novo objeto que é um clone completo do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="0214e-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0214e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0214e-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="0214e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0214e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0214e-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="0214e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0214e-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="0214e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="0214e-109">[out] Um novo objeto que é uma completa solitário de `ptr`.</span><span class="sxs-lookup"><span data-stu-id="0214e-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="0214e-110">Esse argumento não pode ser `null` se ela recebe a cópia do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="0214e-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="0214e-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0214e-111">Return value</span></span>

<span data-ttu-id="0214e-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="0214e-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0214e-113">Constante</span><span class="sxs-lookup"><span data-stu-id="0214e-113">Constant</span></span>  |<span data-ttu-id="0214e-114">Valor</span><span class="sxs-lookup"><span data-stu-id="0214e-114">Value</span></span>  |<span data-ttu-id="0214e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0214e-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="0214e-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0214e-116">0x80041001</span></span> | <span data-ttu-id="0214e-117">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="0214e-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0214e-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0214e-118">0x80041008</span></span> | <span data-ttu-id="0214e-119">`null` foi especificado como um parâmetro, e não é permitido nesse uso.</span><span class="sxs-lookup"><span data-stu-id="0214e-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0214e-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0214e-120">0x80041006</span></span> | <span data-ttu-id="0214e-121">Não há memória suficiente está disponível para clonar o objeto.</span><span class="sxs-lookup"><span data-stu-id="0214e-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0214e-122">0</span><span class="sxs-lookup"><span data-stu-id="0214e-122">0</span></span> | <span data-ttu-id="0214e-123">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0214e-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0214e-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0214e-124">Remarks</span></span>

<span data-ttu-id="0214e-125">Essa função encapsula uma chamada para o [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) método.</span><span class="sxs-lookup"><span data-stu-id="0214e-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="0214e-126">O objeto clonado é um objeto COM que tem uma contagem de referência de 1.</span><span class="sxs-lookup"><span data-stu-id="0214e-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="0214e-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0214e-127">Requirements</span></span>  
 <span data-ttu-id="0214e-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0214e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0214e-129">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0214e-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0214e-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0214e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0214e-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0214e-131">See also</span></span>  
[<span data-ttu-id="0214e-132">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="0214e-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
