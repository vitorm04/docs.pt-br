---
title: "Detecção automática de proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
caps.latest.revision: 18
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f0c1a0d462768229c730f06a6514d040a3e5c1c
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="939ac-102">Detecção automática de proxy</span><span class="sxs-lookup"><span data-stu-id="939ac-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="939ac-103">A detecção automática de proxy é um processo pelo qual um servidor proxy Web é identificado pelo sistema e usado para enviar solicitações em nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="939ac-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="939ac-104">Esse recurso também é conhecido como WPAD (Descoberta Automática de Proxy Web).</span><span class="sxs-lookup"><span data-stu-id="939ac-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="939ac-105">Quando a detecção automática de proxy está habilitada, o sistema tenta localizar um script de configuração de proxy que é responsável por retornar o conjunto de proxies que pode ser usado para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="939ac-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="939ac-106">Se o script de configuração de proxy for encontrado, o script será baixado, compilado e executado no computador local quando as informações de proxy, o fluxo da solicitação ou a resposta for obtida de uma solicitação que usa uma instância <xref:System.Net.WebProxy>.</span><span class="sxs-lookup"><span data-stu-id="939ac-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="939ac-107">A detecção automática de proxy é executada pela classe <xref:System.Net.WebProxy> e pode utilizar configurações no nível da solicitação, configurações nos arquivos de configuração e as configurações especificadas usando a caixa de diálogo **Rede Local (LAN)** do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="939ac-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="939ac-108">Exiba a caixa de diálogo **Configurações da Rede Local (LAN)** do Internet Explorer selecionando **Ferramentas** no menu principal do Internet Explorer e, em seguida, selecionando **Opções da Internet**.</span><span class="sxs-lookup"><span data-stu-id="939ac-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="939ac-109">Em seguida, selecione a guia **Conexões** e, em seguida, clique em **Configurações de LAN**.</span><span class="sxs-lookup"><span data-stu-id="939ac-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="939ac-110">Quando a detecção automática de proxy está habilitada, a classe <xref:System.Net.WebProxy> tenta localizar o script de configuração de proxy da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="939ac-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="939ac-111">A função `InternetQueryOption` de WinINet é usada para localizar o script de configuração de proxy detectado mais recentemente pelo Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="939ac-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="939ac-112">Se o script não for localizado, a classe <xref:System.Net.WebProxy> usará o protocolo DHCP para localizar o script.</span><span class="sxs-lookup"><span data-stu-id="939ac-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="939ac-113">O servidor DHCP pode responder com o local (nome do host) do script ou com a URL completa do script.</span><span class="sxs-lookup"><span data-stu-id="939ac-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="939ac-114">Se o DHCP não identificar o host do WPAD, o DNS será consultado em busca de um host com o WPAD como seu nome ou alias.</span><span class="sxs-lookup"><span data-stu-id="939ac-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="939ac-115">Se o host não for identificado e o local de um script de configuração de proxy for especificado pelas configurações de LAN do Internet Explorer ou por um arquivo de configuração, esse local será usado.</span><span class="sxs-lookup"><span data-stu-id="939ac-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="939ac-116">Os aplicativos em execução como um Serviço NT ou como parte do ASP.NET usam as configurações do servidor proxy do Internet Explorer (se disponíveis) do usuário que faz a invocação.</span><span class="sxs-lookup"><span data-stu-id="939ac-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="939ac-117">Essas configurações podem não estar disponíveis para todos os aplicativos de serviço.</span><span class="sxs-lookup"><span data-stu-id="939ac-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="939ac-118">Os proxies são configurados por conectoide.</span><span class="sxs-lookup"><span data-stu-id="939ac-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="939ac-119">Uma conectoide é um item da caixa de diálogo de conexão de rede e pode ser um dispositivo de rede físico (um modem ou uma placa Ethernet) ou uma interface virtual (como uma conexão VPN em execução em um dispositivo de rede).</span><span class="sxs-lookup"><span data-stu-id="939ac-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="939ac-120">Quando um conectoide é alterado (por exemplo, uma conexão sem fio altera um ponto de acesso ou uma VPN é habilitada), o algoritmo de detecção de proxy é executado novamente.</span><span class="sxs-lookup"><span data-stu-id="939ac-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="939ac-121">Por padrão, as configurações de proxy do Internet Explorer são usadas para detectar o proxy.</span><span class="sxs-lookup"><span data-stu-id="939ac-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="939ac-122">Se o aplicativo estiver sendo executado em uma conta não interativa (sem uma maneira conveniente de definir as configurações de proxy do IE) ou se você desejar usar configurações de proxy diferentes das configurações do IE, configure o proxy criando um arquivo de configuração com o Elemento [\<defaultProxy> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) e o Elemento [\<proxy> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) definidos.</span><span class="sxs-lookup"><span data-stu-id="939ac-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="939ac-123">Para as solicitações criadas por você, desabilite a detecção automática de proxy no nível da solicitação usando um <xref:System.Net.WebRequest.Proxy%2A> nulo com a solicitação, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="939ac-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 <span data-ttu-id="939ac-124">As solicitações que não têm um proxy usam o proxy padrão do domínio do aplicativo, que está disponível na propriedade <xref:System.Net.WebRequest.DefaultWebProxy%2A>.</span><span class="sxs-lookup"><span data-stu-id="939ac-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939ac-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="939ac-125">See Also</span></span>  
 <span data-ttu-id="939ac-126"><xref:System.Net.WebProxy></span><span class="sxs-lookup"><span data-stu-id="939ac-126"><xref:System.Net.WebProxy></span></span>   
 <span data-ttu-id="939ac-127"><xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="939ac-127"><xref:System.Net.WebRequest></span></span>   
 <span data-ttu-id="939ac-128">Elemento [\<system.Net> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="939ac-128">[\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)</span></span>

