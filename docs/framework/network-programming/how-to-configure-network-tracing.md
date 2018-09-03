---
title: Como configurar o rastreamento de rede
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3c9550bf9d3483a8d2961e6137138bfb11f71bca
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404321"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="75b87-102">Como configurar o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="75b87-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="75b87-103">O aplicativo ou o arquivo de configuração do computador mantém as configurações que determinam o formato e o conteúdo dos rastreamentos de rede.</span><span class="sxs-lookup"><span data-stu-id="75b87-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="75b87-104">Antes de executar este procedimento, certifique-se de que o rastreamento está habilitado.</span><span class="sxs-lookup"><span data-stu-id="75b87-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="75b87-105">Para obter informações sobre como habilitar o rastreamento, consulte [Habilitando o rastreamento de rede](../../../docs/framework/network-programming/enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="75b87-105">For information about enabling tracing, see [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="75b87-106">O arquivo de configuração do computador, machine.config, é armazenado na pasta %Windir%\Microsoft.NET\Framework no diretório em que o Windows foi instalado.</span><span class="sxs-lookup"><span data-stu-id="75b87-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="75b87-107">Há um arquivo machine.config separado nas pastas em %Windir%\Microsoft.NET\Framework para cada versão do .NET Framework instalada no computador (por exemplo, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config ou C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config).</span><span class="sxs-lookup"><span data-stu-id="75b87-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="75b87-108">Essas configurações também podem ser feitas no arquivo de configuração do aplicativo, que tem precedência sobre o arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="75b87-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="75b87-109">Para configurar o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="75b87-109">To configure network tracing</span></span>  
  
-   <span data-ttu-id="75b87-110">Adicione as seguintes linhas no arquivo de configuração apropriado.</span><span class="sxs-lookup"><span data-stu-id="75b87-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="75b87-111">Os valores e as opções dessas configurações são descritos nas tabelas abaixo.</span><span class="sxs-lookup"><span data-stu-id="75b87-111">The values and options for these settings are described in the tables below.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="System.Net" tracemode="includehex" maxdatasize="1024">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Cache">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Http">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Sockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.WebSockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="System.Net" value="Verbose"/>  
          <add name="System.Net.Cache" value="Verbose"/>  
          <add name="System.Net.Http" value="Verbose"/>  
          <add name="System.Net.Sockets" value="Verbose"/>  
          <add name="System.Net.WebSockets" value="Verbose"/>  
        </switches>  
        <sharedListeners>  
          <add name="System.Net"  
            type="System.Diagnostics.TextWriterTraceListener"  
            initializeData="network.log"  
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 <span data-ttu-id="75b87-112">Quando você adiciona um nome para o bloco `<switches>`, a saída de rastreamento inclui informações de alguns métodos relacionados ao nome.</span><span class="sxs-lookup"><span data-stu-id="75b87-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="75b87-113">A tabela a seguir descreve a saída.</span><span class="sxs-lookup"><span data-stu-id="75b87-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="75b87-114">Nome</span><span class="sxs-lookup"><span data-stu-id="75b87-114">Name</span></span>|<span data-ttu-id="75b87-115">Saída de</span><span class="sxs-lookup"><span data-stu-id="75b87-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="75b87-116">Alguns métodos públicos das classes <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient> e <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="75b87-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="75b87-117">Alguns métodos públicos das classes <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse>, e informações de depuração SSL (certificados inválidos, lista de emissores ausentes e erros do certificado de cliente).</span><span class="sxs-lookup"><span data-stu-id="75b87-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="75b87-118">Alguns métodos públicos das classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> e <xref:System.Net.HttpListenerResponse>.</span><span class="sxs-lookup"><span data-stu-id="75b87-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="75b87-119">Alguns métodos particulares e internos em `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="75b87-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="75b87-120">Alguns métodos públicos das classes <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> e <xref:System.Net.Http.WebRequestHandler>.</span><span class="sxs-lookup"><span data-stu-id="75b87-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="75b87-121">Alguns métodos públicos das classes <xref:System.Net.WebSockets.ClientWebSocket> e <xref:System.Net.WebSockets.WebSocket>.</span><span class="sxs-lookup"><span data-stu-id="75b87-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="75b87-122">Os atributos listados na tabela a seguir configuram a saída de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="75b87-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="75b87-123">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="75b87-123">Attribute name</span></span>|<span data-ttu-id="75b87-124">Valor do atributo</span><span class="sxs-lookup"><span data-stu-id="75b87-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="75b87-125">Atributo <xref:System.String> obrigatório.</span><span class="sxs-lookup"><span data-stu-id="75b87-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="75b87-126">Define o detalhamento da saída.</span><span class="sxs-lookup"><span data-stu-id="75b87-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="75b87-127">Valores legítimos são `Critical`, `Error`, `Verbose`, `Warning` e `Information`.</span><span class="sxs-lookup"><span data-stu-id="75b87-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="75b87-128">Esse atributo deve ser definido no elemento \<add name> do elemento \<switches>, conforme mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="75b87-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="75b87-129">Uma exceção é gerada se esse atributo é definido no elemento \<source>.</span><span class="sxs-lookup"><span data-stu-id="75b87-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="75b87-130">Atributo <xref:System.Int32> opcional.</span><span class="sxs-lookup"><span data-stu-id="75b87-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="75b87-131">Define o número máximo de bytes de dados de rede inclusos em cada linha de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="75b87-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="75b87-132">O valor padrão é 1024.</span><span class="sxs-lookup"><span data-stu-id="75b87-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="75b87-133">Esse atributo deve ser definido no elemento \<source>, conforme mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="75b87-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="75b87-134">Uma exceção é gerada se esse atributo é definido em um elemento no elemento \<switches>.</span><span class="sxs-lookup"><span data-stu-id="75b87-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="75b87-135">Atributo <xref:System.String> opcional.</span><span class="sxs-lookup"><span data-stu-id="75b87-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="75b87-136">Definido como `includehex` para exibir rastreamentos de protocolo em formato hexadecimal e textual.</span><span class="sxs-lookup"><span data-stu-id="75b87-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="75b87-137">Definido como `protocolonly` para exibir somente o texto.</span><span class="sxs-lookup"><span data-stu-id="75b87-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="75b87-138">O valor padrão é `includehex`.</span><span class="sxs-lookup"><span data-stu-id="75b87-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="75b87-139">Esse atributo deve ser definido no elemento \<switches>, conforme mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="75b87-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="75b87-140">Uma exceção é gerada se esse atributo é definido em um elemento no elemento \<source>.</span><span class="sxs-lookup"><span data-stu-id="75b87-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75b87-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75b87-141">See Also</span></span>  
 [<span data-ttu-id="75b87-142">Interpretando o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="75b87-142">Interpreting Network Tracing</span></span>](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [<span data-ttu-id="75b87-143">Rastreamento de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="75b87-143">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 [<span data-ttu-id="75b87-144">Habilitando o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="75b87-144">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [<span data-ttu-id="75b87-145">Introdução à instrumentação e ao rastreamento</span><span class="sxs-lookup"><span data-stu-id="75b87-145">Introduction to Instrumentation and Tracing</span></span>](https://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
