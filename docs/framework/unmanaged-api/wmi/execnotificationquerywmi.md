---
title: Função ExecNotificationQueryWmi (referência de API não gerenciada)
description: A função ExecNotificationQueryWmi executa uma consulta para receber eventos.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd00a1fa8099d5a87577271487c46e68a46794c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566977"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="b468e-103">Função ExecNotificationQueryWmi</span><span class="sxs-lookup"><span data-stu-id="b468e-103">ExecNotificationQueryWmi function</span></span>
<span data-ttu-id="b468e-104">Executa uma consulta para receber eventos.</span><span class="sxs-lookup"><span data-stu-id="b468e-104">Executes a query to receive events.</span></span> <span data-ttu-id="b468e-105">A chamada retorna imediatamente, e o chamador pode sondar o enumerador retornado para eventos à medida que eles chegam.</span><span class="sxs-lookup"><span data-stu-id="b468e-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="b468e-106">Liberar enumerador retornado cancela a consulta.</span><span class="sxs-lookup"><span data-stu-id="b468e-106">Releasing the returned enumerator cancels the query.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b468e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b468e-107">Syntax</span></span>  
  
```  
HRESULT ExecNotificationQueryWmi (
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

## <a name="parameters"></a><span data-ttu-id="b468e-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b468e-108">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="b468e-109">[in] Uma cadeia de caracteres com a linguagem de consulta válida com suporte pelo gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="b468e-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="b468e-110">Ele deve ser "WQL", o acrônimo de linguagem de consulta WMI.</span><span class="sxs-lookup"><span data-stu-id="b468e-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="b468e-111">[in] O texto da consulta.</span><span class="sxs-lookup"><span data-stu-id="b468e-111">[in] The text of the query.</span></span> <span data-ttu-id="b468e-112">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="b468e-112">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="b468e-113">[in] Uma combinação dos seguintes dois sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="b468e-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="b468e-114">Esses valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="b468e-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> 

| <span data-ttu-id="b468e-115">Constante</span><span class="sxs-lookup"><span data-stu-id="b468e-115">Constant</span></span> | <span data-ttu-id="b468e-116">Valor</span><span class="sxs-lookup"><span data-stu-id="b468e-116">Value</span></span>  | <span data-ttu-id="b468e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b468e-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="b468e-118">0x10</span><span class="sxs-lookup"><span data-stu-id="b468e-118">0x10</span></span> | <span data-ttu-id="b468e-119">O sinalizador faz com que uma chamada semissíncrona.</span><span class="sxs-lookup"><span data-stu-id="b468e-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="b468e-120">Se este sinalizador não for definido, a chamada falhará.</span><span class="sxs-lookup"><span data-stu-id="b468e-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="b468e-121">Isso é porque os eventos são recebidos continuamente, que significa que o usuário deve sondar o enumerador retornado.</span><span class="sxs-lookup"><span data-stu-id="b468e-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="b468e-122">Essa chamada de bloqueio por tempo indeterminado, que torna impossível.</span><span class="sxs-lookup"><span data-stu-id="b468e-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="b468e-123">0x20</span><span class="sxs-lookup"><span data-stu-id="b468e-123">0x20</span></span> | <span data-ttu-id="b468e-124">A função retorna um enumerador de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="b468e-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="b468e-125">Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas eles não permitem chamadas para [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="b468e-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`  
<span data-ttu-id="b468e-126">[in] Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="b468e-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="b468e-127">Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo os eventos solicitados.</span><span class="sxs-lookup"><span data-stu-id="b468e-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span> 

`ppEnum`  
<span data-ttu-id="b468e-128">[out] Se nenhum erro ocorrer, recebe o ponteiro para o enumerador que permite que o chamador recuperar as instâncias no conjunto de resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="b468e-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="b468e-129">Consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b468e-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="b468e-130">[in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="b468e-130">[in] The authorization level.</span></span>

