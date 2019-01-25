---
title: Função ExecQueryWmi (referência de API não gerenciada)
description: A função ExecQueryWmi executa uma consulta para recuperar objetos.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cd8992fc37c570b5ea20f8751bef729311bfb7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718189"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="bacee-103">Função ExecQueryWmi</span><span class="sxs-lookup"><span data-stu-id="bacee-103">ExecQueryWmi function</span></span>
<span data-ttu-id="bacee-104">Executa uma consulta para recuperar objetos.</span><span class="sxs-lookup"><span data-stu-id="bacee-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bacee-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bacee-105">Syntax</span></span>  
  
```  
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a><span data-ttu-id="bacee-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bacee-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="bacee-107">[in] Uma cadeia de caracteres com a linguagem de consulta válida com suporte pelo gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="bacee-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="bacee-108">Ele deve ser "WQL", o acrônimo de linguagem de consulta WMI.</span><span class="sxs-lookup"><span data-stu-id="bacee-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="bacee-109">[in] O texto da consulta.</span><span class="sxs-lookup"><span data-stu-id="bacee-109">[in] The text of the query.</span></span> <span data-ttu-id="bacee-110">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="bacee-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="bacee-111">[in] Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="bacee-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="bacee-112">Os seguintes valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="bacee-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="bacee-113">Constante</span><span class="sxs-lookup"><span data-stu-id="bacee-113">Constant</span></span> | <span data-ttu-id="bacee-114">Valor</span><span class="sxs-lookup"><span data-stu-id="bacee-114">Value</span></span>  | <span data-ttu-id="bacee-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bacee-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="bacee-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="bacee-116">0x20000</span></span> | <span data-ttu-id="bacee-117">Se definido, a função recupera os qualificadores corrigidos armazenados no namespace localizado da localidade da conexão atual.</span><span class="sxs-lookup"><span data-stu-id="bacee-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="bacee-118">Se não for definido, a função recupera somente os qualificadores armazenados no namespace de imediato.</span><span class="sxs-lookup"><span data-stu-id="bacee-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="bacee-119">0x10</span><span class="sxs-lookup"><span data-stu-id="bacee-119">0x10</span></span> | <span data-ttu-id="bacee-120">O sinalizador faz com que uma chamada semissíncrona.</span><span class="sxs-lookup"><span data-stu-id="bacee-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="bacee-121">0x20</span><span class="sxs-lookup"><span data-stu-id="bacee-121">0x20</span></span> | <span data-ttu-id="bacee-122">A função retorna um enumerador de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="bacee-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="bacee-123">Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas eles não permitem chamadas para [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="bacee-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="bacee-124">0</span><span class="sxs-lookup"><span data-stu-id="bacee-124">0</span></span> | <span data-ttu-id="bacee-125">WMI mantém ponteiros para objetos no enumration até que eles sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="bacee-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="bacee-126">0x100</span><span class="sxs-lookup"><span data-stu-id="bacee-126">0x100</span></span> | <span data-ttu-id="bacee-127">Garante que quaisquer objetos retornados tenham informações suficientes neles até que as propriedades do sistema, como **Path**, **RelPath**, e **Server**, não são `null`.</span><span class="sxs-lookup"><span data-stu-id="bacee-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="bacee-128">2</span><span class="sxs-lookup"><span data-stu-id="bacee-128">2</span></span> | <span data-ttu-id="bacee-129">Este sinalizador é usado para criação de protótipos.</span><span class="sxs-lookup"><span data-stu-id="bacee-129">This flag is used for prototyping.</span></span> <span data-ttu-id="bacee-130">Ele não executa a consulta e, em vez disso, retorna um objeto que se parece com um objeto de resultado típico.</span><span class="sxs-lookup"><span data-stu-id="bacee-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="bacee-131">0x200</span><span class="sxs-lookup"><span data-stu-id="bacee-131">0x200</span></span> | <span data-ttu-id="bacee-132">Causas acesso direcionam ao provedor para a classe especificada sem levar em consideração as subclasses ou de sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="bacee-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="bacee-133">Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="bacee-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="bacee-134">[in] Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="bacee-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="bacee-135">Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="bacee-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="bacee-136">[out] Se nenhum erro ocorrer, recebe o ponteiro para o enumerador que permite que o chamador recuperar as instâncias no conjunto de resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="bacee-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="bacee-137">A consulta pode ter um conjunto de resultados com instâncias de zero.</span><span class="sxs-lookup"><span data-stu-id="bacee-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="bacee-138">Consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="bacee-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="bacee-139">[in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="bacee-139">[in] The authorization level.</span></span>

<span data-ttu-id="bacee-140">`impLevel` [in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="bacee-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="bacee-141">[in] Um ponteiro para um [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="bacee-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="bacee-142">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="bacee-142">[in] The user name.</span></span> <span data-ttu-id="bacee-143">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="bacee-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="bacee-144">[in] A senha.</span><span class="sxs-lookup"><span data-stu-id="bacee-144">[in] The password.</span></span> <span data-ttu-id="bacee-145">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="bacee-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="bacee-146">[in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="bacee-146">[in] The domain name of the user.</span></span> <span data-ttu-id="bacee-147">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="bacee-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="bacee-148">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bacee-148">Return value</span></span>

<span data-ttu-id="bacee-149">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="bacee-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bacee-150">Constante</span><span class="sxs-lookup"><span data-stu-id="bacee-150">Constant</span></span>  |<span data-ttu-id="bacee-151">Valor</span><span class="sxs-lookup"><span data-stu-id="bacee-151">Value</span></span>  |<span data-ttu-id="bacee-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="bacee-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="bacee-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="bacee-153">0x80041003</span></span> | <span data-ttu-id="bacee-154">O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="bacee-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="bacee-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bacee-155">0x80041001</span></span> | <span data-ttu-id="bacee-156">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="bacee-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bacee-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bacee-157">0x80041008</span></span> | <span data-ttu-id="bacee-158">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="bacee-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="bacee-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="bacee-159">0x80041017</span></span> | <span data-ttu-id="bacee-160">A consulta teve um erro de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="bacee-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="bacee-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="bacee-161">0x80041018</span></span> | <span data-ttu-id="bacee-162">O idioma de consulta solicitado não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="bacee-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="bacee-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="bacee-163">0x8004106c</span></span> | <span data-ttu-id="bacee-164">A consulta é muito complexa.</span><span class="sxs-lookup"><span data-stu-id="bacee-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bacee-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bacee-165">0x80041006</span></span> | <span data-ttu-id="bacee-166">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="bacee-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="bacee-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="bacee-167">0x80041033</span></span> | <span data-ttu-id="bacee-168">WMI foi provavelmente interrompido e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="bacee-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="bacee-169">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="bacee-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="bacee-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="bacee-170">0x80041015</span></span> | <span data-ttu-id="bacee-171">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="bacee-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="bacee-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="bacee-172">0x80041002</span></span> | <span data-ttu-id="bacee-173">A consulta especifica uma classe que não existe.</span><span class="sxs-lookup"><span data-stu-id="bacee-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bacee-174">0</span><span class="sxs-lookup"><span data-stu-id="bacee-174">0</span></span> | <span data-ttu-id="bacee-175">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bacee-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bacee-176">Comentários</span><span class="sxs-lookup"><span data-stu-id="bacee-176">Remarks</span></span>

<span data-ttu-id="bacee-177">Essa função encapsula uma chamada para o [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) método.</span><span class="sxs-lookup"><span data-stu-id="bacee-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="bacee-178">Essa função processa a consulta especificada no `strQuery` parâmetro e cria um enumerador por meio do qual o chamador pode acessar os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="bacee-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="bacee-179">O enumerador é um ponteiro para um [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; a consulta os resultados são instâncias de objetos de classe disponibilizados por meio de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span><span class="sxs-lookup"><span data-stu-id="bacee-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="bacee-180">Há limites para o número de `AND` e `OR` palavras-chave que podem ser usadas em consultas WQL.</span><span class="sxs-lookup"><span data-stu-id="bacee-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="bacee-181">Grande número de palavras-chave WQL usadas em uma consulta complexa pode fazer com que o WMI retornar os `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) código de erro como um `HRESULT` valor.</span><span class="sxs-lookup"><span data-stu-id="bacee-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="bacee-182">O limite de palavras-chave WQL depende complexas como a consulta é.</span><span class="sxs-lookup"><span data-stu-id="bacee-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="bacee-183">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="bacee-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bacee-184">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bacee-184">Requirements</span></span>  
 <span data-ttu-id="bacee-185">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bacee-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bacee-186">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bacee-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bacee-187">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bacee-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bacee-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bacee-188">See also</span></span>
- [<span data-ttu-id="bacee-189">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="bacee-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
