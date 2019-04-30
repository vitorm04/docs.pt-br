---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 5e23342d57621554aaec67c5c568bb75202a9454
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963482"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="80876-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="80876-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="80876-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="80876-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80876-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80876-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="80876-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="80876-105">Methods</span></span>  
 <span data-ttu-id="80876-106">A classe HttpTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="80876-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="80876-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="80876-107">Properties</span></span>  
 <span data-ttu-id="80876-108">A classe HttpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="80876-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="80876-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="80876-109">AllowCookies</span></span>  
 <span data-ttu-id="80876-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="80876-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="80876-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-112">Um valor que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="80876-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="80876-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="80876-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="80876-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80876-114">Data type: string</span></span>  
  
 <span data-ttu-id="80876-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-116">O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um ouvinte HTTP.</span><span class="sxs-lookup"><span data-stu-id="80876-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="80876-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="80876-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="80876-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="80876-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="80876-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-120">Um valor que indica se os proxies são ignorados para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="80876-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="80876-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="80876-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="80876-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80876-122">Data type: string</span></span>  
  
 <span data-ttu-id="80876-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-124">Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="80876-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="80876-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="80876-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="80876-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="80876-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="80876-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-128">Quando habilitada, as conexões HTTP são mantidas ativos, independentemente do nível de atividade.</span><span class="sxs-lookup"><span data-stu-id="80876-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="80876-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="80876-129">MaxBufferSize</span></span>  
 <span data-ttu-id="80876-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="80876-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="80876-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-132">O tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="80876-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="80876-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="80876-133">ProxyAddress</span></span>  
 <span data-ttu-id="80876-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80876-134">Data type: string</span></span>  
  
 <span data-ttu-id="80876-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-136">Um URI que contém o endereço do proxy a ser usado para solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="80876-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="80876-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="80876-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="80876-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80876-138">Data type: string</span></span>  
  
 <span data-ttu-id="80876-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-140">O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="80876-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="80876-141">território</span><span class="sxs-lookup"><span data-stu-id="80876-141">Realm</span></span>  
 <span data-ttu-id="80876-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80876-142">Data type: string</span></span>  
  
 <span data-ttu-id="80876-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-144">O realm de autenticação.</span><span class="sxs-lookup"><span data-stu-id="80876-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="80876-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="80876-145">TransferMode</span></span>  
 <span data-ttu-id="80876-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80876-146">Data type: string</span></span>  
  
 <span data-ttu-id="80876-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-148">Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="80876-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="80876-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="80876-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="80876-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="80876-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="80876-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-152">Um valor que indica se o compartilhamento de Conexão não segura está habilitada no servidor.</span><span class="sxs-lookup"><span data-stu-id="80876-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="80876-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="80876-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="80876-154">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="80876-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="80876-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80876-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80876-156">Um valor que indica se as configurações de proxy de todo o computador são usadas em vez de configurações específicas do usuário.</span><span class="sxs-lookup"><span data-stu-id="80876-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80876-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80876-157">Requirements</span></span>  
  
|<span data-ttu-id="80876-158">MOF</span><span class="sxs-lookup"><span data-stu-id="80876-158">MOF</span></span>|<span data-ttu-id="80876-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="80876-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="80876-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="80876-160">Namespace</span></span>|<span data-ttu-id="80876-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="80876-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80876-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80876-162">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
