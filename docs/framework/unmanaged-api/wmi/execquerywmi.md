---
title: "Função ExecQueryWmi (referência de API não gerenciada)"
description: "A função ExecQueryWmi executa uma consulta para recuperar objetos."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecQueryWmi
helpviewer_keywords: ExecQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ebd5463fd3b4109203e829da8e3683bbb79cf59
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="execquerywmi-function"></a><span data-ttu-id="5d7fc-103">Função ExecQueryWmi</span><span class="sxs-lookup"><span data-stu-id="5d7fc-103">ExecQueryWmi function</span></span>
<span data-ttu-id="5d7fc-104">Executa uma consulta para recuperar objetos.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5d7fc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d7fc-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="5d7fc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d7fc-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="5d7fc-107">[in] Uma cadeia de caracteres com a linguagem de consulta válido com suporte de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="5d7fc-108">Ele deve ser "WQL", o acrônimo para a linguagem de consulta WMI.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="5d7fc-109">[in] O texto da consulta.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-109">[in] The text of the query.</span></span> <span data-ttu-id="5d7fc-110">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="5d7fc-111">[in] Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="5d7fc-112">Os seguintes valores são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="5d7fc-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="5d7fc-113">Constante</span><span class="sxs-lookup"><span data-stu-id="5d7fc-113">Constant</span></span> | <span data-ttu-id="5d7fc-114">Valor</span><span class="sxs-lookup"><span data-stu-id="5d7fc-114">Value</span></span>  | <span data-ttu-id="5d7fc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d7fc-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="5d7fc-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="5d7fc-116">0x20000</span></span> | <span data-ttu-id="5d7fc-117">Se o conjunto, a função recupera os qualificadores aperfeiçoados armazenados no namespace localizado da localidade da conexão atual.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="5d7fc-118">Se não for definido, a função recupera somente os qualificadores armazenados no namespace de imediato.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="5d7fc-119">0x10</span><span class="sxs-lookup"><span data-stu-id="5d7fc-119">0x10</span></span> | <span data-ttu-id="5d7fc-120">O sinalizador faz com que uma chamada semi-síncrona.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="5d7fc-121">0x20</span><span class="sxs-lookup"><span data-stu-id="5d7fc-121">0x20</span></span> | <span data-ttu-id="5d7fc-122">A função retorna um enumerador de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="5d7fc-123">Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas não permitem chamadas para [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="5d7fc-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="5d7fc-124">0</span><span class="sxs-lookup"><span data-stu-id="5d7fc-124">0</span></span> | <span data-ttu-id="5d7fc-125">WMI retém ponteiros para objetos de enumration até que eles sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="5d7fc-126">0x100</span><span class="sxs-lookup"><span data-stu-id="5d7fc-126">0x100</span></span> | <span data-ttu-id="5d7fc-127">Garante que qualquer retornado objetos possuem informações suficientes para que propriedades do sistema, como **__PATH**, **RelPath**, e **Server**, não são `null`.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="5d7fc-128">2</span><span class="sxs-lookup"><span data-stu-id="5d7fc-128">2</span></span> | <span data-ttu-id="5d7fc-129">Este sinalizador é usado para criação de protótipos.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-129">This flag is used for prototyping.</span></span> <span data-ttu-id="5d7fc-130">Ele não executa a consulta e retorna um objeto que se parece com um objeto de resultado típico.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="5d7fc-131">0x200</span><span class="sxs-lookup"><span data-stu-id="5d7fc-131">0x200</span></span> | <span data-ttu-id="5d7fc-132">Causas direcionam o acesso ao provedor para a classe especificada independentemente de sua classe pai ou as subclasses.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="5d7fc-133">Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="5d7fc-134">[in] Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="5d7fc-135">Caso contrário, é um ponteiro para um [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instância pode ser usada pelo provedor que fornece as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-135">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="5d7fc-136">[out] Se nenhum erro ocorrer, recebe o ponteiro para o enumerador que permite que o chamador recuperar as instâncias no conjunto de resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="5d7fc-137">A consulta pode ter um conjunto de resultados com zero instâncias.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="5d7fc-138">Consulte o [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="5d7fc-139">[in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-139">[in] The authorization level.</span></span>

<span data-ttu-id="5d7fc-140">`impLevel`[in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="5d7fc-141">[in] Um ponteiro para um [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objeto que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-141">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="5d7fc-142">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-142">[in] The user name.</span></span> <span data-ttu-id="5d7fc-143">Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="5d7fc-144">[in] A senha.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-144">[in] The password.</span></span> <span data-ttu-id="5d7fc-145">Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="5d7fc-146">[in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-146">[in] The domain name of the user.</span></span> <span data-ttu-id="5d7fc-147">Consulte o [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d7fc-148">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5d7fc-148">Return value</span></span>

<span data-ttu-id="5d7fc-149">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="5d7fc-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5d7fc-150">Constante</span><span class="sxs-lookup"><span data-stu-id="5d7fc-150">Constant</span></span>  |<span data-ttu-id="5d7fc-151">Valor</span><span class="sxs-lookup"><span data-stu-id="5d7fc-151">Value</span></span>  |<span data-ttu-id="5d7fc-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d7fc-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="5d7fc-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="5d7fc-153">0x80041003</span></span> | <span data-ttu-id="5d7fc-154">O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="5d7fc-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5d7fc-155">0x80041001</span></span> | <span data-ttu-id="5d7fc-156">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5d7fc-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5d7fc-157">0x80041008</span></span> | <span data-ttu-id="5d7fc-158">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="5d7fc-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="5d7fc-159">0x80041017</span></span> | <span data-ttu-id="5d7fc-160">A consulta teve um erro de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="5d7fc-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="5d7fc-161">0x80041018</span></span> | <span data-ttu-id="5d7fc-162">O idioma de consulta solicitado não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="5d7fc-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="5d7fc-163">0x8004106c</span></span> | <span data-ttu-id="5d7fc-164">A consulta é muito complexa.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5d7fc-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5d7fc-165">0x80041006</span></span> | <span data-ttu-id="5d7fc-166">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="5d7fc-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="5d7fc-167">0x80041033</span></span> | <span data-ttu-id="5d7fc-168">WMI foi provavelmente interrompido e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="5d7fc-169">Chamar [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="5d7fc-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="5d7fc-170">0x80041015</span></span> | <span data-ttu-id="5d7fc-171">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="5d7fc-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5d7fc-172">0x80041002</span></span> | <span data-ttu-id="5d7fc-173">A consulta especifica uma classe que não existe.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5d7fc-174">0</span><span class="sxs-lookup"><span data-stu-id="5d7fc-174">0</span></span> | <span data-ttu-id="5d7fc-175">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5d7fc-176">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d7fc-176">Remarks</span></span>

<span data-ttu-id="5d7fc-177">Essa função encapsula uma chamada para o [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-177">This function wraps a call to the [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5d7fc-178">Essa função processa a consulta especificada no `strQuery` parâmetro e cria um enumerador por meio do qual o chamador pode acessar os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="5d7fc-179">O enumerador é um ponteiro para um [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; a consulta resultados são instâncias de objetos de classe disponibilizados por meio de [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-179">The enumerator is a pointer to an [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; the query results are instances of class objects made available through the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span></span>

<span data-ttu-id="5d7fc-180">Há limites para o número de `AND` e `OR` palavras-chave que podem ser usadas em consultas WQL.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="5d7fc-181">Grandes números das palavras-chave WQL usadas em uma consulta complexa podem fazer com que o WMI retornar o `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) código de erro como uma `HRESULT` valor.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="5d7fc-182">O limite de palavras-chave WQL depende a consulta é complexo.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="5d7fc-183">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d7fc-184">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d7fc-184">Requirements</span></span>  
 <span data-ttu-id="5d7fc-185">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d7fc-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d7fc-186">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5d7fc-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5d7fc-187">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5d7fc-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7fc-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d7fc-188">See also</span></span>  
[<span data-ttu-id="5d7fc-189">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="5d7fc-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
