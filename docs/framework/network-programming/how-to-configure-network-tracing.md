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
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040649"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="a18df-102">Como: Configurar rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="a18df-102">How to: Configure network tracing</span></span>

<span data-ttu-id="a18df-103">O aplicativo ou o arquivo de configuração do computador mantém as configurações que determinam o formato e o conteúdo dos rastreamentos de rede.</span><span class="sxs-lookup"><span data-stu-id="a18df-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="a18df-104">Antes de executar este procedimento, certifique-se de que o rastreamento está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a18df-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="a18df-105">Para obter mais informações, consulte [Ativar rastreamento de rede](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="a18df-105">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="a18df-106">O arquivo de configuração do computador, *machine.config,* é armazenado na pasta *%windir%\Microsoft.NET\Framework.*</span><span class="sxs-lookup"><span data-stu-id="a18df-106">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="a18df-107">Há um arquivo de *máquina.config* separado nas pastas em *%windir%\Microsoft.NET\Framework* para cada versão do .NET Framework instalado no computador, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a18df-107">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="a18df-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="a18df-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="a18df-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="a18df-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="a18df-110">Essas configurações também podem ser feitas no arquivo de configuração do aplicativo, que tem precedência sobre o arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="a18df-110">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="a18df-111">Configurar rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="a18df-111">Configure network tracing</span></span>

<span data-ttu-id="a18df-112">Para configurar o rastreamento de rede, adicione as seguintes linhas ao arquivo de configuração apropriado.</span><span class="sxs-lookup"><span data-stu-id="a18df-112">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="a18df-113">Os valores e as opções dessas configurações são descritos nas tabelas abaixo.</span><span class="sxs-lookup"><span data-stu-id="a18df-113">The values and options for these settings are described in the tables below.</span></span>

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
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a><span data-ttu-id="a18df-114">Trace saída de métodos</span><span class="sxs-lookup"><span data-stu-id="a18df-114">Trace output from methods</span></span>

<span data-ttu-id="a18df-115">Quando você adiciona um nome para o bloco `<switches>`, a saída de rastreamento inclui informações de alguns métodos relacionados ao nome.</span><span class="sxs-lookup"><span data-stu-id="a18df-115">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="a18df-116">A tabela a seguir descreve a saída:</span><span class="sxs-lookup"><span data-stu-id="a18df-116">The following table describes the output:</span></span>

|<span data-ttu-id="a18df-117">Nome</span><span class="sxs-lookup"><span data-stu-id="a18df-117">Name</span></span>|<span data-ttu-id="a18df-118">Saída de</span><span class="sxs-lookup"><span data-stu-id="a18df-118">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="a18df-119">Alguns métodos <xref:System.Net.Sockets.Socket>públicos <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.TcpClient>das <xref:System.Net.Dns> classes e classes.</span><span class="sxs-lookup"><span data-stu-id="a18df-119">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="a18df-120">Alguns métodos <xref:System.Net.HttpWebRequest>públicos <xref:System.Net.HttpWebResponse> <xref:System.Net.FtpWebRequest>das, <xref:System.Net.FtpWebResponse> e classes e informações de depuração SSL (certificados inválidos, lista de emissores ausentes e erros de certificado do cliente).</span><span class="sxs-lookup"><span data-stu-id="a18df-120">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="a18df-121">Alguns métodos públicos das classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> e <xref:System.Net.HttpListenerResponse>.</span><span class="sxs-lookup"><span data-stu-id="a18df-121">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="a18df-122">Alguns métodos particulares e internos em `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="a18df-122">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="a18df-123">Alguns métodos públicos das classes <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> e <xref:System.Net.Http.WebRequestHandler>.</span><span class="sxs-lookup"><span data-stu-id="a18df-123">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="a18df-124">Alguns métodos públicos das classes <xref:System.Net.WebSockets.ClientWebSocket> e <xref:System.Net.WebSockets.WebSocket>.</span><span class="sxs-lookup"><span data-stu-id="a18df-124">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="a18df-125">Atributos de saída de rastreamento</span><span class="sxs-lookup"><span data-stu-id="a18df-125">Trace output attributes</span></span>

<span data-ttu-id="a18df-126">Os atributos listados na tabela a seguir configuram saída de rastreamento:</span><span class="sxs-lookup"><span data-stu-id="a18df-126">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="a18df-127">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="a18df-127">Attribute name</span></span>|<span data-ttu-id="a18df-128">Valor do atributo</span><span class="sxs-lookup"><span data-stu-id="a18df-128">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="a18df-129">Atributo <xref:System.String> obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a18df-129">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="a18df-130">Define o detalhamento da saída.</span><span class="sxs-lookup"><span data-stu-id="a18df-130">Sets the verbosity of the output.</span></span> <span data-ttu-id="a18df-131">Valores legítimos são `Critical`, `Error`, `Verbose`, `Warning` e `Information`.</span><span class="sxs-lookup"><span data-stu-id="a18df-131">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="a18df-132">Este atributo deve ser definido no elemento **de adição** do elemento **switches.**</span><span class="sxs-lookup"><span data-stu-id="a18df-132">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="a18df-133">Uma exceção é lançada se esse atributo for definido no elemento **de origem.**</span><span class="sxs-lookup"><span data-stu-id="a18df-133">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="a18df-134">Exemplo: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="a18df-134">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="a18df-135">Atributo <xref:System.Int32> opcional.</span><span class="sxs-lookup"><span data-stu-id="a18df-135">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="a18df-136">Define o número máximo de bytes de dados de rede inclusos em cada linha de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="a18df-136">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="a18df-137">O valor padrão é 1.024.</span><span class="sxs-lookup"><span data-stu-id="a18df-137">The default value is 1024.</span></span><br /><br /><span data-ttu-id="a18df-138">Este atributo deve ser definido no elemento **de origem.**</span><span class="sxs-lookup"><span data-stu-id="a18df-138">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="a18df-139">Uma exceção é lançada se esse atributo for definido em um elemento o elemento **switches.**</span><span class="sxs-lookup"><span data-stu-id="a18df-139">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="a18df-140">Exemplo: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="a18df-140">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="a18df-141">Atributo <xref:System.String> opcional.</span><span class="sxs-lookup"><span data-stu-id="a18df-141">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="a18df-142">Definido como `includehex` para exibir rastreamentos de protocolo em formato hexadecimal e textual.</span><span class="sxs-lookup"><span data-stu-id="a18df-142">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="a18df-143">Definido como `protocolonly` para exibir somente o texto.</span><span class="sxs-lookup"><span data-stu-id="a18df-143">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="a18df-144">O valor padrão é `includehex`.</span><span class="sxs-lookup"><span data-stu-id="a18df-144">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="a18df-145">Este atributo deve ser definido no elemento **de origem.**</span><span class="sxs-lookup"><span data-stu-id="a18df-145">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="a18df-146">Uma exceção é lançada se esse atributo for definido em um elemento o elemento **switches.**</span><span class="sxs-lookup"><span data-stu-id="a18df-146">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="a18df-147">Exemplo: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="a18df-147">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="a18df-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="a18df-148">See also</span></span>

- [<span data-ttu-id="a18df-149">Interpretando o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="a18df-149">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="a18df-150">Rastreamento de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a18df-150">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="a18df-151">Habilitando o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="a18df-151">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="a18df-152">Rastreamento e instrumentação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="a18df-152">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
