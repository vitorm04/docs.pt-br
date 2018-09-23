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
ms.openlocfilehash: 67abf017040b9e6bbe9b10e560c8d57c124ae84e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705673"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="9d6b9-103">Função PutInstanceWmi</span><span class="sxs-lookup"><span data-stu-id="9d6b9-103">PutInstanceWmi function</span></span>
<span data-ttu-id="9d6b9-104">Cria ou atualiza uma instância de uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="9d6b9-105">A instância é gravada no repositório da WMI.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9d6b9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d6b9-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="9d6b9-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d6b9-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="9d6b9-108">[in] Um ponteiro para a instância a ser gravado.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="9d6b9-109">[in] Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="9d6b9-110">Os seguintes valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9d6b9-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="9d6b9-111">Constante</span><span class="sxs-lookup"><span data-stu-id="9d6b9-111">Constant</span></span>  |<span data-ttu-id="9d6b9-112">Valor</span><span class="sxs-lookup"><span data-stu-id="9d6b9-112">Value</span></span>  |<span data-ttu-id="9d6b9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d6b9-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="9d6b9-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="9d6b9-114">0x20000</span></span> | <span data-ttu-id="9d6b9-115">Se definido, WMI não armazena qualquer qualificador com a **Amended** sabor.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="9d6b9-116">Se não for definido, supõe-se que esse objeto não está localizado, e todos os qualificadores são storedwith dessa instância.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="9d6b9-117">0</span><span class="sxs-lookup"><span data-stu-id="9d6b9-117">0</span></span> | <span data-ttu-id="9d6b9-118">Se ele não existir ou substituí-lo se ele já existir, crie a instância.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="9d6b9-119">1</span><span class="sxs-lookup"><span data-stu-id="9d6b9-119">1</span></span> | <span data-ttu-id="9d6b9-120">Atualize a instância.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-120">Update the instance.</span></span> <span data-ttu-id="9d6b9-121">A instância deve existir para a chamada seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="9d6b9-122">2</span><span class="sxs-lookup"><span data-stu-id="9d6b9-122">2</span></span> | <span data-ttu-id="9d6b9-123">Crie a instância.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-123">Create the instance.</span></span> <span data-ttu-id="9d6b9-124">A chamada falhará se a instância já existe.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="9d6b9-125">0x10</span><span class="sxs-lookup"><span data-stu-id="9d6b9-125">0x10</span></span> | <span data-ttu-id="9d6b9-126">O sinalizador faz com que uma chamada semissíncrona.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="9d6b9-127">[in] Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="9d6b9-128">Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="9d6b9-129">[out] Se `null`, esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="9d6b9-130">Se `lFlags` contém `WBEM_FLAG_RETURN_IMMEDIATELY`, a função retornará imediatamente com `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="9d6b9-131">O `ppCallResult` parâmetro recebe um ponteiro para um novo [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) objeto.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d6b9-132">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9d6b9-132">Return value</span></span>

