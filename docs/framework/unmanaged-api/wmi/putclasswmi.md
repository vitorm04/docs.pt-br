---
title: Função PutClassWmi (referência de API não gerenciada)
description: A função PutClassWmi cria uma nova classe ou atualiza uma existente.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101784"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="ef759-103">Função PutClassWmi</span><span class="sxs-lookup"><span data-stu-id="ef759-103">PutClassWmi function</span></span>

<span data-ttu-id="ef759-104">Cria uma nova classe ou atualiza uma existente.</span><span class="sxs-lookup"><span data-stu-id="ef759-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ef759-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef759-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="ef759-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef759-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="ef759-107">no Um ponteiro para uma definição de classe válida.</span><span class="sxs-lookup"><span data-stu-id="ef759-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="ef759-108">Ele deve ser inicializado corretamente com todos os valores de propriedade necessários.</span><span class="sxs-lookup"><span data-stu-id="ef759-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="ef759-109">no Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="ef759-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="ef759-110">Os valores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="ef759-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ef759-111">Constante</span><span class="sxs-lookup"><span data-stu-id="ef759-111">Constant</span></span>  |<span data-ttu-id="ef759-112">Valor</span><span class="sxs-lookup"><span data-stu-id="ef759-112">Value</span></span>  |<span data-ttu-id="ef759-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef759-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="ef759-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="ef759-114">0x20000</span></span> | <span data-ttu-id="ef759-115">Se definido, o WMI não armazena nenhum qualificador com o tipo emendado.</span><span class="sxs-lookup"><span data-stu-id="ef759-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="ef759-116">Se não estiver definido, supõe-se que esse objeto não está localizado e todos os qualificadores são armazenados com essa instância.</span><span class="sxs-lookup"><span data-stu-id="ef759-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="ef759-117">0</span><span class="sxs-lookup"><span data-stu-id="ef759-117">0</span></span> | <span data-ttu-id="ef759-118">Crie a classe se ela não existir ou substitua-a se ela já existir.</span><span class="sxs-lookup"><span data-stu-id="ef759-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="ef759-119">1</span><span class="sxs-lookup"><span data-stu-id="ef759-119">1</span></span> | <span data-ttu-id="ef759-120">Atualize a classe.</span><span class="sxs-lookup"><span data-stu-id="ef759-120">Update the class.</span></span> <span data-ttu-id="ef759-121">A classe deve existir para que a chamada seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ef759-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="ef759-122">2</span><span class="sxs-lookup"><span data-stu-id="ef759-122">2</span></span> | <span data-ttu-id="ef759-123">Crie a classe.</span><span class="sxs-lookup"><span data-stu-id="ef759-123">Create the class.</span></span> <span data-ttu-id="ef759-124">A chamada falhará se a classe já existir.</span><span class="sxs-lookup"><span data-stu-id="ef759-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="ef759-125">0x10</span><span class="sxs-lookup"><span data-stu-id="ef759-125">0x10</span></span> | <span data-ttu-id="ef759-126">O sinalizador causa uma chamada de semisynchronous.</span><span class="sxs-lookup"><span data-stu-id="ef759-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="ef759-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="ef759-127">0x10000</span></span> | <span data-ttu-id="ef759-128">Os provedores de push devem especificar esse sinalizador ao chamar `PutClassWmi` para indicar que essa classe foi alterada.</span><span class="sxs-lookup"><span data-stu-id="ef759-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="ef759-129">0</span><span class="sxs-lookup"><span data-stu-id="ef759-129">0</span></span> | <span data-ttu-id="ef759-130">Permite que uma classe seja atualizada se não houver classes derivadas e nenhuma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ef759-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="ef759-131">Ele também permitirá atualizações em todos os casos se a alteração for apenas para qualificadores não importantes, como o qualificador de descrição.</span><span class="sxs-lookup"><span data-stu-id="ef759-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="ef759-132">Se a classe tiver instâncias ou alterações para qualificadores importantes, a atualização falhará.</span><span class="sxs-lookup"><span data-stu-id="ef759-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="ef759-133">0x20</span><span class="sxs-lookup"><span data-stu-id="ef759-133">0x20</span></span> | <span data-ttu-id="ef759-134">Permite atualizações de classes, mesmo se houver classes filhas, desde que a alteração não cause conflitos com classes filhas.</span><span class="sxs-lookup"><span data-stu-id="ef759-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="ef759-135">Por exemplo, esse sinalizador permite que uma nova propriedade seja adicionada à classe base que não foi mencionada anteriormente em nenhuma das classes filhas.</span><span class="sxs-lookup"><span data-stu-id="ef759-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="ef759-136">Se a classe tiver instâncias, a atualização falhará.</span><span class="sxs-lookup"><span data-stu-id="ef759-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="ef759-137">0x40</span><span class="sxs-lookup"><span data-stu-id="ef759-137">0x40</span></span> | <span data-ttu-id="ef759-138">força atualizações de classes quando existem classes filhas conflitantes.</span><span class="sxs-lookup"><span data-stu-id="ef759-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="ef759-139">Por exemplo, esse sinalizador força uma atualização se um qualificador de classe é definido em uma classe filho e a classe base tenta adicionar o mesmo qualificador que está em conflito com o existente.</span><span class="sxs-lookup"><span data-stu-id="ef759-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="ef759-140">No modo de força, o conflito tis é resolvido com a exclusão do qualificador conflitante na classe filho.</span><span class="sxs-lookup"><span data-stu-id="ef759-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="ef759-141">no Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="ef759-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="ef759-142">Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="ef759-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="ef759-143">fora Se `null`, esse parâmetro não será usado.</span><span class="sxs-lookup"><span data-stu-id="ef759-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="ef759-144">Se `lFlags` contiver `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente com `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="ef759-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="ef759-145">O parâmetro `ppCallResult` recebe um ponteiro para um novo objeto [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .</span><span class="sxs-lookup"><span data-stu-id="ef759-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="ef759-146">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ef759-146">Return value</span></span>

<span data-ttu-id="ef759-147">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="ef759-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ef759-148">Constante</span><span class="sxs-lookup"><span data-stu-id="ef759-148">Constant</span></span>  |<span data-ttu-id="ef759-149">Valor</span><span class="sxs-lookup"><span data-stu-id="ef759-149">Value</span></span>  |<span data-ttu-id="ef759-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef759-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="ef759-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="ef759-151">0x80041003</span></span> | <span data-ttu-id="ef759-152">O usuário não tem permissão para criar ou modificar classes.</span><span class="sxs-lookup"><span data-stu-id="ef759-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="ef759-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ef759-153">0x80041001</span></span> | <span data-ttu-id="ef759-154">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="ef759-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="ef759-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="ef759-155">0x80041010</span></span> | <span data-ttu-id="ef759-156">A classe especificada é inválida.</span><span class="sxs-lookup"><span data-stu-id="ef759-156">The specified class is not valid.</span></span> <span data-ttu-id="ef759-157">Normalmente, isso indica que `pObject` especifica um objeto de instância.</span><span class="sxs-lookup"><span data-stu-id="ef759-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ef759-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ef759-158">0x80041008</span></span> | <span data-ttu-id="ef759-159">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="ef759-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="ef759-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="ef759-160">0x80041016</span></span> | <span data-ttu-id="ef759-161">O nome de classe especificado não é válido.</span><span class="sxs-lookup"><span data-stu-id="ef759-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="ef759-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="ef759-162">0x80041025</span></span> | <span data-ttu-id="ef759-163">Foi feita uma tentativa de fazer uma alteração que invalidaria uma subclasse.</span><span class="sxs-lookup"><span data-stu-id="ef759-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="ef759-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="ef759-164">0x80041019</span></span> | <span data-ttu-id="ef759-165">O sinalizador de `WBEM_FLAG_CREATE_ONLY` foi especificado, mas a classe já existe.</span><span class="sxs-lookup"><span data-stu-id="ef759-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="ef759-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ef759-166">0x80041002</span></span> | <span data-ttu-id="ef759-167">`WBEM_FLAG_UPDATE_ONLY` foi especificado em `lFlags`e a classe não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="ef759-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="ef759-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="ef759-168">0x80041020</span></span> | <span data-ttu-id="ef759-169">As propriedades obrigatórias para classes não foram definidas.</span><span class="sxs-lookup"><span data-stu-id="ef759-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ef759-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ef759-170">0x80041006</span></span> | <span data-ttu-id="ef759-171">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="ef759-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="ef759-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="ef759-172">0x80041033</span></span> | <span data-ttu-id="ef759-173">O WMI provavelmente foi interrompido e reiniciado.</span><span class="sxs-lookup"><span data-stu-id="ef759-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="ef759-174">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="ef759-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="ef759-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="ef759-175">0x80041015</span></span> | <span data-ttu-id="ef759-176">O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="ef759-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ef759-177">0</span><span class="sxs-lookup"><span data-stu-id="ef759-177">0</span></span> | <span data-ttu-id="ef759-178">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ef759-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ef759-179">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef759-179">Remarks</span></span>

<span data-ttu-id="ef759-180">Essa função encapsula uma chamada para o método [IWbemServices::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .</span><span class="sxs-lookup"><span data-stu-id="ef759-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="ef759-181">O usuário não pode criar classes com nomes que comecem ou terminem com um caractere de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="ef759-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="ef759-182">Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="ef759-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef759-183">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef759-183">Requirements</span></span>

<span data-ttu-id="ef759-184">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef759-184">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ef759-185">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ef759-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ef759-186">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ef759-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ef759-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef759-187">See also</span></span>

- [<span data-ttu-id="ef759-188">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="ef759-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
