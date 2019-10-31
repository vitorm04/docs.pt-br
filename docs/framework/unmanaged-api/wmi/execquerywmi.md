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
ms.openlocfilehash: 3c6ea58eca5ac635893a24b57ade261e04a69721
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130430"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="aa02a-103">Função ExecQueryWmi</span><span class="sxs-lookup"><span data-stu-id="aa02a-103">ExecQueryWmi function</span></span>

<span data-ttu-id="aa02a-104">Executa uma consulta para recuperar objetos.</span><span class="sxs-lookup"><span data-stu-id="aa02a-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="aa02a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa02a-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="aa02a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa02a-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="aa02a-107">no Uma cadeia de caracteres com a linguagem de consulta válida com suporte pelo gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="aa02a-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="aa02a-108">Deve ser "WQL", o acrônimo para linguagem WQL.</span><span class="sxs-lookup"><span data-stu-id="aa02a-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="aa02a-109">no O texto da consulta.</span><span class="sxs-lookup"><span data-stu-id="aa02a-109">[in] The text of the query.</span></span> <span data-ttu-id="aa02a-110">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="aa02a-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="aa02a-111">no Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="aa02a-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="aa02a-112">Os valores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="aa02a-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="aa02a-113">Constante</span><span class="sxs-lookup"><span data-stu-id="aa02a-113">Constant</span></span> | <span data-ttu-id="aa02a-114">Valor</span><span class="sxs-lookup"><span data-stu-id="aa02a-114">Value</span></span>  | <span data-ttu-id="aa02a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa02a-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="aa02a-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="aa02a-116">0x20000</span></span> | <span data-ttu-id="aa02a-117">Se definido, a função recupera os qualificadores corrigidos armazenados no namespace localizado da localidade da conexão atual.</span><span class="sxs-lookup"><span data-stu-id="aa02a-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="aa02a-118">Se não for definido, a função recuperará somente os qualificadores armazenados no namespace imediato.</span><span class="sxs-lookup"><span data-stu-id="aa02a-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="aa02a-119">0x10</span><span class="sxs-lookup"><span data-stu-id="aa02a-119">0x10</span></span> | <span data-ttu-id="aa02a-120">O sinalizador causa uma chamada de semisynchronous.</span><span class="sxs-lookup"><span data-stu-id="aa02a-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="aa02a-121">0x20</span><span class="sxs-lookup"><span data-stu-id="aa02a-121">0x20</span></span> | <span data-ttu-id="aa02a-122">A função retorna um enumerador somente encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="aa02a-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="aa02a-123">Normalmente, enumeradores somente de encaminhamento são mais rápidos e usam menos memória do que enumeradores convencionais, mas não permitem que as chamadas [clonem](clone.md).</span><span class="sxs-lookup"><span data-stu-id="aa02a-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="aa02a-124">0</span><span class="sxs-lookup"><span data-stu-id="aa02a-124">0</span></span> | <span data-ttu-id="aa02a-125">O WMI retém ponteiros para objetos na enumeração até que sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="aa02a-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="aa02a-126">0x100</span><span class="sxs-lookup"><span data-stu-id="aa02a-126">0x100</span></span> | <span data-ttu-id="aa02a-127">Garante que todos os objetos retornados tenham informações suficientes para que as propriedades do sistema, como **__PATH**, **__RELPATH**e **__SERVER**, não sejam `null`.</span><span class="sxs-lookup"><span data-stu-id="aa02a-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="aa02a-128">2</span><span class="sxs-lookup"><span data-stu-id="aa02a-128">2</span></span> | <span data-ttu-id="aa02a-129">Este sinalizador é usado para criação de protótipos.</span><span class="sxs-lookup"><span data-stu-id="aa02a-129">This flag is used for prototyping.</span></span> <span data-ttu-id="aa02a-130">Ele não executa a consulta e, em vez disso, retorna um objeto que se parece com um objeto de resultado típico.</span><span class="sxs-lookup"><span data-stu-id="aa02a-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="aa02a-131">0x200</span><span class="sxs-lookup"><span data-stu-id="aa02a-131">0x200</span></span> | <span data-ttu-id="aa02a-132">Faz com que o acesso direto ao provedor para a classe especificada sem considerar sua classe pai ou qualquer subclasse.</span><span class="sxs-lookup"><span data-stu-id="aa02a-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="aa02a-133">Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="aa02a-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="aa02a-134">no Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="aa02a-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="aa02a-135">Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="aa02a-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="aa02a-136">fora Se nenhum erro ocorrer, o receberá o ponteiro para o enumerador que permite ao chamador recuperar as instâncias no conjunto de resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="aa02a-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="aa02a-137">A consulta pode ter um conjunto de resultados com zero instâncias.</span><span class="sxs-lookup"><span data-stu-id="aa02a-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="aa02a-138">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aa02a-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="aa02a-139">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="aa02a-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="aa02a-140">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="aa02a-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="aa02a-141">no Um ponteiro para um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="aa02a-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="aa02a-142">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="aa02a-142">[in] The user name.</span></span> <span data-ttu-id="aa02a-143">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aa02a-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="aa02a-144">no A senha.</span><span class="sxs-lookup"><span data-stu-id="aa02a-144">[in] The password.</span></span> <span data-ttu-id="aa02a-145">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aa02a-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="aa02a-146">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="aa02a-146">[in] The domain name of the user.</span></span> <span data-ttu-id="aa02a-147">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="aa02a-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="aa02a-148">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="aa02a-148">Return value</span></span>

