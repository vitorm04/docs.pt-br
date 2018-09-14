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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb187719ff502abe61ac5deb69c6427a4a64ab44
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609901"
---
# <a name="spawninstance-function"></a><span data-ttu-id="23583-103">Função SpawnInstance</span><span class="sxs-lookup"><span data-stu-id="23583-103">SpawnInstance function</span></span>
<span data-ttu-id="23583-104">Cria uma nova instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="23583-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="23583-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23583-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="23583-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23583-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="23583-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="23583-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="23583-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="23583-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="23583-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="23583-109">[in] Reserved.</span></span> <span data-ttu-id="23583-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="23583-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="23583-111">[out] Recebe o ponteiro para a nova instância da classe.</span><span class="sxs-lookup"><span data-stu-id="23583-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="23583-112">Se ocorrer um erro, um novo objeto não é retornado, e `ppNewInstance` é esquerda sem modificações.</span><span class="sxs-lookup"><span data-stu-id="23583-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="23583-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="23583-113">Return value</span></span>

<span data-ttu-id="23583-114">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="23583-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="23583-115">Constante</span><span class="sxs-lookup"><span data-stu-id="23583-115">Constant</span></span>  |<span data-ttu-id="23583-116">Valor</span><span class="sxs-lookup"><span data-stu-id="23583-116">Value</span></span>  |<span data-ttu-id="23583-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="23583-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="23583-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="23583-118">0x80041020</span></span> | <span data-ttu-id="23583-119">`ptr` não é uma definição de classe válido e não é possível gerar novas instâncias.</span><span class="sxs-lookup"><span data-stu-id="23583-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="23583-120">O está incompleto ou não foi registrado com o gerenciamento do Windows, chamando [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="23583-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="23583-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="23583-121">0x80041006</span></span> | <span data-ttu-id="23583-122">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="23583-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="23583-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="23583-123">0x80041008</span></span> | <span data-ttu-id="23583-124">`ppNewClass` é `null`.</span><span class="sxs-lookup"><span data-stu-id="23583-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="23583-125">0</span><span class="sxs-lookup"><span data-stu-id="23583-125">0</span></span> | <span data-ttu-id="23583-126">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="23583-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="23583-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="23583-127">Remarks</span></span>

<span data-ttu-id="23583-128">Essa função encapsula uma chamada para o [IWbemclassObject:: SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) método.</span><span class="sxs-lookup"><span data-stu-id="23583-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="23583-129">`ptr` deve ser uma definição de classe obtida de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="23583-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="23583-130">(Observe que ao gerar uma instância de uma instância é suportado, mas a instância retornada estiver vazia.) Você, em seguida, usar essa definição de classe para criar novas instâncias.</span><span class="sxs-lookup"><span data-stu-id="23583-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="23583-131">Uma chamada para o [PutInstanceWmi](putinstancewmi.md) função é necessária se você pretende gravar a instância de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="23583-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>




<span data-ttu-id="23583-132">O novo objeto retornado no `ppNewClass` automaticamente se torna uma subclasse do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="23583-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="23583-133">Esse comportamento não pode ser substituído.</span><span class="sxs-lookup"><span data-stu-id="23583-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="23583-134">Não há nenhum outro método pelo qual as subclasses (classes derivadas) podem ser criadas.</span><span class="sxs-lookup"><span data-stu-id="23583-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="23583-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23583-135">Requirements</span></span>  
 <span data-ttu-id="23583-136">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23583-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23583-137">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="23583-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="23583-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="23583-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23583-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23583-139">See also</span></span>  
[<span data-ttu-id="23583-140">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="23583-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
