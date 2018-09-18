---
title: Função ConnectServerWmi (referência de API não gerenciada)
description: A função ConnectServerWmi usa DCOM para criar uma conexão a um namespace WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 163e61eef8a753b5b6470285e5e3ce63789e25a4
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970417"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="27009-103">Função ConnectServerWmi</span><span class="sxs-lookup"><span data-stu-id="27009-103">ConnectServerWmi function</span></span>
<span data-ttu-id="27009-104">Cria uma conexão por meio do DCOM para um namespace do WMI em um computador especificado.</span><span class="sxs-lookup"><span data-stu-id="27009-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="27009-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27009-105">Syntax</span></span>  
  
```  
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```  
## <a name="parameters"></a><span data-ttu-id="27009-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27009-106">Parameters</span></span>

<span data-ttu-id="27009-107">`strNetworkResource` [in] Ponteiro para um válido `BSTR` que contém o caminho do objeto do namespace WMI correto.</span><span class="sxs-lookup"><span data-stu-id="27009-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="27009-108">Consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="27009-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="27009-109">`strUser` [in] Um ponteiro para um válido `BSTR` que contém o nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="27009-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="27009-110">Um `null` valor indica o contexto de segurança atual.</span><span class="sxs-lookup"><span data-stu-id="27009-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="27009-111">Se o usuário for de um domínio diferente daquele atual, `strUser` também pode conter o nome de usuário e domínio separados por uma barra invertida.</span><span class="sxs-lookup"><span data-stu-id="27009-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="27009-112">`strUser` também pode ser usuário nome principal (UPN) Formatar, suhc como *userName@domainName*.</span><span class="sxs-lookup"><span data-stu-id="27009-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="27009-113">Consulte a [comentários](#remarks) seção para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="27009-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="27009-114">`strPassword` [in] Um ponteiro para um válido `BSTR` que contém a senha.</span><span class="sxs-lookup"><span data-stu-id="27009-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="27009-115">Um `null` indica o contexto de segurança atual.</span><span class="sxs-lookup"><span data-stu-id="27009-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="27009-116">Uma cadeia de caracteres vazia ("") indica uma senha válida de comprimento zero.</span><span class="sxs-lookup"><span data-stu-id="27009-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="27009-117">`strLocale` [in] Um ponteiro para um válido `BSTR` que indica a localidade correta para a recuperação de informações.</span><span class="sxs-lookup"><span data-stu-id="27009-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="27009-118">Identificadores de localidade da Microsoft, o formato da cadeia de caracteres é "MS\_*xxx*", onde *xxx* é uma cadeia de caracteres em formato hexadecimal que indica o identificador de localidade (LCID).</span><span class="sxs-lookup"><span data-stu-id="27009-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="27009-119">Se um local inválido for especificado, o método retorna `WBEM_E_INVALID_PARAMETER` exceto no Windows 7, em que a localidade padrão do servidor é usada em vez disso.</span><span class="sxs-lookup"><span data-stu-id="27009-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="27009-120">Se ' null1, a localidade atual é usado.</span><span class="sxs-lookup"><span data-stu-id="27009-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="27009-121">`lSecurityFlags` [in] Sinalizadores a serem passados para o `ConnectServerWmi` método.</span><span class="sxs-lookup"><span data-stu-id="27009-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="27009-122">Um valor de zero (0) para esse parâmetro resulta na chamada para `ConnectServerWmi` retornando somente após o estabelecimento de uma conexão ao servidor.</span><span class="sxs-lookup"><span data-stu-id="27009-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="27009-123">Isso pode resultar em um aplicativo não está respondendo indefinidamente se o servidor será interrompido.</span><span class="sxs-lookup"><span data-stu-id="27009-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="27009-124">Os outros valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="27009-124">The other valid values are:</span></span>

| <span data-ttu-id="27009-125">Constante</span><span class="sxs-lookup"><span data-stu-id="27009-125">Constant</span></span>  | <span data-ttu-id="27009-126">Valor</span><span class="sxs-lookup"><span data-stu-id="27009-126">Value</span></span>  | <span data-ttu-id="27009-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="27009-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="27009-128">0x40</span><span class="sxs-lookup"><span data-stu-id="27009-128">0x40</span></span> | <span data-ttu-id="27009-129">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="27009-129">Reserved for internal use.</span></span> <span data-ttu-id="27009-130">Não use.</span><span class="sxs-lookup"><span data-stu-id="27009-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="27009-131">0x80</span><span class="sxs-lookup"><span data-stu-id="27009-131">0x80</span></span> | <span data-ttu-id="27009-132">`ConnectServerWmi` Retorna em dois minutos ou menos.</span><span class="sxs-lookup"><span data-stu-id="27009-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="27009-133">`strAuthority` [in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="27009-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="27009-134">Ele pode ter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="27009-134">It can have the following values:</span></span>

| <span data-ttu-id="27009-135">Valor</span><span class="sxs-lookup"><span data-stu-id="27009-135">Value</span></span> | <span data-ttu-id="27009-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="27009-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="27009-137">em branco</span><span class="sxs-lookup"><span data-stu-id="27009-137">blank</span></span> | <span data-ttu-id="27009-138">A autenticação NTLM é usada e o domínio NTLM do usuário atual será usado.</span><span class="sxs-lookup"><span data-stu-id="27009-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="27009-139">Se `strUser` Especifica o domínio (o local recomendado), ele não deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="27009-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="27009-140">A função retorna `WBEM_E_INVALID_PARAMETER` se você especificar o domínio em ambos os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="27009-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="27009-141">Kerberos:*nome da entidade*</span><span class="sxs-lookup"><span data-stu-id="27009-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="27009-142">A autenticação Kerberos é usada, e este parâmetro contém um nome principal Kerberos.</span><span class="sxs-lookup"><span data-stu-id="27009-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="27009-143">NTLMDOMAIN:*nome de domínio*</span><span class="sxs-lookup"><span data-stu-id="27009-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="27009-144">Autenticação NT LAN Manager é usada, e este parâmetro contém um nome de domínio do NTLM.</span><span class="sxs-lookup"><span data-stu-id="27009-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="27009-145">[in] Normalmente, esse parâmetro é é `null`.</span><span class="sxs-lookup"><span data-stu-id="27009-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="27009-146">Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) objeto exigido por um ou mais provedores de classe dinâmica.</span><span class="sxs-lookup"><span data-stu-id="27009-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="27009-147">[out] Quando a função retornar, recebe um ponteiro para um [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto associado ao namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="27009-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="27009-148">Ele é definido para apontar para `null` quando ocorre um erro.</span><span class="sxs-lookup"><span data-stu-id="27009-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="27009-149">[in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="27009-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="27009-150">[in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="27009-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="27009-151">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="27009-151">Return value</span></span>

<span data-ttu-id="27009-152">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="27009-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="27009-153">Constante</span><span class="sxs-lookup"><span data-stu-id="27009-153">Constant</span></span>  |<span data-ttu-id="27009-154">Valor</span><span class="sxs-lookup"><span data-stu-id="27009-154">Value</span></span>  |<span data-ttu-id="27009-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="27009-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="27009-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="27009-156">0x80041001</span></span> | <span data-ttu-id="27009-157">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="27009-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="27009-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="27009-158">0x80041008</span></span> | <span data-ttu-id="27009-159">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="27009-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="27009-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="27009-160">0x80041006</span></span> | <span data-ttu-id="27009-161">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="27009-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="27009-162">0</span><span class="sxs-lookup"><span data-stu-id="27009-162">0</span></span> | <span data-ttu-id="27009-163">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="27009-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="27009-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="27009-164">Remarks</span></span>

<span data-ttu-id="27009-165">Essa função encapsula uma chamada para o [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) método.</span><span class="sxs-lookup"><span data-stu-id="27009-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="27009-166">Para acesso local para o namespace padrão, `strNetworkResource` pode ser um caminho de objeto simples: "root\default" ou "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="27009-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="27009-167">Para acessar o namespace padrão em um computador remoto usando a rede COM ou compatível com a Microsoft, que incluem o nome do computador: "\\myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="27009-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="27009-168">O nome do computador também pode ser um nome DNS ou endereço IP.</span><span class="sxs-lookup"><span data-stu-id="27009-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="27009-169">O `ConnectServerWmi` função também pode se conectar com computadores que executam o IPv6 usando um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="27009-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="27009-170">`strUser` não pode ser uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="27009-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="27009-171">Se o domínio é especificado na `strAuthority`, ela também não deve ser incluída no `strUser`, ou a função retornará `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="27009-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="27009-172">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27009-172">Requirements</span></span>  
 <span data-ttu-id="27009-173">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27009-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27009-174">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="27009-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="27009-175">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="27009-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27009-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27009-176">See also</span></span>  
[<span data-ttu-id="27009-177">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="27009-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
