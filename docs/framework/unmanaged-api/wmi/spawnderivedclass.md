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
ms.openlocfilehash: c213f311f1af1e56d0ce24eba3b76f33be541323
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798234"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="26137-103">Função SpawnDerivedClass</span><span class="sxs-lookup"><span data-stu-id="26137-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="26137-104">Cria um objeto de classe derivada recentemente por meio de um objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="26137-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="26137-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26137-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="26137-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26137-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="26137-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="26137-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="26137-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="26137-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="26137-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="26137-109">[in] Reserved.</span></span> <span data-ttu-id="26137-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="26137-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="26137-111">fora Recebe o ponteiro para o novo objeto de definição de classe.</span><span class="sxs-lookup"><span data-stu-id="26137-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="26137-112">Se ocorrer um erro, um novo objeto não será retornado e `ppNewClass` permanecerá não modificado.</span><span class="sxs-lookup"><span data-stu-id="26137-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="26137-113">Seu valor não pode `null`ser.</span><span class="sxs-lookup"><span data-stu-id="26137-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="26137-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="26137-114">Return value</span></span>

<span data-ttu-id="26137-115">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="26137-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="26137-116">Constante</span><span class="sxs-lookup"><span data-stu-id="26137-116">Constant</span></span>  |<span data-ttu-id="26137-117">Valor</span><span class="sxs-lookup"><span data-stu-id="26137-117">Value</span></span>  |<span data-ttu-id="26137-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="26137-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="26137-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="26137-119">0x80041001</span></span> | <span data-ttu-id="26137-120">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="26137-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="26137-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="26137-121">0x80041016</span></span> | <span data-ttu-id="26137-122">Uma operação inválida, como a geração de uma classe de uma instância, foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="26137-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="26137-123">A classe de origem não foi totalmente definida ou registrada com o gerenciamento do Windows, portanto, não é permitida uma nova classe derivada.</span><span class="sxs-lookup"><span data-stu-id="26137-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="26137-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="26137-124">0x80041006</span></span> | <span data-ttu-id="26137-125">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="26137-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="26137-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="26137-126">0x80041008</span></span> | <span data-ttu-id="26137-127">`ppNewClass` é `null`.</span><span class="sxs-lookup"><span data-stu-id="26137-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="26137-128">0</span><span class="sxs-lookup"><span data-stu-id="26137-128">0</span></span> | <span data-ttu-id="26137-129">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="26137-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="26137-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="26137-130">Remarks</span></span>

<span data-ttu-id="26137-131">Essa função encapsula uma chamada para o método [IWbemClassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="26137-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="26137-132">`ptr`deve ser uma definição de classe que se torna a classe pai do objeto gerado.</span><span class="sxs-lookup"><span data-stu-id="26137-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="26137-133">O objeto retornado se torna uma subclasse do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="26137-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="26137-134">O novo objeto retornado em `ppNewClass` torna-se automaticamente uma subclasse do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="26137-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="26137-135">Esse comportamento não pode ser substituído.</span><span class="sxs-lookup"><span data-stu-id="26137-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="26137-136">Não há nenhum outro método pelo qual as subclasses (classes derivadas) podem ser criadas.</span><span class="sxs-lookup"><span data-stu-id="26137-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="26137-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26137-137">Requirements</span></span>  
 <span data-ttu-id="26137-138">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26137-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26137-139">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="26137-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="26137-140">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26137-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26137-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26137-141">See also</span></span>

- [<span data-ttu-id="26137-142">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="26137-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