<span data-ttu-id="aa02a-149">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="aa02a-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aa02a-150">Constante</span><span class="sxs-lookup"><span data-stu-id="aa02a-150">Constant</span></span>  |<span data-ttu-id="aa02a-151">Valor</span><span class="sxs-lookup"><span data-stu-id="aa02a-151">Value</span></span>  |<span data-ttu-id="aa02a-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa02a-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="aa02a-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="aa02a-153">0x80041003</span></span> | <span data-ttu-id="aa02a-154">O usuário não tem permissão para exibir uma ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="aa02a-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="aa02a-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="aa02a-155">0x80041001</span></span> | <span data-ttu-id="aa02a-156">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="aa02a-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="aa02a-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="aa02a-157">0x80041008</span></span> | <span data-ttu-id="aa02a-158">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="aa02a-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="aa02a-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="aa02a-159">0x80041017</span></span> | <span data-ttu-id="aa02a-160">A consulta tinha um erro de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="aa02a-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="aa02a-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="aa02a-161">0x80041018</span></span> | <span data-ttu-id="aa02a-162">O idioma de consulta solicitado não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="aa02a-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="aa02a-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="aa02a-163">0x8004106c</span></span> | <span data-ttu-id="aa02a-164">A consulta é muito complexa.</span><span class="sxs-lookup"><span data-stu-id="aa02a-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="aa02a-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="aa02a-165">0x80041006</span></span> | <span data-ttu-id="aa02a-166">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="aa02a-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="aa02a-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="aa02a-167">0x80041033</span></span> | <span data-ttu-id="aa02a-168">O WMI provavelmente foi interrompido e reiniciado.</span><span class="sxs-lookup"><span data-stu-id="aa02a-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="aa02a-169">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="aa02a-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="aa02a-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="aa02a-170">0x80041015</span></span> | <span data-ttu-id="aa02a-171">O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="aa02a-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="aa02a-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="aa02a-172">0x80041002</span></span> | <span data-ttu-id="aa02a-173">A consulta especifica uma classe que não existe.</span><span class="sxs-lookup"><span data-stu-id="aa02a-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="aa02a-174">0</span><span class="sxs-lookup"><span data-stu-id="aa02a-174">0</span></span> | <span data-ttu-id="aa02a-175">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="aa02a-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="aa02a-176">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa02a-176">Remarks</span></span>

<span data-ttu-id="aa02a-177">Essa função encapsula uma chamada para o método [IWbemServices:: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) .</span><span class="sxs-lookup"><span data-stu-id="aa02a-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="aa02a-178">Essa função processa a consulta especificada no parâmetro `strQuery` e cria um enumerador por meio do qual o chamador pode acessar os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="aa02a-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="aa02a-179">O enumerador é um ponteiro para uma interface [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) ; os resultados da consulta são instâncias de objetos de classe disponibilizados por meio da interface [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="aa02a-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="aa02a-180">Há limites para o número de `AND` e `OR` palavras-chave que podem ser usadas em consultas WQL.</span><span class="sxs-lookup"><span data-stu-id="aa02a-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="aa02a-181">Grandes números de palavras-chave WQL usadas em uma consulta complexa podem fazer com que o WMI retorne o código de erro `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) como um valor de `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="aa02a-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="aa02a-182">O limite de palavras-chave WQL depende da complexidade da consulta.</span><span class="sxs-lookup"><span data-stu-id="aa02a-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="aa02a-183">Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="aa02a-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa02a-184">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa02a-184">Requirements</span></span>

<span data-ttu-id="aa02a-185">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa02a-185">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="aa02a-186">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="aa02a-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="aa02a-187">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aa02a-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aa02a-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa02a-188">See also</span></span>

- [<span data-ttu-id="aa02a-189">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="aa02a-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
