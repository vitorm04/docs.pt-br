---
title: "Configuração de proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 41f7cfe76acfb4b6bbf66207685935c190a51901
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="proxy-configuration"></a><span data-ttu-id="ac5b2-102">Configuração de proxy</span><span class="sxs-lookup"><span data-stu-id="ac5b2-102">Proxy Configuration</span></span>
<span data-ttu-id="ac5b2-103">Um servidor proxy manipula as solicitações de clientes para recursos.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="ac5b2-104">Um proxy pode retornar um recurso solicitado do seu cache ou encaminhar a solicitação para o servidor na qual o recurso reside.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="ac5b2-105">Proxies podem melhorar o desempenho da rede, reduzindo o número de solicitações enviadas a servidores remotos.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="ac5b2-106">Proxies também podem ser usados para restringir o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="ac5b2-107">Proxies adaptáveis</span><span class="sxs-lookup"><span data-stu-id="ac5b2-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="ac5b2-108">No .NET Framework, os proxies existem em duas variedades: adaptáveis e estáticos.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="ac5b2-109">Proxies adaptáveis ajustam suas configurações quando as configurações de rede são alteradas.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="ac5b2-110">Por exemplo, se um usuário de laptop inicia uma conexão de rede dial-up, um proxy adaptável reconheceria essa alteração, descobrir e executaria seu novo script de configuração e ajustaria suas configurações adequadamente.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="ac5b2-111">Proxies adaptáveis são configurados por um script de configuração (consulte [Detecção automática de proxy](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="ac5b2-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="ac5b2-112">O script gera um conjunto de protocolos de aplicativo e um proxy para cada protocolo.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="ac5b2-113">Várias opções de controlam a maneira como o script de configuração é executado.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-113">Several options control how the configuration script is run.</span></span> <span data-ttu-id="ac5b2-114">Você pode especificar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ac5b2-114">You can specify the following:</span></span>  
  
-   <span data-ttu-id="ac5b2-115">A frequência com que o script de configuração é baixado e executado.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-115">How often the configuration script is downloaded and run.</span></span>  
  
-   <span data-ttu-id="ac5b2-116">Tempo de espera para o download do script.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-116">How long to wait for the script to download.</span></span>  
  
-   <span data-ttu-id="ac5b2-117">Quais credenciais seu sistema deve usar para acessar o proxy.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-117">Which credentials your system should use to access the proxy.</span></span>  
  
-   <span data-ttu-id="ac5b2-118">Quais credenciais seu sistema deve usar para baixar o script de configuração.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-118">Which credentials your system should use to download the configuration script.</span></span>  
  
 <span data-ttu-id="ac5b2-119">Alterações no ambiente de rede podem exigir que o sistema use um novo conjunto de proxies.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-119">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="ac5b2-120">Se uma conexão de rede ficar inoperante ou uma nova conexão de rede for inicializada, o sistema deve descobrir a origem correta do script de configuração no novo ambiente e executar o novo script.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-120">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="ac5b2-121">A tabela a seguir mostra as opções de configuração para um proxy adaptável.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-121">The following table shows configuration options for an adaptive proxy.</span></span>  
  
