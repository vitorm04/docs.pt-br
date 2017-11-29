---
title: "Função PutClassWmi (referência de API não gerenciada)"
description: "A função PutClassWmi cria uma nova classe ou atualiza uma existente."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dda7dc4d71b65c8b031f2dca459bd282eef1f270
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="putclasswmi-function"></a><span data-ttu-id="9e6f4-103">Função PutClassWmi</span><span class="sxs-lookup"><span data-stu-id="9e6f4-103">PutClassWmi function</span></span>
<span data-ttu-id="9e6f4-104">Cria uma nova classe ou atualiza uma existente.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-104">Creates a new class or updates an existing one.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9e6f4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e6f4-105">Syntax</span></span>  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="9e6f4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e6f4-106">Parameters</span></span>

`pObject`    
<span data-ttu-id="9e6f4-107">[in] Um ponteiro para uma definição de classe válido.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="9e6f4-108">Ele deve ser inicializado corretamente com todos os valores de propriedade necessária.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`   
<span data-ttu-id="9e6f4-109">[in] Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="9e6f4-110">Os seguintes valores são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9e6f4-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="9e6f4-111">Constante</span><span class="sxs-lookup"><span data-stu-id="9e6f4-111">Constant</span></span>  |<span data-ttu-id="9e6f4-112">Valor</span><span class="sxs-lookup"><span data-stu-id="9e6f4-112">Value</span></span>  |<span data-ttu-id="9e6f4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e6f4-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="9e6f4-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="9e6f4-114">0x20000</span></span> | <span data-ttu-id="9e6f4-115">Se o conjunto de WMI não armazena quaisquer qualificadores com o tipo aperfeiçoado.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> </br> <span data-ttu-id="9e6f4-116">Se não for definido, presume-se que esse objeto não é localizado, e todos os qualificadores são storedwith essa instância.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="9e6f4-117">0</span><span class="sxs-lookup"><span data-stu-id="9e6f4-117">0</span></span> | <span data-ttu-id="9e6f4-118">Crie a classe se ela não existir ou substituí-lo se ele já existe.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="9e6f4-119">1</span><span class="sxs-lookup"><span data-stu-id="9e6f4-119">1</span></span> | <span data-ttu-id="9e6f4-120">Atualize a classe.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-120">Update the class.</span></span> <span data-ttu-id="9e6f4-121">A classe deve existir para a chamada seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="9e6f4-122">2</span><span class="sxs-lookup"><span data-stu-id="9e6f4-122">2</span></span> | <span data-ttu-id="9e6f4-123">Crie a classe.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-123">Create the class.</span></span> <span data-ttu-id="9e6f4-124">A chamada falhará se a classe já existe.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="9e6f4-125">0x10</span><span class="sxs-lookup"><span data-stu-id="9e6f4-125">0x10</span></span> | <span data-ttu-id="9e6f4-126">O sinalizador faz com que uma chamada semi-síncrona.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="9e6f4-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="9e6f4-127">0x10000</span></span> | <span data-ttu-id="9e6f4-128">Provedores de envio devem especificar esse sinalizador ao chamar `PutClassWmi` para indicar que esta classe foi alterado.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="9e6f4-129">0</span><span class="sxs-lookup"><span data-stu-id="9e6f4-129">0</span></span> | <span data-ttu-id="9e6f4-130">Permite que uma classe a ser atualizado se não houver nenhuma classe derivada e nenhuma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="9e6f4-131">Ele também permite atualizações em todos os casos se a alteração é apenas para qualificadores importantes, como o qualificador de descrição.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="9e6f4-132">Se a classe tem instâncias ou as alterações serão qualificadores importantes, a atualização falhará.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="9e6f4-133">0x20</span><span class="sxs-lookup"><span data-stu-id="9e6f4-133">0x20</span></span> | <span data-ttu-id="9e6f4-134">Permite atualizações de classes mesmo se houver classes filhas, desde que a alteração não causar conflitos com classes filhas.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="9e6f4-135">Por exemplo, esse sinalizador permite uma nova propriedade a ser adicionada à classe base que não foi mencionado anteriormente em qualquer uma das classes filho.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="9e6f4-136">Se a classe tiver instâncias, a atualização falhará.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="9e6f4-137">0x40</span><span class="sxs-lookup"><span data-stu-id="9e6f4-137">0x40</span></span> | <span data-ttu-id="9e6f4-138">força atualizações das classes quando as classes filhas conflitantes.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="9e6f4-139">Por exemplo, esse sinalizador força uma atualização se um qualificador de classe é definido em uma classe filho, e a classe base tenta adicionar o mesmo qualificador que está em conflito com thte existente a um.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with thte existing one.</span></span> <span data-ttu-id="9e6f4-140">No modo de força, o conflito de tis é resolvido com a exclusão do qualificador conflitante na classe filha.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`  
<span data-ttu-id="9e6f4-141">[in] Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="9e6f4-142">Caso contrário, é um ponteiro para um [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instância pode ser usada pelo provedor que fornece as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-142">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="9e6f4-143">[out] Se `null`, esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="9e6f4-144">Se `lFlags` contém `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente com `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="9e6f4-145">O `ppCallResult` parâmetro recebe um ponteiro para um novo [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e6f4-146">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9e6f4-146">Return value</span></span>

<span data-ttu-id="9e6f4-147">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9e6f4-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9e6f4-148">Constante</span><span class="sxs-lookup"><span data-stu-id="9e6f4-148">Constant</span></span>  |<span data-ttu-id="9e6f4-149">Valor</span><span class="sxs-lookup"><span data-stu-id="9e6f4-149">Value</span></span>  |<span data-ttu-id="9e6f4-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e6f4-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="9e6f4-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="9e6f4-151">0x80041003</span></span> | <span data-ttu-id="9e6f4-152">O usuário não tem permissão para criar ou modificar classes.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="9e6f4-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9e6f4-153">0x80041001</span></span> | <span data-ttu-id="9e6f4-154">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="9e6f4-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="9e6f4-155">0x80041010</span></span> | <span data-ttu-id="9e6f4-156">A classe especificada é inválida.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-156">The specified class is not valid.</span></span> <span data-ttu-id="9e6f4-157">Normalmente, isso indica que `pObject` Especifica um objeto de instância.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9e6f4-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9e6f4-158">0x80041008</span></span> | <span data-ttu-id="9e6f4-159">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="9e6f4-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="9e6f4-160">0x80041016</span></span> | <span data-ttu-id="9e6f4-161">O nome da classe especificada não é válido.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="9e6f4-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="9e6f4-162">0x80041025</span></span> | <span data-ttu-id="9e6f4-163">Foi feita uma tentativa para fazer uma alteração que invalide uma subclasse.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="9e6f4-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="9e6f4-164">0x80041019</span></span> | <span data-ttu-id="9e6f4-165">O `WBEM_FLAG_CREATE_ONLY` sinalizador foi especificado, mas a classe já existe.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="9e6f4-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9e6f4-166">0x80041002</span></span> | <span data-ttu-id="9e6f4-167">`WBEM_FLAG_UPDATE_ONLY`foi especificado em `lFlags`, e a classe não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="9e6f4-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="9e6f4-168">0x80041020</span></span> | <span data-ttu-id="9e6f4-169">As propriedades necessárias para classes nem todos foi definidas.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9e6f4-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9e6f4-170">0x80041006</span></span> | <span data-ttu-id="9e6f4-171">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="9e6f4-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="9e6f4-172">0x80041033</span></span> | <span data-ttu-id="9e6f4-173">WMI foi provavelmente interrompido e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="9e6f4-174">Chamar [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="9e6f4-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="9e6f4-175">0x80041015</span></span> | <span data-ttu-id="9e6f4-176">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9e6f4-177">0</span><span class="sxs-lookup"><span data-stu-id="9e6f4-177">0</span></span> | <span data-ttu-id="9e6f4-178">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-178">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9e6f4-179">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e6f4-179">Remarks</span></span>

<span data-ttu-id="9e6f4-180">Essa função encapsula uma chamada para o [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-180">This function wraps a call to the [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="9e6f4-181">O usuário não pode criar classes com nomes que podem começam ou terminam com um sublinhado chacater</span><span class="sxs-lookup"><span data-stu-id="9e6f4-181">The user may not create classes with names that begin or end with an underscore chacater</span></span>

<span data-ttu-id="9e6f4-182">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="9e6f4-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e6f4-183">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e6f4-183">Requirements</span></span>  
 <span data-ttu-id="9e6f4-184">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e6f4-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e6f4-185">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9e6f4-185">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9e6f4-186">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9e6f4-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6f4-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e6f4-187">See also</span></span>  
[<span data-ttu-id="9e6f4-188">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="9e6f4-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
