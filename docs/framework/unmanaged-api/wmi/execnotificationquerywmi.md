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
ms.openlocfilehash: 5cfe54c7c9b7ae707b2d3591afbd830bac171f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798652"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="b537c-103">Função ExecNotificationQueryWmi</span><span class="sxs-lookup"><span data-stu-id="b537c-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="b537c-104">Executa uma consulta para receber eventos.</span><span class="sxs-lookup"><span data-stu-id="b537c-104">Executes a query to receive events.</span></span> <span data-ttu-id="b537c-105">A chamada retorna imediatamente, e o chamador pode sondar o enumerador retornado em busca de eventos à medida que eles chegam.</span><span class="sxs-lookup"><span data-stu-id="b537c-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="b537c-106">A liberação do enumerador retornado cancela a consulta.</span><span class="sxs-lookup"><span data-stu-id="b537c-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b537c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b537c-107">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="b537c-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b537c-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="b537c-109">no Uma cadeia de caracteres com a linguagem de consulta válida com suporte pelo gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="b537c-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="b537c-110">Deve ser "WQL", o acrônimo para linguagem WQL.</span><span class="sxs-lookup"><span data-stu-id="b537c-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="b537c-111">no O texto da consulta.</span><span class="sxs-lookup"><span data-stu-id="b537c-111">[in] The text of the query.</span></span> <span data-ttu-id="b537c-112">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="b537c-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="b537c-113">no Uma combinação dos dois sinalizadores a seguir que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="b537c-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="b537c-114">Esses valores são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código.</span><span class="sxs-lookup"><span data-stu-id="b537c-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="b537c-115">Constante</span><span class="sxs-lookup"><span data-stu-id="b537c-115">Constant</span></span> | <span data-ttu-id="b537c-116">Valor</span><span class="sxs-lookup"><span data-stu-id="b537c-116">Value</span></span>  | <span data-ttu-id="b537c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b537c-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="b537c-118">0x10</span><span class="sxs-lookup"><span data-stu-id="b537c-118">0x10</span></span> | <span data-ttu-id="b537c-119">O sinalizador causa uma chamada de semisynchronous.</span><span class="sxs-lookup"><span data-stu-id="b537c-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="b537c-120">Se esse sinalizador não for definido, a chamada falhará.</span><span class="sxs-lookup"><span data-stu-id="b537c-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="b537c-121">Isso ocorre porque os eventos são recebidos continuamente, o que significa que o usuário deve sondar o enumerador retornado.</span><span class="sxs-lookup"><span data-stu-id="b537c-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="b537c-122">Bloquear essa chamada indefinidamente torna isso impossível.</span><span class="sxs-lookup"><span data-stu-id="b537c-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="b537c-123">0x20</span><span class="sxs-lookup"><span data-stu-id="b537c-123">0x20</span></span> | <span data-ttu-id="b537c-124">A função retorna um enumerador somente encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="b537c-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="b537c-125">Normalmente, enumeradores somente de encaminhamento são mais rápidos e usam menos memória do que enumeradores convencionais, mas não permitem que as chamadas [clonem](clone.md).</span><span class="sxs-lookup"><span data-stu-id="b537c-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="b537c-126">no Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="b537c-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="b537c-127">Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo os eventos solicitados.</span><span class="sxs-lookup"><span data-stu-id="b537c-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="b537c-128">fora Se nenhum erro ocorrer, o receberá o ponteiro para o enumerador que permite ao chamador recuperar as instâncias no conjunto de resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="b537c-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="b537c-129">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b537c-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="b537c-130">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="b537c-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="b537c-131">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="b537c-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="b537c-132">no Um ponteiro para um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="b537c-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="b537c-133">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="b537c-133">[in] The user name.</span></span> <span data-ttu-id="b537c-134">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b537c-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="b537c-135">no A senha.</span><span class="sxs-lookup"><span data-stu-id="b537c-135">[in] The password.</span></span> <span data-ttu-id="b537c-136">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b537c-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="b537c-137">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="b537c-137">[in] The domain name of the user.</span></span> <span data-ttu-id="b537c-138">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b537c-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="b537c-139">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b537c-139">Return value</span></span>

