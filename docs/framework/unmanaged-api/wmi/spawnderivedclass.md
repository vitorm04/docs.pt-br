---
title: Função SpawnDerivedClass (referência de API não gerenciada)
description: A função SpawnDerivedClass cria um novo objeto que deriva de um objeto.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99b996cf848de968d71cc1d325d3bbda7bd5386f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715540"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="8ee29-103">Função SpawnDerivedClass</span><span class="sxs-lookup"><span data-stu-id="8ee29-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="8ee29-104">Cria um objeto de classe derivada recentemente por meio de um objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="8ee29-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8ee29-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ee29-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="8ee29-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ee29-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8ee29-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="8ee29-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8ee29-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="8ee29-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="8ee29-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="8ee29-109">[in] Reserved.</span></span> <span data-ttu-id="8ee29-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="8ee29-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="8ee29-111">[out] Recebe o ponteiro para o novo objeto de definição de classe.</span><span class="sxs-lookup"><span data-stu-id="8ee29-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="8ee29-112">Se ocorrer um erro, um novo objeto não é retornado, e `ppNewClass` é esquerda sem modificações.</span><span class="sxs-lookup"><span data-stu-id="8ee29-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="8ee29-113">Seu valor não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="8ee29-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="8ee29-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8ee29-114">Return value</span></span>

<span data-ttu-id="8ee29-115">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="8ee29-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8ee29-116">Constante</span><span class="sxs-lookup"><span data-stu-id="8ee29-116">Constant</span></span>  |<span data-ttu-id="8ee29-117">Valor</span><span class="sxs-lookup"><span data-stu-id="8ee29-117">Value</span></span>  |<span data-ttu-id="8ee29-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ee29-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="8ee29-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8ee29-119">0x80041001</span></span> | <span data-ttu-id="8ee29-120">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="8ee29-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="8ee29-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="8ee29-121">0x80041016</span></span> | <span data-ttu-id="8ee29-122">Uma operação inválida, como a geração de uma classe de uma instância, foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="8ee29-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="8ee29-123">A classe de origem não completamente foi definida ou está registrada com o gerenciamento do Windows, portanto, uma nova classe derivada não é permitida.</span><span class="sxs-lookup"><span data-stu-id="8ee29-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8ee29-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8ee29-124">0x80041006</span></span> | <span data-ttu-id="8ee29-125">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="8ee29-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8ee29-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8ee29-126">0x80041008</span></span> | <span data-ttu-id="8ee29-127">`ppNewClass` é `null`.</span><span class="sxs-lookup"><span data-stu-id="8ee29-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="8ee29-128">0</span><span class="sxs-lookup"><span data-stu-id="8ee29-128">0</span></span> | <span data-ttu-id="8ee29-129">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8ee29-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8ee29-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ee29-130">Remarks</span></span>

<span data-ttu-id="8ee29-131">Essa função encapsula uma chamada para o [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) método.</span><span class="sxs-lookup"><span data-stu-id="8ee29-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="8ee29-132">`ptr` deve ser uma definição de classe que se torna a classe pai do objeto gerado.</span><span class="sxs-lookup"><span data-stu-id="8ee29-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="8ee29-133">O objeto retornado se torna uma subclasse do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="8ee29-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="8ee29-134">O novo objeto retornado no `ppNewClass` automaticamente se torna uma subclasse do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="8ee29-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="8ee29-135">Esse comportamento não pode ser substituído.</span><span class="sxs-lookup"><span data-stu-id="8ee29-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="8ee29-136">Não há nenhum outro método pelo qual as subclasses (classes derivadas) podem ser criadas.</span><span class="sxs-lookup"><span data-stu-id="8ee29-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ee29-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ee29-137">Requirements</span></span>  
 <span data-ttu-id="8ee29-138">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee29-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee29-139">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8ee29-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8ee29-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee29-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee29-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ee29-141">See also</span></span>
- [<span data-ttu-id="8ee29-142">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="8ee29-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
