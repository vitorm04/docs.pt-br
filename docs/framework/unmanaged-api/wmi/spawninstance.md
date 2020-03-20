---
title: Função SpawnInstance (referência de API não gerenciada)
description: A função SpawnInstance cria uma nova instância de uma classe.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176715"
---
# <a name="spawninstance-function"></a><span data-ttu-id="2a1f5-103">Função SpawnInstance</span><span class="sxs-lookup"><span data-stu-id="2a1f5-103">SpawnInstance function</span></span>
<span data-ttu-id="2a1f5-104">Cria uma nova instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2a1f5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a1f5-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="2a1f5-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a1f5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2a1f5-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2a1f5-108">[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="2a1f5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="2a1f5-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-109">[in] Reserved.</span></span> <span data-ttu-id="2a1f5-110">Este parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="2a1f5-111">[fora] Recebe o ponteiro para a nova instância da classe.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="2a1f5-112">Se ocorrer um erro, um novo objeto `ppNewInstance` não será devolvido e não será modificado.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="2a1f5-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2a1f5-113">Return value</span></span>

<span data-ttu-id="2a1f5-114">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="2a1f5-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2a1f5-115">Constante</span><span class="sxs-lookup"><span data-stu-id="2a1f5-115">Constant</span></span>  |<span data-ttu-id="2a1f5-116">Valor</span><span class="sxs-lookup"><span data-stu-id="2a1f5-116">Value</span></span>  |<span data-ttu-id="2a1f5-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a1f5-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="2a1f5-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="2a1f5-118">0x80041020</span></span> | <span data-ttu-id="2a1f5-119">`ptr`não é uma definição de classe válida e não pode gerar novas instâncias.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="2a1f5-120">Ou ele está incompleto ou não foi registrado no Windows Management ligando para [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="2a1f5-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2a1f5-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2a1f5-121">0x80041006</span></span> | <span data-ttu-id="2a1f5-122">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2a1f5-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2a1f5-123">0x80041008</span></span> | <span data-ttu-id="2a1f5-124">`ppNewClass` é `null`.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2a1f5-125">0</span><span class="sxs-lookup"><span data-stu-id="2a1f5-125">0</span></span> | <span data-ttu-id="2a1f5-126">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2a1f5-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a1f5-127">Remarks</span></span>

<span data-ttu-id="2a1f5-128">Esta função envolve uma chamada para o método [IWbemClassObject::SpawnInstance.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)</span><span class="sxs-lookup"><span data-stu-id="2a1f5-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="2a1f5-129">`ptr`deve ser uma definição de classe obtida do Windows Management.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="2a1f5-130">(Observe que a desova de uma instância de uma instância é suportada, mas a instância retornada está vazia.) Em seguida, use essa definição de classe para criar novas instâncias.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="2a1f5-131">Uma chamada para a função [PutInstanceWmi](putinstancewmi.md) é necessária se você pretende escrever a instância para o Gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="2a1f5-132">O novo objeto `ppNewClass` retornado automaticamente torna-se uma subclasse do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="2a1f5-133">Esse comportamento não pode ser anulado.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="2a1f5-134">Não há outro método pelo qual subclasses (classes derivadas) possam ser criadas.</span><span class="sxs-lookup"><span data-stu-id="2a1f5-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a1f5-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a1f5-135">Requirements</span></span>  
 <span data-ttu-id="2a1f5-136">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a1f5-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a1f5-137">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2a1f5-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2a1f5-138">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2a1f5-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1f5-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a1f5-139">See also</span></span>

- [<span data-ttu-id="2a1f5-140">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="2a1f5-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
