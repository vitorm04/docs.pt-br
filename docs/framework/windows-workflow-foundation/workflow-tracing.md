---
title: Rastreamento de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 972520aae7a2af950ed1ba079769861173784148
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837500"
---
# <a name="workflow-tracing"></a><span data-ttu-id="025b7-102">Rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="025b7-102">Workflow Tracing</span></span>
<span data-ttu-id="025b7-103">Oferece de rastreamento de fluxo de trabalho uma maneira para capturar informações de diagnóstico usando os ouvintes de rastreamento do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="025b7-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="025b7-104">O rastreamento podem ser ativado se é um problema detectado com o aplicativo e desativado novamente o problema é resolvido uma vez.</span><span class="sxs-lookup"><span data-stu-id="025b7-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="025b7-105">Há duas maneiras que você pode ativar o rastreamento de depuração para fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="025b7-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="025b7-106">Você poderá configurá-lo usando o visualizador de rastreamento do evento ou você pode usar <xref:System.Diagnostics> para enviar os eventos de rastreamento em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="025b7-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="025b7-107">Ativar o rastreamento de depuração em ETW</span><span class="sxs-lookup"><span data-stu-id="025b7-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="025b7-108">Para ativar o rastreamento usando ETW, ative o canal de depuração no visualizador de eventos:</span><span class="sxs-lookup"><span data-stu-id="025b7-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="025b7-109">Navegue para o nó analítico e de depuração dos logs no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="025b7-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="025b7-110">No modo de exibição de árvore no Visualizador de Eventos, navegue até **Visualizador de eventos-> logs de aplicativos e serviços-> Microsoft-> Windows-> Application Server-Applications**.</span><span class="sxs-lookup"><span data-stu-id="025b7-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="025b7-111">Clique com o botão direito do mouse em **servidor de aplicativos** e selecione **Exibir-> Mostrar logs analíticos e de depuração**.</span><span class="sxs-lookup"><span data-stu-id="025b7-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="025b7-112">Clique com o botão direito do mouse em **depurar** e selecione **habilitar log**.</span><span class="sxs-lookup"><span data-stu-id="025b7-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="025b7-113">Quando um fluxo de trabalho executa a depuração e os rastreamentos são emitidas ao canal de depuração de ETW, podem ser exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="025b7-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="025b7-114">Navegue até **Visualizador de eventos-> logs de serviços e aplicativos-> Microsoft-> Windows-> Application Server – Applications**.</span><span class="sxs-lookup"><span data-stu-id="025b7-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="025b7-115">Clique com o botão direito do mouse em **depurar** e selecione **Atualizar**.</span><span class="sxs-lookup"><span data-stu-id="025b7-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="025b7-116">O tamanho do buffer analítico padrão de rastreamento é apenas 4 quilobytes de (KB); é recomendável aumentar o tamanho para 32 KB.</span><span class="sxs-lookup"><span data-stu-id="025b7-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="025b7-117">Para fazer isso, execute as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="025b7-117">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="025b7-118">Execute o seguinte comando no diretório atual do framework (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.0 .21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="025b7-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="025b7-119">Altere o \<bufferSize > valor no arquivo Windows. ApplicationServer. Applications. Man para 32.</span><span class="sxs-lookup"><span data-stu-id="025b7-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="025b7-120">Execute o seguinte comando no diretório atual do framework (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.0 .21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="025b7-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="025b7-121">Se você estiver usando o perfil de cliente .NET Framework 4, deverá primeiro registrar o manifesto do ETW executando o seguinte comando no diretório .NET Framework 4: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="025b7-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="025b7-122">Ativar o rastreamento de depuração usando System.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="025b7-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="025b7-123">Essas ouvintes podem ser configuradas no arquivo App.config do aplicativo de fluxo de trabalho, ou no Web.config para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="025b7-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="025b7-124">Neste exemplo, uma <xref:System.Diagnostics.TextWriterTraceListener> está configurada para salvar informações de rastreamento no arquivo MyTraceLog. txt no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="025b7-124">In this example, a <xref:System.Diagnostics.TextWriterTraceListener> is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="025b7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="025b7-125">See also</span></span>

- <span data-ttu-id="025b7-126">[Monitoramento do Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="025b7-126">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="025b7-127">[Monitorando aplicativos com o app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="025b7-127">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
