---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 34ad4b8534d082d7f5248d42d70ca5bd0647a5dc
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454311"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="c1d98-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c1d98-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="c1d98-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c1d98-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1d98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1d98-104">Syntax</span></span>  
  
```csharp
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c1d98-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c1d98-105">Methods</span></span>  
 <span data-ttu-id="c1d98-106">A classe HttpTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="c1d98-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c1d98-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c1d98-107">Properties</span></span>  
 <span data-ttu-id="c1d98-108">A classe HttpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c1d98-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="c1d98-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="c1d98-109">AllowCookies</span></span>  
 <span data-ttu-id="c1d98-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c1d98-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1d98-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-112">Um valor que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="c1d98-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="c1d98-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="c1d98-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="c1d98-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c1d98-114">Data type: string</span></span>  
  
 <span data-ttu-id="c1d98-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-116">O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um ouvinte HTTP.</span><span class="sxs-lookup"><span data-stu-id="c1d98-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="c1d98-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="c1d98-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="c1d98-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c1d98-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1d98-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-120">Um valor que indica se os proxies são ignorados para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="c1d98-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="c1d98-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c1d98-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="c1d98-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c1d98-122">Data type: string</span></span>  
  
 <span data-ttu-id="c1d98-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-124">Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="c1d98-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="c1d98-125">keepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="c1d98-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="c1d98-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c1d98-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1d98-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-128">Quando habilitada, as conexões HTTP são mantidas ativos, independentemente do nível de atividade.</span><span class="sxs-lookup"><span data-stu-id="c1d98-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="c1d98-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c1d98-129">MaxBufferSize</span></span>  
 <span data-ttu-id="c1d98-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c1d98-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="c1d98-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-132">O tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="c1d98-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="c1d98-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="c1d98-133">ProxyAddress</span></span>  
 <span data-ttu-id="c1d98-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c1d98-134">Data type: string</span></span>  
  
 <span data-ttu-id="c1d98-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-136">Um URI que contém o endereço do proxy a ser usado para solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="c1d98-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="c1d98-137">proxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="c1d98-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="c1d98-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c1d98-138">Data type: string</span></span>  
  
 <span data-ttu-id="c1d98-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-140">O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="c1d98-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="c1d98-141">território</span><span class="sxs-lookup"><span data-stu-id="c1d98-141">Realm</span></span>  
 <span data-ttu-id="c1d98-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c1d98-142">Data type: string</span></span>  
  
 <span data-ttu-id="c1d98-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-144">O realm de autenticação.</span><span class="sxs-lookup"><span data-stu-id="c1d98-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="c1d98-145">transferMode</span><span class="sxs-lookup"><span data-stu-id="c1d98-145">TransferMode</span></span>  
 <span data-ttu-id="c1d98-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c1d98-146">Data type: string</span></span>  
  
 <span data-ttu-id="c1d98-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-148">Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="c1d98-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="c1d98-149">unsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="c1d98-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="c1d98-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c1d98-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1d98-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-152">Um valor que indica se o compartilhamento de Conexão não segura está habilitada no servidor.</span><span class="sxs-lookup"><span data-stu-id="c1d98-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="c1d98-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="c1d98-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="c1d98-154">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c1d98-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1d98-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c1d98-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1d98-156">Um valor que indica se as configurações de proxy de todo o computador são usadas em vez de configurações específicas do usuário.</span><span class="sxs-lookup"><span data-stu-id="c1d98-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1d98-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1d98-157">Requirements</span></span>  
  
|<span data-ttu-id="c1d98-158">MOF</span><span class="sxs-lookup"><span data-stu-id="c1d98-158">MOF</span></span>|<span data-ttu-id="c1d98-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c1d98-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c1d98-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="c1d98-160">Namespace</span></span>|<span data-ttu-id="c1d98-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c1d98-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1d98-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1d98-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