<span data-ttu-id="9d6b9-133">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9d6b9-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9d6b9-134">Constante</span><span class="sxs-lookup"><span data-stu-id="9d6b9-134">Constant</span></span>  |<span data-ttu-id="9d6b9-135">Valor</span><span class="sxs-lookup"><span data-stu-id="9d6b9-135">Value</span></span>  |<span data-ttu-id="9d6b9-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d6b9-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="9d6b9-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="9d6b9-137">0x80041003</span></span> | <span data-ttu-id="9d6b9-138">O usuário não tem permissão para atualizar uma instância da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="9d6b9-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9d6b9-139">0x80041001</span></span> | <span data-ttu-id="9d6b9-140">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="9d6b9-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="9d6b9-141">0x80041010</span></span> | <span data-ttu-id="9d6b9-142">A classe que dão suporte a essa instância não é válida.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="9d6b9-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="9d6b9-143">0x80041028</span></span> | <span data-ttu-id="9d6b9-144">uma `null` foi especificado para uma propriedade que não pode ser `null`, por exemplo, um que é marcado por um **indexado** ou **Not_Null** qualificador.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="9d6b9-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="9d6b9-145">0x8004100f</span></span> | <span data-ttu-id="9d6b9-146">A instância especificada é inválida.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-146">The specified instance is not valid.</span></span> <span data-ttu-id="9d6b9-147">(Por exemplo, chamar `PutInstanceWmi` com uma classe retorna esse valor.)</span><span class="sxs-lookup"><span data-stu-id="9d6b9-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9d6b9-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9d6b9-148">0x80041008</span></span> | <span data-ttu-id="9d6b9-149">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="9d6b9-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="9d6b9-150">0x80041019</span></span> | <span data-ttu-id="9d6b9-151">O `WBEM_FLAG_CREATE_ONLY` sinalizador foi especificado, mas a instância já existe.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="9d6b9-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9d6b9-152">0x80041002</span></span> | <span data-ttu-id="9d6b9-153">`WBEM_FLAG_UPDATE_ONLY` foi especificado no `lFlags`, mas a instância não existe.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9d6b9-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9d6b9-154">0x80041006</span></span> | <span data-ttu-id="9d6b9-155">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="9d6b9-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="9d6b9-156">0x80041033</span></span> | <span data-ttu-id="9d6b9-157">WMI foi provavelmente interrompido e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="9d6b9-158">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="9d6b9-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="9d6b9-159">0x80041015</span></span> | <span data-ttu-id="9d6b9-160">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9d6b9-161">0</span><span class="sxs-lookup"><span data-stu-id="9d6b9-161">0</span></span> | <span data-ttu-id="9d6b9-162">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="9d6b9-163">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d6b9-163">Remarks</span></span>

<span data-ttu-id="9d6b9-164">Essa função encapsula uma chamada para o [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) método.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="9d6b9-165">O `PutInstanceWmi` função dá suporte à criação de instâncias e instâncias de classes existentes somente atualização.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="9d6b9-166">Dependendo de como a `pCtx` parâmetro for definido, algumas ou todas as propriedades da instância são atualizadas.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="9d6b9-167">Quando a instância apontado pelo `pInst` pertence a uma subclasse, gerenciamento do Windows chama todos os provedores de responsáveis para as classes da qual deriva a subclasse.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="9d6b9-168">Todos esses provedores devem obter êxito para o original `PutInstanceWmi` solicitação seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="9d6b9-169">O provedor de suporte a classe de nível mais alta na hierarquia é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="9d6b9-170">A ordem de chamada continua com a subclasse da classe superior e prossegue de cima para baixo até que o gerenciamento do Windows alcança o provedor para a classe que tem a instância apontada pelo `pInst`.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="9d6b9-171">Gerenciamento do Windows não chama os provedores para qualquer uma das classes filhas de uma instância.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="9d6b9-172">Quando um aplicativo deve atualizar uma instância que pertence a uma hierarquia de classe, o `pInst` parâmetro deve apontar para a instância que contém as propriedades a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="9d6b9-173">Ou seja, considere uma instância de destino que pertence a **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="9d6b9-174">O **ClassB** instância deriva **ClassA**, e **ClassA** define a propriedade **PropA**.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="9d6b9-175">Se um aplicativo quiser fazer uma alteração para o valor de **PropA** na **ClassB** instância, ele deve definir `pInst` para essa instância em vez de uma instância do **ClassA** .</span><span class="sxs-lookup"><span data-stu-id="9d6b9-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="9d6b9-176">Chamar `PutInstanceWmi` em uma instância de uma classe abstrata não é permitido.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="9d6b9-177">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="9d6b9-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d6b9-178">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d6b9-178">Requirements</span></span>  
 <span data-ttu-id="9d6b9-179">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6b9-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6b9-180">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9d6b9-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9d6b9-181">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6b9-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6b9-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d6b9-182">See also</span></span>  
[<span data-ttu-id="9d6b9-183">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="9d6b9-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