|<span data-ttu-id="ac5b2-122">Definição do arquivo de configuração, propriedade ou atributo</span><span class="sxs-lookup"><span data-stu-id="ac5b2-122">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="ac5b2-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac5b2-123">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|<span data-ttu-id="ac5b2-124">Tempo decorrido em segundos entre downloads de script.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-124">Elapsed time in seconds between script downloads.</span></span>|  
|`scriptDownloadTimeout`|<span data-ttu-id="ac5b2-125">Tempo de espera (em segundos) para baixar o script.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-125">Time to wait (in seconds) for the script to download.</span></span>|  
|<span data-ttu-id="ac5b2-126">`useDefaultCredentials` ou <xref:System.Net.WebProxy.UseDefaultCredentials></span><span class="sxs-lookup"><span data-stu-id="ac5b2-126">`useDefaultCredentials` or <xref:System.Net.WebProxy.UseDefaultCredentials></span></span>|<span data-ttu-id="ac5b2-127">Controla se o sistema usa as credenciais de rede padrão para acessar um proxy.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-127">Controls whether the system uses the default network credentials to access a proxy.</span></span>|  
|`useDefaultCredentialForScriptDownload`|<span data-ttu-id="ac5b2-128">Controla se o sistema usa as credenciais de rede padrão para baixar o script de configuração.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-128">Controls whether the system uses the default network credentials to download the configuration script.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="ac5b2-129">Controla se as configurações de proxy estático (endereço de proxy, lista de ignoráveis e ignorar no local) devem ser lido das configurações de proxy do Internet Explorer para o usuário.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-129">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="ac5b2-130">Se esse valor for definido como "true", as configurações de proxy estático do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-130">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span><br /><br /> <span data-ttu-id="ac5b2-131">Se esse valor for "false" ou se não estiver definido, as configurações de proxy estático podem ser especificadas na configuração e substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-131">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="ac5b2-132">Esse valor também deve ser definido como "false" ou não estar configurado para habilitar proxies adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-132">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="ac5b2-133">O exemplo a seguir mostra uma configuração de proxy adaptável típica.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-133">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="ac5b2-134">Proxies estáticos</span><span class="sxs-lookup"><span data-stu-id="ac5b2-134">Static Proxies</span></span>  
 <span data-ttu-id="ac5b2-135">Proxies estáticos geralmente são configurados explicitamente por um aplicativo ou quando um arquivo de configuração é invocado por um aplicativo ou pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-135">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="ac5b2-136">Proxies estáticos são úteis em redes em que a topologia é alterada com frequência, como um computador desktop conectado a uma rede corporativa.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-136">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="ac5b2-137">Várias opções de controlam como um proxy estático funciona.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-137">Several options control how a static proxy operates.</span></span> <span data-ttu-id="ac5b2-138">Você pode especificar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ac5b2-138">You can specify the following:</span></span>  
  
-   <span data-ttu-id="ac5b2-139">O endereço do proxy.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-139">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="ac5b2-140">Se o proxy deve ou não ser ignorado para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-140">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="ac5b2-141">Se o proxy deve ou não ser ignorado para um conjunto de endereços.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-141">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="ac5b2-142">A tabela a seguir mostra as opções de configuração para um proxy estático.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-142">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="ac5b2-143">Definição do arquivo de configuração, propriedade ou atributo</span><span class="sxs-lookup"><span data-stu-id="ac5b2-143">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="ac5b2-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac5b2-144">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="ac5b2-145">`proxyaddress` ou <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="ac5b2-145">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="ac5b2-146">O endereço do proxy a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-146">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="ac5b2-147">`bypassonlocal` ou <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="ac5b2-147">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="ac5b2-148">Controla se o proxy é ignorado para endereços locais.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-148">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="ac5b2-149">`bypasslist` ou <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="ac5b2-149">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="ac5b2-150">Descreve, com expressões regulares, um conjunto de endereços que ignora o proxy.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-150">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="ac5b2-151">Controla se as configurações de proxy estático (endereço de proxy, lista de ignoráveis e ignorar no local) devem ser lido das configurações de proxy do Internet Explorer para o usuário.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-151">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="ac5b2-152">Se esse valor for definido como "true", as configurações de proxy estático do Internet Explorer serão usadas.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-152">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="ac5b2-153">No .NET Framework 2.0, quando esse valor é definido como "true", as configurações de proxy do Internet Explorer não são substituídas por outras configurações de proxy no arquivo de configurações.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-153">On .NET Framework 2.0 when this value is set to "true", the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="ac5b2-154">No .NET Framework 1.1, as configurações de proxy do Internet Explorer podem ser substituídas por outras configurações de proxy no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-154">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="ac5b2-155">Se esse valor for "false" ou se não estiver definido, as configurações de proxy estático podem ser especificadas na configuração e substituirão as configurações de proxy do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-155">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="ac5b2-156">Esse valor também deve ser definido como "false" ou não estar configurado para habilitar proxies adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-156">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="ac5b2-157">O exemplo a seguir mostra uma configuração de proxy estático típica.</span><span class="sxs-lookup"><span data-stu-id="ac5b2-157">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac5b2-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac5b2-158">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="ac5b2-159">Detecção automática de proxy</span><span class="sxs-lookup"><span data-stu-id="ac5b2-159">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
