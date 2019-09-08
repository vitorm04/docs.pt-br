---
title: Função ConnectServerWmi (referência de API não gerenciada)
description: A função ConnectServerWmi usa DCOM para criar uma conexão com um namespace WMI.
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
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798747"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="c1b3c-103">Função ConnectServerWmi</span><span class="sxs-lookup"><span data-stu-id="c1b3c-103">ConnectServerWmi function</span></span>

<span data-ttu-id="c1b3c-104">Cria uma conexão por meio do DCOM para um namespace do WMI em um computador especificado.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c1b3c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1b3c-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="c1b3c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1b3c-106">Parameters</span></span>

`strNetworkResource`\
<span data-ttu-id="c1b3c-107">no Ponteiro para um válido `BSTR` que contém o caminho do objeto do namespace WMI correto.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-107">[in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="c1b3c-108">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-108">See the [Remarks](#remarks) section for more information.</span></span>

`strUser`\
<span data-ttu-id="c1b3c-109">no Um ponteiro para um válido `BSTR` que contém o nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-109">[in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="c1b3c-110">Um `null` valor indica o contexto de segurança atual.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="c1b3c-111">Se o usuário for de um domínio diferente do atual, `strUser` também poderá conter o domínio e o nome de usuário separados por uma barra invertida.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="c1b3c-112">`strUser`também pode ser no formato UPN (nome principal do usuário), `userName@domainName`como.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-112">`strUser` can also be in user principal name (UPN) format, such as `userName@domainName`.</span></span> <span data-ttu-id="c1b3c-113">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-113">See the [Remarks](#remarks) section for more information.</span></span>

`strPassword`\
<span data-ttu-id="c1b3c-114">no Um ponteiro para um válido `BSTR` que contém a senha.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-114">[in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="c1b3c-115">Um `null` indica o contexto de segurança atual.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="c1b3c-116">Uma cadeia de caracteres vazia ("") indica uma senha de comprimento zero válida.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-116">An empty string ("") indicates a valid zero-length password.</span></span>

`strLocale`\
<span data-ttu-id="c1b3c-117">no Um ponteiro para um válido `BSTR` que indica a localidade correta para a recuperação de informações.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-117">[in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="c1b3c-118">Para identificadores de localidade da Microsoft, o formato da cadeia de caracteres\_é "MS*xxx*", em que *xxx* é uma cadeia de caracteres no formato hexadecimal que indica o LCID (identificador de localidade).</span><span class="sxs-lookup"><span data-stu-id="c1b3c-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="c1b3c-119">Se uma localidade inválida for especificada, o método `WBEM_E_INVALID_PARAMETER` retornará, exceto no Windows 7, em que a localidade padrão do servidor será usada.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="c1b3c-120">Se ' null1 ', a localidade atual será usada.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-120">If \`null1, the current locale is used.</span></span>

`lSecurityFlags`\
<span data-ttu-id="c1b3c-121">no Sinalizadores a serem passados para `ConnectServerWmi` o método.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-121">[in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="c1b3c-122">Um valor de zero (0) para esse parâmetro resulta na chamada para `ConnectServerWmi` retornar somente depois que uma conexão com o servidor é estabelecida.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="c1b3c-123">Isso pode resultar em um aplicativo não respondendo indefinidamente se o servidor estiver interrompido.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="c1b3c-124">Os outros valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="c1b3c-124">The other valid values are:</span></span>

| <span data-ttu-id="c1b3c-125">Constante</span><span class="sxs-lookup"><span data-stu-id="c1b3c-125">Constant</span></span>  | <span data-ttu-id="c1b3c-126">Valor</span><span class="sxs-lookup"><span data-stu-id="c1b3c-126">Value</span></span>  | <span data-ttu-id="c1b3c-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1b3c-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="c1b3c-128">0x40</span><span class="sxs-lookup"><span data-stu-id="c1b3c-128">0x40</span></span> | <span data-ttu-id="c1b3c-129">Reservado para uso interno.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-129">Reserved for internal use.</span></span> <span data-ttu-id="c1b3c-130">Não use.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="c1b3c-131">0x80</span><span class="sxs-lookup"><span data-stu-id="c1b3c-131">0x80</span></span> | <span data-ttu-id="c1b3c-132">`ConnectServerWmi`retorna em dois minutos ou menos.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

`strAuthority`\
<span data-ttu-id="c1b3c-133">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-133">[in] The domain name of the user.</span></span> <span data-ttu-id="c1b3c-134">Ele pode ter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c1b3c-134">It can have the following values:</span></span>

| <span data-ttu-id="c1b3c-135">Valor</span><span class="sxs-lookup"><span data-stu-id="c1b3c-135">Value</span></span> | <span data-ttu-id="c1b3c-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1b3c-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="c1b3c-137">ficará</span><span class="sxs-lookup"><span data-stu-id="c1b3c-137">blank</span></span> | <span data-ttu-id="c1b3c-138">A autenticação NTLM é usada e o domínio NTLM do usuário atual é usado.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="c1b3c-139">Se `strUser` especifica o domínio (o local recomendado), ele não deve ser especificado aqui.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="c1b3c-140">A função retornará `WBEM_E_INVALID_PARAMETER` se você especificar o domínio em ambos os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="c1b3c-141">Kerberos:*nome da entidade*</span><span class="sxs-lookup"><span data-stu-id="c1b3c-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="c1b3c-142">A autenticação Kerberos é usada e esse parâmetro contém um nome de entidade de segurança Kerberos.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="c1b3c-143">NTLMDOMAIN:*nome de domínio*</span><span class="sxs-lookup"><span data-stu-id="c1b3c-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="c1b3c-144">A autenticação do Gerenciador de LAN do NT é usada e esse parâmetro contém um nome de domínio NTLM.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`\
<span data-ttu-id="c1b3c-145">no Normalmente, esse parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-145">[in] Typically, this parameter is `null`.</span></span> <span data-ttu-id="c1b3c-146">Caso contrário, é um ponteiro para um objeto [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) exigido por um ou mais provedores de classe dinâmica.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span>

`ppNamespace`\
<span data-ttu-id="c1b3c-147">fora Quando a função retorna, recebe um ponteiro para um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) associado ao namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="c1b3c-148">Ele é definido para apontar para `null` quando há um erro.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`\
<span data-ttu-id="c1b3c-149">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-149">[in] The impersonation level.</span></span>

`authLevel`\
<span data-ttu-id="c1b3c-150">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="c1b3c-151">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c1b3c-151">Return value</span></span>

<span data-ttu-id="c1b3c-152">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c1b3c-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c1b3c-153">Constante</span><span class="sxs-lookup"><span data-stu-id="c1b3c-153">Constant</span></span>  |<span data-ttu-id="c1b3c-154">Valor</span><span class="sxs-lookup"><span data-stu-id="c1b3c-154">Value</span></span>  |<span data-ttu-id="c1b3c-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1b3c-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="c1b3c-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c1b3c-156">0x80041001</span></span> | <span data-ttu-id="c1b3c-157">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c1b3c-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c1b3c-158">0x80041008</span></span> | <span data-ttu-id="c1b3c-159">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c1b3c-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c1b3c-160">0x80041006</span></span> | <span data-ttu-id="c1b3c-161">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c1b3c-162">0</span><span class="sxs-lookup"><span data-stu-id="c1b3c-162">0</span></span> | <span data-ttu-id="c1b3c-163">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c1b3c-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1b3c-164">Remarks</span></span>

<span data-ttu-id="c1b3c-165">Essa função encapsula uma chamada para o método [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .</span><span class="sxs-lookup"><span data-stu-id="c1b3c-165">This function wraps a call to the [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) method.</span></span>

<span data-ttu-id="c1b3c-166">Para acesso local ao namespace padrão, `strNetworkResource` pode ser um caminho de objeto simples: "root\default" ou "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="c1b3c-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="c1b3c-167">Para acessar o namespace padrão em um computador remoto usando a rede compatível com ou com a Microsoft, inclua o nome do computador\\: "myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="c1b3c-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="c1b3c-168">O nome do computador também pode ser um nome DNS ou endereço IP.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="c1b3c-169">A `ConnectServerWmi` função também pode se conectar a computadores que executam o IPv6 usando um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="c1b3c-170">`strUser`Não pode ser uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="c1b3c-171">Se o domínio for especificado em `strAuthority`, ele também não deverá ser incluído no `strUser`, ou a função retornará `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="c1b3c-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c1b3c-172">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1b3c-172">Requirements</span></span>

 <span data-ttu-id="c1b3c-173">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b3c-173">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="c1b3c-174">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c1b3c-174">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="c1b3c-175">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b3c-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c1b3c-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1b3c-176">See also</span></span>

- [<span data-ttu-id="c1b3c-177">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c1b3c-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
