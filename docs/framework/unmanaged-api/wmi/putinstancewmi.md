---
title: Função PutInstanceWmi (referência de API não gerenciada)
description: A função PutInstanceWmi cria ou atualiza uma instância de uma classe existente.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798379"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="6508d-103">Função PutInstanceWmi</span><span class="sxs-lookup"><span data-stu-id="6508d-103">PutInstanceWmi function</span></span>

<span data-ttu-id="6508d-104">Cria ou atualiza uma instância de uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="6508d-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="6508d-105">A instância é gravada no repositório da WMI.</span><span class="sxs-lookup"><span data-stu-id="6508d-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6508d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6508d-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="6508d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6508d-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="6508d-108">no Um ponteiro para a instância a ser gravada.</span><span class="sxs-lookup"><span data-stu-id="6508d-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="6508d-109">no Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="6508d-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="6508d-110">Os valores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="6508d-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6508d-111">Constante</span><span class="sxs-lookup"><span data-stu-id="6508d-111">Constant</span></span>  |<span data-ttu-id="6508d-112">Valor</span><span class="sxs-lookup"><span data-stu-id="6508d-112">Value</span></span>  |<span data-ttu-id="6508d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6508d-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="6508d-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="6508d-114">0x20000</span></span> | <span data-ttu-id="6508d-115">Se definido, o WMI não armazena nenhum qualificador com o tipo **emendado** .</span><span class="sxs-lookup"><span data-stu-id="6508d-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="6508d-116">Se não estiver definido, supõe-se que esse objeto não está localizado e todos os qualificadores são armazenados com essa instância.</span><span class="sxs-lookup"><span data-stu-id="6508d-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="6508d-117">0</span><span class="sxs-lookup"><span data-stu-id="6508d-117">0</span></span> | <span data-ttu-id="6508d-118">Crie a instância se ela não existir ou substitua-a se ela já existir.</span><span class="sxs-lookup"><span data-stu-id="6508d-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="6508d-119">1</span><span class="sxs-lookup"><span data-stu-id="6508d-119">1</span></span> | <span data-ttu-id="6508d-120">Atualize a instância.</span><span class="sxs-lookup"><span data-stu-id="6508d-120">Update the instance.</span></span> <span data-ttu-id="6508d-121">A instância deve existir para que a chamada seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="6508d-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="6508d-122">2</span><span class="sxs-lookup"><span data-stu-id="6508d-122">2</span></span> | <span data-ttu-id="6508d-123">Crie a instância.</span><span class="sxs-lookup"><span data-stu-id="6508d-123">Create the instance.</span></span> <span data-ttu-id="6508d-124">A chamada falhará se a instância já existir.</span><span class="sxs-lookup"><span data-stu-id="6508d-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="6508d-125">0x10</span><span class="sxs-lookup"><span data-stu-id="6508d-125">0x10</span></span> | <span data-ttu-id="6508d-126">O sinalizador causa uma chamada de semisynchronous.</span><span class="sxs-lookup"><span data-stu-id="6508d-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="6508d-127">no Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="6508d-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="6508d-128">Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="6508d-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="6508d-129">fora Se `null`, esse parâmetro não será usado.</span><span class="sxs-lookup"><span data-stu-id="6508d-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="6508d-130">Se `lFlags` contiver `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente `WBEM_S_NO_ERROR`com.</span><span class="sxs-lookup"><span data-stu-id="6508d-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="6508d-131">O `ppCallResult` parâmetro recebe um ponteiro para um novo objeto [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .</span><span class="sxs-lookup"><span data-stu-id="6508d-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="6508d-132">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6508d-132">Return value</span></span>

<span data-ttu-id="6508d-133">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="6508d-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6508d-134">Constante</span><span class="sxs-lookup"><span data-stu-id="6508d-134">Constant</span></span>  |<span data-ttu-id="6508d-135">Valor</span><span class="sxs-lookup"><span data-stu-id="6508d-135">Value</span></span>  |<span data-ttu-id="6508d-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="6508d-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="6508d-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="6508d-137">0x80041003</span></span> | <span data-ttu-id="6508d-138">O usuário não tem permissão para atualizar uma instância da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="6508d-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="6508d-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6508d-139">0x80041001</span></span> | <span data-ttu-id="6508d-140">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="6508d-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="6508d-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="6508d-141">0x80041010</span></span> | <span data-ttu-id="6508d-142">A classe que dá suporte a esta instância não é válida.</span><span class="sxs-lookup"><span data-stu-id="6508d-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="6508d-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="6508d-143">0x80041028</span></span> | <span data-ttu-id="6508d-144">um `null` foi especificado para uma propriedade que não pode `null`ser, como uma que está marcada por um qualificador **indexado** ou **NOT_NULL** .</span><span class="sxs-lookup"><span data-stu-id="6508d-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="6508d-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="6508d-145">0x8004100f</span></span> | <span data-ttu-id="6508d-146">A instância especificada é inválida.</span><span class="sxs-lookup"><span data-stu-id="6508d-146">The specified instance is not valid.</span></span> <span data-ttu-id="6508d-147">(Por exemplo, chamar `PutInstanceWmi` com uma classe retorna esse valor.)</span><span class="sxs-lookup"><span data-stu-id="6508d-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6508d-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6508d-148">0x80041008</span></span> | <span data-ttu-id="6508d-149">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="6508d-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="6508d-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="6508d-150">0x80041019</span></span> | <span data-ttu-id="6508d-151">O `WBEM_FLAG_CREATE_ONLY` sinalizador foi especificado, mas a instância já existe.</span><span class="sxs-lookup"><span data-stu-id="6508d-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="6508d-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6508d-152">0x80041002</span></span> | <span data-ttu-id="6508d-153">`WBEM_FLAG_UPDATE_ONLY`foi especificado em `lFlags`, mas a instância não existe.</span><span class="sxs-lookup"><span data-stu-id="6508d-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6508d-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6508d-154">0x80041006</span></span> | <span data-ttu-id="6508d-155">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="6508d-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="6508d-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="6508d-156">0x80041033</span></span> | <span data-ttu-id="6508d-157">O WMI provavelmente foi interrompido e reiniciado.</span><span class="sxs-lookup"><span data-stu-id="6508d-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="6508d-158">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="6508d-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="6508d-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="6508d-159">0x80041015</span></span> | <span data-ttu-id="6508d-160">O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="6508d-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6508d-161">0</span><span class="sxs-lookup"><span data-stu-id="6508d-161">0</span></span> | <span data-ttu-id="6508d-162">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="6508d-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6508d-163">Comentários</span><span class="sxs-lookup"><span data-stu-id="6508d-163">Remarks</span></span>

<span data-ttu-id="6508d-164">Essa função encapsula uma chamada para o método [IWbemServices::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .</span><span class="sxs-lookup"><span data-stu-id="6508d-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="6508d-165">A `PutInstanceWmi` função dá suporte à criação de instâncias e à atualização de instâncias somente de classes existentes.</span><span class="sxs-lookup"><span data-stu-id="6508d-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="6508d-166">Dependendo de como o `pCtx` parâmetro é definido, algumas ou todas as propriedades da instância serão atualizadas.</span><span class="sxs-lookup"><span data-stu-id="6508d-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="6508d-167">Quando a instância apontada `pInst` pertence a uma subclasse, o gerenciamento do Windows chama todos os provedores responsáveis pelas classes das quais a subclasse deriva.</span><span class="sxs-lookup"><span data-stu-id="6508d-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="6508d-168">Todos esses provedores devem ter sucesso para que a `PutInstanceWmi` solicitação original seja realizada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="6508d-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="6508d-169">O provedor que dá suporte à classe mais alta na hierarquia é chamado primeiro.</span><span class="sxs-lookup"><span data-stu-id="6508d-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="6508d-170">A ordem de chamada continua com a subclasse da classe superior e prossegue de cima para baixo até que o gerenciamento do Windows atinja o provedor para a classe proprietária da instância apontada `pInst`pelo.</span><span class="sxs-lookup"><span data-stu-id="6508d-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="6508d-171">O gerenciamento do Windows não chama os provedores para nenhuma das classes filhas de uma instância.</span><span class="sxs-lookup"><span data-stu-id="6508d-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="6508d-172">Quando um aplicativo deve atualizar uma instância que pertence a uma hierarquia de classe, `pInst` o parâmetro deve apontar para a instância que contém as propriedades a serem modificadas.</span><span class="sxs-lookup"><span data-stu-id="6508d-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="6508d-173">Ou seja, considere uma instância de destino que pertença a **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="6508d-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="6508d-174">A instância **ClassB** deriva de **ClasseA**, e a **ClasseA** define a propriedade **Propa**.</span><span class="sxs-lookup"><span data-stu-id="6508d-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="6508d-175">Se um aplicativo quiser fazer uma alteração no valor de **Propa** na instância de **ClassB** , ele deverá definir `pInst` essa instância em vez de uma instância de **ClassA**.</span><span class="sxs-lookup"><span data-stu-id="6508d-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="6508d-176">Não `PutInstanceWmi` é permitido chamar em uma instância de uma classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="6508d-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="6508d-177">Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="6508d-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="6508d-178">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6508d-178">Requirements</span></span>

<span data-ttu-id="6508d-179">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6508d-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6508d-180">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6508d-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6508d-181">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6508d-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6508d-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6508d-182">See also</span></span>

- [<span data-ttu-id="6508d-183">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="6508d-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
