---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 2376a0ec25539b97a37b1827e3e4c148eb8d5838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610767"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="178ec-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="178ec-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="178ec-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="178ec-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="178ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="178ec-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="178ec-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="178ec-105">Methods</span></span>  
 <span data-ttu-id="178ec-106">A classe HttpTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="178ec-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="178ec-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="178ec-107">Properties</span></span>  
 <span data-ttu-id="178ec-108">A classe HttpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="178ec-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="178ec-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="178ec-109">AllowCookies</span></span>  
 <span data-ttu-id="178ec-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="178ec-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="178ec-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-112">Um valor que indica se o cliente aceita cookies e propaga-os em solicitações futuras.</span><span class="sxs-lookup"><span data-stu-id="178ec-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="178ec-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="178ec-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="178ec-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="178ec-114">Data type: string</span></span>  
  
 <span data-ttu-id="178ec-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-116">O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um ouvinte HTTP.</span><span class="sxs-lookup"><span data-stu-id="178ec-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="178ec-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="178ec-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="178ec-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="178ec-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="178ec-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-120">Um valor que indica se os proxies são ignorados para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="178ec-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="178ec-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="178ec-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="178ec-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="178ec-122">Data type: string</span></span>  
  
 <span data-ttu-id="178ec-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-124">Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="178ec-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="178ec-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="178ec-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="178ec-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="178ec-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="178ec-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-128">Quando habilitada, as conexões HTTP são mantidas ativos, independentemente do nível de atividade.</span><span class="sxs-lookup"><span data-stu-id="178ec-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="178ec-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="178ec-129">MaxBufferSize</span></span>  
 <span data-ttu-id="178ec-130">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="178ec-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="178ec-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-132">O tamanho máximo do pool de buffers.</span><span class="sxs-lookup"><span data-stu-id="178ec-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="178ec-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="178ec-133">ProxyAddress</span></span>  
 <span data-ttu-id="178ec-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="178ec-134">Data type: string</span></span>  
  
 <span data-ttu-id="178ec-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-136">Um URI que contém o endereço do proxy a ser usado para solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="178ec-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="178ec-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="178ec-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="178ec-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="178ec-138">Data type: string</span></span>  
  
 <span data-ttu-id="178ec-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-140">O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="178ec-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="178ec-141">território</span><span class="sxs-lookup"><span data-stu-id="178ec-141">Realm</span></span>  
 <span data-ttu-id="178ec-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="178ec-142">Data type: string</span></span>  
  
 <span data-ttu-id="178ec-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-144">O realm de autenticação.</span><span class="sxs-lookup"><span data-stu-id="178ec-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="178ec-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="178ec-145">TransferMode</span></span>  
 <span data-ttu-id="178ec-146">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="178ec-146">Data type: string</span></span>  
  
 <span data-ttu-id="178ec-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-148">Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.</span><span class="sxs-lookup"><span data-stu-id="178ec-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="178ec-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="178ec-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="178ec-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="178ec-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="178ec-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-152">Um valor que indica se o compartilhamento de Conexão não segura está habilitada no servidor.</span><span class="sxs-lookup"><span data-stu-id="178ec-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="178ec-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="178ec-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="178ec-154">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="178ec-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="178ec-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="178ec-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="178ec-156">Um valor que indica se as configurações de proxy de todo o computador são usadas em vez de configurações específicas do usuário.</span><span class="sxs-lookup"><span data-stu-id="178ec-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="178ec-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="178ec-157">Requirements</span></span>  
  
|<span data-ttu-id="178ec-158">MOF</span><span class="sxs-lookup"><span data-stu-id="178ec-158">MOF</span></span>|<span data-ttu-id="178ec-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="178ec-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="178ec-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="178ec-160">Namespace</span></span>|<span data-ttu-id="178ec-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="178ec-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="178ec-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="178ec-162">See also</span></span>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