<span data-ttu-id="b468e-131">`impLevel` [in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="b468e-131">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="b468e-132">[in] Um ponteiro para um [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="b468e-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="b468e-133">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="b468e-133">[in] The user name.</span></span> <span data-ttu-id="b468e-134">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b468e-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="b468e-135">[in] A senha.</span><span class="sxs-lookup"><span data-stu-id="b468e-135">[in] The password.</span></span> <span data-ttu-id="b468e-136">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b468e-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="b468e-137">[in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="b468e-137">[in] The domain name of the user.</span></span> <span data-ttu-id="b468e-138">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b468e-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="b468e-139">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b468e-139">Return value</span></span>

<span data-ttu-id="b468e-140">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="b468e-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b468e-141">Constante</span><span class="sxs-lookup"><span data-stu-id="b468e-141">Constant</span></span>  |<span data-ttu-id="b468e-142">Valor</span><span class="sxs-lookup"><span data-stu-id="b468e-142">Value</span></span>  |<span data-ttu-id="b468e-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="b468e-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="b468e-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="b468e-144">0x80041003</span></span> | <span data-ttu-id="b468e-145">O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="b468e-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="b468e-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b468e-146">0x80041001</span></span> | <span data-ttu-id="b468e-147">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="b468e-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b468e-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b468e-148">0x80041008</span></span> | <span data-ttu-id="b468e-149">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="b468e-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="b468e-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="b468e-150">0x80041010</span></span> | <span data-ttu-id="b468e-151">A consulta especifica uma classe que não existe.</span><span class="sxs-lookup"><span data-stu-id="b468e-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="b468e-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="b468e-152">0x80042002</span></span> | <span data-ttu-id="b468e-153">Muita precisão na entrega de eventos foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="b468e-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="b468e-154">Uma maior tolerância de sondagem deve ser especificada.</span><span class="sxs-lookup"><span data-stu-id="b468e-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="b468e-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="b468e-155">0x80042001</span></span> | <span data-ttu-id="b468e-156">A consulta requess mais informações de gerenciamento do Windows podem fornecer.</span><span class="sxs-lookup"><span data-stu-id="b468e-156">The query requess more information than Windows Management can provide.</span></span> <span data-ttu-id="b468e-157">Isso `HRESULT` é retornado quando uma consulta de evento resulta em uma solicitação de sondagem de todos os objetos em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b468e-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="b468e-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="b468e-158">0x80041017</span></span> | <span data-ttu-id="b468e-159">A consulta teve um erro de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="b468e-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="b468e-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="b468e-160">0x80041018</span></span> | <span data-ttu-id="b468e-161">O idioma de consulta solicitado não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="b468e-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="b468e-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="b468e-162">0x8004106c</span></span> | <span data-ttu-id="b468e-163">A consulta é muito complexa.</span><span class="sxs-lookup"><span data-stu-id="b468e-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b468e-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b468e-164">0x80041006</span></span> | <span data-ttu-id="b468e-165">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="b468e-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="b468e-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="b468e-166">0x80041033</span></span> | <span data-ttu-id="b468e-167">WMI foi provavelmente interrompido e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="b468e-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="b468e-168">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="b468e-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b468e-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b468e-169">0x80041015</span></span> | <span data-ttu-id="b468e-170">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="b468e-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="b468e-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="b468e-171">0x80041058</span></span> | <span data-ttu-id="b468e-172">A consulta não pode ser analisada.</span><span class="sxs-lookup"><span data-stu-id="b468e-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b468e-173">0</span><span class="sxs-lookup"><span data-stu-id="b468e-173">0</span></span> | <span data-ttu-id="b468e-174">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b468e-174">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b468e-175">Comentários</span><span class="sxs-lookup"><span data-stu-id="b468e-175">Remarks</span></span>

<span data-ttu-id="b468e-176">Essa função encapsula uma chamada para o [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) método.</span><span class="sxs-lookup"><span data-stu-id="b468e-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="b468e-177">Depois que a função retornar, o chamador periodicamente passa retornado `ppEnum` do objeto para o [próxima](next.md) função para ver se todos os eventos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b468e-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="b468e-178">Há limites para o número de `AND` e `OR` palavras-chave que podem ser usadas em consultas WQL.</span><span class="sxs-lookup"><span data-stu-id="b468e-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="b468e-179">Grande número de palavras-chave WQL usadas em uma consulta complexa pode fazer com que o WMI retornar os `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) código de erro como um `HRESULT` valor.</span><span class="sxs-lookup"><span data-stu-id="b468e-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="b468e-180">O limite de palavras-chave WQL depende complexas como a consulta é.</span><span class="sxs-lookup"><span data-stu-id="b468e-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="b468e-181">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="b468e-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b468e-182">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b468e-182">Requirements</span></span>  
 <span data-ttu-id="b468e-183">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b468e-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b468e-184">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b468e-184">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b468e-185">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b468e-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b468e-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b468e-186">See also</span></span>
- [<span data-ttu-id="b468e-187">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b468e-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
