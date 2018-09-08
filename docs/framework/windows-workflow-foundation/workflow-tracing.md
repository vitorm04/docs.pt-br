---
title: Rastreamento de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 27e56933043c9eb955500cdd1c5bbd06cb33bde8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129543"
---
# <a name="workflow-tracing"></a>Rastreamento de fluxo de trabalho
Oferece de rastreamento de fluxo de trabalho uma maneira para capturar informações de diagnóstico usando os ouvintes de rastreamento do .NET Framework. O rastreamento podem ser ativado se é um problema detectado com o aplicativo e desativado novamente o problema é resolvido uma vez. Há duas maneiras que você pode ativar o rastreamento de depuração para fluxos de trabalho. Você poderá configurá-lo usando o visualizador de rastreamento do evento ou você pode usar <xref:System.Diagnostics> para enviar os eventos de rastreamento em um arquivo.  
  
## <a name="enabling-debug-tracing-in-etw"></a>Ativar o rastreamento de depuração em ETW  
 Para ativar o rastreamento usando ETW, ative o canal de depuração no visualizador de eventos:  
  
1.  Navegue para o nó analítico e de depuração dos logs no visualizador de eventos.  
  
2.  Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos -> aplicativos e Logs de serviços -> Microsoft -> Windows -> aplicativos de servidor**. Clique com botão direito **aplicativos de servidor** e selecione **Exibir -> Mostrar Logs analíticos e depuração**. Clique com botão direito **Debug** e selecione **Habilitar Log**.  
  
3.  Quando um fluxo de trabalho executa a depuração e os rastreamentos são emitidas ao canal de depuração de ETW, podem ser exibidos no visualizador de eventos. Navegue até **Visualizador de eventos -> aplicativos e Logs de serviços -> Microsoft -> Windows -> aplicativos de servidor**. Clique com botão direito **Debug** e selecione **atualizar**.  
  
4.  O tamanho do buffer analítico padrão de rastreamento é apenas 4 quilobytes de (KB); é recomendável aumentar o tamanho para 32 KB. Para fazer isso, execute as seguintes etapas.  
  
    1.  Execute o seguinte comando no diretório atual do framework (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.0 .21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Alterar o \<bufferSize > valor no arquivo do Windows a 32.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  Execute o seguinte comando no diretório atual do framework (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.0 .21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  Se você estiver usando o .NET Framework 4 Client Profile, você deve primeiro registrar o manifesto ETW executando o seguinte comando do diretório .NET Framework 4: `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Ativar o rastreamento de depuração usando System.Diagnostics  
 Essas ouvintes podem ser configuradas no arquivo App.config do aplicativo de fluxo de trabalho, ou no Web.config para um serviço de fluxo de trabalho. Neste exemplo, uma [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) está configurado para salvar informações de rastreamento para o arquivo de Mytracelog no diretório atual.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Monitoramento do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitoramento de aplicativos com a malha de aplicativos](https://go.microsoft.com/fwlink/?LinkId=201275)