<span data-ttu-id="b537c-140">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="b537c-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b537c-141">Constante</span><span class="sxs-lookup"><span data-stu-id="b537c-141">Constant</span></span>  |<span data-ttu-id="b537c-142">Valor</span><span class="sxs-lookup"><span data-stu-id="b537c-142">Value</span></span>  |<span data-ttu-id="b537c-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="b537c-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="b537c-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="b537c-144">0x80041003</span></span> | <span data-ttu-id="b537c-145">O usuário não tem permissão para exibir uma ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="b537c-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="b537c-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b537c-146">0x80041001</span></span> | <span data-ttu-id="b537c-147">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="b537c-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b537c-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b537c-148">0x80041008</span></span> | <span data-ttu-id="b537c-149">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="b537c-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="b537c-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="b537c-150">0x80041010</span></span> | <span data-ttu-id="b537c-151">A consulta especifica uma classe que não existe.</span><span class="sxs-lookup"><span data-stu-id="b537c-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="b537c-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="b537c-152">0x80042002</span></span> | <span data-ttu-id="b537c-153">Foi solicitada muita precisão na entrega de eventos.</span><span class="sxs-lookup"><span data-stu-id="b537c-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="b537c-154">Uma tolerância de sondagem maior deve ser especificada.</span><span class="sxs-lookup"><span data-stu-id="b537c-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="b537c-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="b537c-155">0x80042001</span></span> | <span data-ttu-id="b537c-156">A consulta solicita mais informações do que o gerenciamento do Windows pode fornecer.</span><span class="sxs-lookup"><span data-stu-id="b537c-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="b537c-157">Isso `HRESULT` é retornado quando uma consulta de evento resulta em uma solicitação para sondar todos os objetos em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b537c-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="b537c-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="b537c-158">0x80041017</span></span> | <span data-ttu-id="b537c-159">A consulta tinha um erro de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="b537c-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="b537c-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="b537c-160">0x80041018</span></span> | <span data-ttu-id="b537c-161">O idioma de consulta solicitado não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="b537c-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="b537c-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="b537c-162">0x8004106c</span></span> | <span data-ttu-id="b537c-163">A consulta é muito complexa.</span><span class="sxs-lookup"><span data-stu-id="b537c-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b537c-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b537c-164">0x80041006</span></span> | <span data-ttu-id="b537c-165">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="b537c-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="b537c-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="b537c-166">0x80041033</span></span> | <span data-ttu-id="b537c-167">O WMI provavelmente foi interrompido e reiniciado.</span><span class="sxs-lookup"><span data-stu-id="b537c-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="b537c-168">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="b537c-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b537c-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b537c-169">0x80041015</span></span> | <span data-ttu-id="b537c-170">O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="b537c-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="b537c-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="b537c-171">0x80041058</span></span> | <span data-ttu-id="b537c-172">A consulta não pode ser analisada.</span><span class="sxs-lookup"><span data-stu-id="b537c-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b537c-173">0</span><span class="sxs-lookup"><span data-stu-id="b537c-173">0</span></span> | <span data-ttu-id="b537c-174">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b537c-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="b537c-175">Comentários</span><span class="sxs-lookup"><span data-stu-id="b537c-175">Remarks</span></span>

<span data-ttu-id="b537c-176">Essa função encapsula uma chamada para o método [IWbemServices:: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) .</span><span class="sxs-lookup"><span data-stu-id="b537c-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="b537c-177">Depois que a função retorna, o chamador passa periodicamente `ppEnum` o objeto retornado para a [próxima](next.md) função para ver se há algum evento disponível.</span><span class="sxs-lookup"><span data-stu-id="b537c-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="b537c-178">Há limites para o número de `AND` palavras-chave e `OR` que podem ser usadas em consultas WQL.</span><span class="sxs-lookup"><span data-stu-id="b537c-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="b537c-179">Grandes números de palavras-chave WQL usadas em uma consulta complexa podem fazer com que o WMI `WBEM_E_QUOTA_VIOLATION` retorne o código de erro (ou `HRESULT` 0x8004106c) como um valor.</span><span class="sxs-lookup"><span data-stu-id="b537c-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="b537c-180">O limite de palavras-chave WQL depende da complexidade da consulta.</span><span class="sxs-lookup"><span data-stu-id="b537c-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="b537c-181">Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="b537c-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b537c-182">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b537c-182">Requirements</span></span>

<span data-ttu-id="b537c-183">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b537c-183">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b537c-184">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b537c-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="b537c-185">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b537c-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b537c-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b537c-186">See also</span></span>

- [<span data-ttu-id="b537c-187">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b537c-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
