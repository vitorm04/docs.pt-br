---
title: Como configurar o rastreamento de rede
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 12f328d58ef568c78d1e2c8a8ff564839cba9f3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-network-tracing"></a>Como configurar o rastreamento de rede
O aplicativo ou o arquivo de configuração do computador mantém as configurações que determinam o formato e o conteúdo dos rastreamentos de rede. Antes de executar este procedimento, certifique-se de que o rastreamento está habilitado. Para obter informações sobre como habilitar o rastreamento, consulte [Habilitando o rastreamento de rede](../../../docs/framework/network-programming/enabling-network-tracing.md).  
  
 O arquivo de configuração do computador, machine.config, é armazenado na pasta %Windir%\Microsoft.NET\Framework no diretório em que o Windows foi instalado. Há um arquivo Machine. config separado nas pastas em %windir%\Microsoft.NET\Framework. para cada versão do .NET Framework instalado no computador (por exemplo, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config ou C:\Windows\ Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Essas configurações também podem ser feitas no arquivo de configuração do aplicativo, que tem precedência sobre o arquivo de configuração do computador.  
  
### <a name="to-configure-network-tracing"></a>Para configurar o rastreamento de rede  
  
-   Adicione as seguintes linhas no arquivo de configuração apropriado. Os valores e as opções dessas configurações são descritos nas tabelas abaixo.  
  
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
  
 Quando você adiciona um nome para o bloco `<switches>`, a saída de rastreamento inclui informações de alguns métodos relacionados ao nome. A tabela a seguir descreve a saída.  
  
|Nome|Saída de|  
|----------|-----------------|  
|`System.Net.Sockets`|Alguns métodos públicos das classes <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient> e <xref:System.Net.Dns>.|  
|`System.Net`|Alguns métodos públicos das classes <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse>, e informações de depuração SSL (certificados inválidos, lista de emissores ausentes e erros do certificado de cliente).|  
|`System.Net.HttpListener`|Alguns métodos públicos das classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> e <xref:System.Net.HttpListenerResponse>.|  
|`System.Net.Cache`|Alguns métodos particulares e internos em `System.Net.Cache`.|  
|`System.Net.Http`|Alguns métodos públicos das classes <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> e <xref:System.Net.Http.WebRequestHandler>.|  
|`System.Net.WebSockets.WebSocket`|Alguns métodos públicos das classes <xref:System.Net.WebSockets.ClientWebSocket> e <xref:System.Net.WebSockets.WebSocket>.|  
  
 Os atributos listados na tabela a seguir configuram a saída de rastreamento.  
  
|Nome do atributo|Valor do atributo|  
|--------------------|---------------------|  
|`Value`|Atributo <xref:System.String> obrigatório. Define o detalhamento da saída. Valores legítimos são `Critical`, `Error`, `Verbose`, `Warning` e `Information`.<br /><br /> Esse atributo deve ser definido no elemento \<add name> do elemento \<switches>, conforme mostrado no exemplo. Uma exceção é gerada se esse atributo é definido no elemento \<source>.|  
|`maxdatasize`|Atributo <xref:System.Int32> opcional. Define o número máximo de bytes de dados de rede inclusos em cada linha de rastreamento. O valor padrão é 1024.<br /><br /> Esse atributo deve ser definido no elemento \<source>, conforme mostrado no exemplo. Uma exceção é gerada se esse atributo é definido em um elemento no elemento \<switches>.|  
|`Tracemode`|Atributo <xref:System.String> opcional. Definido como `includehex` para exibir rastreamentos de protocolo em formato hexadecimal e textual. Definido como `protocolonly` para exibir somente o texto. O valor padrão é `includehex`.<br /><br /> Esse atributo deve ser definido no elemento \<switches>, conforme mostrado no exemplo. Uma exceção é gerada se esse atributo é definido em um elemento no elemento \<source>.|  
  
## <a name="see-also"></a>Consulte também  
 [Interpretando o rastreamento de rede](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Rastreamento de rede no .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 [Habilitar o rastreamento de rede](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Introdução à instrumentação e ao rastreamento](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
