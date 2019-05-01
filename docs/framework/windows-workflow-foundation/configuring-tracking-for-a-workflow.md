---
title: Configurando o rastreamento para um fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: c3e73c3801a41a9401ac2e636fda6362487a05af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052762"
---
# <a name="configuring-tracking-for-a-workflow"></a>Configurando o rastreamento para um fluxo de trabalho

Um fluxo de trabalho pode executar em três maneiras:

- Hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Executado como <xref:System.Activities.WorkflowApplication>

- Executado diretamente usando <xref:System.Activities.WorkflowInvoker>

Dependendo do fluxo de trabalho que hospeda a opção, um participante de rastreamento pode ser adicionado ao código ou em um arquivo de configuração. Este tópico descreve como controlando é configurado adicionando um participante de rastreamento a <xref:System.Activities.WorkflowApplication> e a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, e como ativar o rastreamento para usar <xref:System.Activities.WorkflowInvoker>.

## <a name="configuring-workflow-application-tracking"></a>Configurando o rastreamento de aplicativo de fluxo de trabalho

Um fluxo de trabalho pode executar usando a classe de <xref:System.Activities.WorkflowApplication> . Este tópico demonstra como controlando é configurado para um aplicativo de fluxo de trabalho [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] adicionando um participante de rastreamento para o host do fluxo de trabalho <xref:System.Activities.WorkflowApplication> . Nesse caso, o fluxo de trabalho é executado como um aplicativo de fluxo de trabalho. Você configura um aplicativo de fluxo de trabalho com o código (em vez de usar um arquivo de configuração), que é um arquivo .exe são hospedado usando a classe de <xref:System.Activities.WorkflowApplication> . O participante de rastreamento é adicionado como uma extensão para instância de <xref:System.Activities.WorkflowApplication> . Isso é feito adicionando <xref:System.Activities.Tracking.TrackingParticipant> a coleção de extensões para a instância de WorkflowApplication.

Para um aplicativo de fluxo de trabalho, você pode adicionar a extensão do comportamento de <xref:System.Activities.Tracking.EtwTrackingParticipant> conforme mostrado no código a seguir.

```csharp
LogActivity activity = new LogActivity();

WorkflowApplication instance = new WorkflowApplication(activity);
EtwTrackingParticipant trackingParticipant =
    new EtwTrackingParticipant
{

        TrackingProfile = new TrackingProfile
           {
               Name = "SampleTrackingProfile",
               ActivityDefinitionId = "ProcessOrder",
               Queries = new WorkflowInstanceQuery
               {
                  States = { "*" }
              }
          }
       };
instance.Extensions.Add(trackingParticipant);
```

### <a name="configuring-workflow-service-tracking"></a>Configurando acompanhar de Serviço de Fluxo de Trabalho

Um fluxo de trabalho pode ser exposto como um serviço WCF quando hospedados no <xref:System.ServiceModel.Activities.WorkflowServiceHost> host de serviço. <xref:System.ServiceModel.Activities.WorkflowServiceHost> é uma implementação específica do .NET ServiceHost para um serviço fluxo de trabalho- base. Esta seção explica como configurar o controle para uma execução de serviço do fluxo de trabalho [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] em <xref:System.ServiceModel.Activities.WorkflowServiceHost>. É configurada por um arquivo web.config (para um serviço web hospedado) ou um arquivo App.config (para um serviço hospedado em um aplicativo autônomo, como um aplicativo de console) especificando um comportamento do serviço ou com o código adicionando um comportamento acompanhamento- específico à coleção de <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> para o host serviço.

Para um serviço de fluxo de trabalho hospedados no <xref:System.ServiceModel.WorkflowServiceHost>, você pode adicionar a <xref:System.Activities.Tracking.EtwTrackingParticipant> usando o <`behavior`> elemento em um arquivo de configuração, conforme mostrado no exemplo a seguir.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

Como alternativa, para um serviço de fluxo de trabalho hospedado em <xref:System.ServiceModel.WorkflowServiceHost>, você pode adicionar a extensão do comportamento de <xref:System.Activities.Tracking.EtwTrackingParticipant> com o código. Para adicionar um participante personalizado de rastreamento, criar uma nova extensão do comportamento e adicioná-lo a <xref:System.ServiceModel.ServiceHost> conforme mostrado no código de exemplo a seguir.

> [!NOTE]
> Se você deseja exibir o código de exemplo que mostra como criar um elemento de comportamento personalizado que adiciona um participante personalizado, consulte a [acompanhamento](./samples/tracking.md) exemplos.

```csharp
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new
                                 Uri("http://localhost:8001/Sample"));
EtwTrackingBehavior trackingBehavior =
    new EtwTrackingBehavior
    {
        ProfileName = "Sample Tracking Profile"
    };
svcHost.Description.Behaviors.Add(trackingBehavior);
svcHost.Open();
```

O participante de rastreamento é adicionado ao host serviço de fluxo de trabalho como uma extensão para o comportamento.

Este exemplo de código abaixo mostra como ler um perfil de rastreamento do arquivo de configuração.

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            if (profileName == null)
            {
                profileName = "";
            }

            //Find the profile with the specified profile name in the list of profile found in config
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))
                        select p;

            if (match.Count() == 0)
            {
                //return an empty profile
                trackingProfile = new TrackingProfile()
                {
                    ActivityDefinitionId = displayName
                };

            }
            else
            {
                trackingProfile = match.First();
            }

            return trackingProfile;
```

Este exemplo de código mostra como adicionar um perfil de rastreamento a um host de fluxo de trabalho.

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> Para obter mais informações sobre perfis de rastreamento, consulte [perfis de acompanhamento](https://go.microsoft.com/fwlink/?LinkId=201310).

### <a name="configuring-tracking-using-workflowinvoker"></a>Configurando o rastreamento usando WorkflowInvoker

Para configurar o rastreamento para um fluxo de trabalho foi executado usando <xref:System.Activities.WorkflowInvoker>, adicione o provedor de rastreamento como uma extensão para uma instância de <xref:System.Activities.WorkflowInvoker> . O exemplo de código a seguir é do [acompanhamento personalizado](./samples/custom-tracking.md) exemplo.

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Registros de exibição de rastreamento no visualizador de eventos

Há dois logs do visualizador de eventos de interesse específico exibir quando controlando a execução de WF - o log analítico e depuração de log. Ambos residem em Microsoft&#124;Windows&#124;nó de aplicativos de servidor. Os logs dentro desta seção contêm eventos de um único aplicativo em vez de eventos que têm um impacto no sistema inteiro.

Os eventos de rastreamento de depuração são gravados no log de depuração. Para coletar eventos de rastreamento de depuração de WF no visualizador de eventos, ative o log de depuração.

1. Para abrir o Visualizador de eventos, clique em **inicie**e, em seguida, clique em **executar.** Na caixa de diálogo Executar, digite `eventvwr`.

2. Na caixa de diálogo Visualizador de eventos, expanda o **Applications and Services Logs** nó.

3. Expanda o **Microsoft**, **Windows**, e **aplicativos de servidor** nós.

4. Clique com botão direito a **Debug** nó sob o **aplicativos de servidor** nó e selecione **Habilitar Log**.

5. Execute o aplicativo rastreamento ativado gerar eventos de rastreamento.

6. Clique com botão direito do **Debug** nó e selecione **atualizar.** Os eventos de rastreamento devem ser no centro painel visível.

WF 4 fornece um participante de rastreamento que grava registros de rastreamento a uma sessão de rastreamento (ETW de evento para o Windows). O participante de rastreamento de ETW é configurado com um perfil de rastreamento para assinar a acompanhar registros. Quando você estiver ativado, os erros que acompanham registros são emitidas a ETW. Eventos de controle de (ETW entre o intervalo de 100-113) que correspondem aos eventos de rastreamento emissores por participante de rastreamento de ETW são gravados no log analítico.

Para exibir registros de rastreamento, siga estas etapas.

1. Para abrir o Visualizador de eventos, clique em **inicie**e, em seguida, clique em **executar.** Na caixa de diálogo Executar, digite `eventvwr`.

2. Na caixa de diálogo Visualizador de eventos, expanda o **Applications and Services Logs** nó.

3. Expanda o **Microsoft**, **Windows**, e **aplicativos de servidor** nós.

4. Com o botão direito do **analítico** nó sob o **aplicativos de servidor** nó e selecione **Habilitar Log**.

5. Executar o aplicativo acompanhamento- ativado gerar registros de rastreamento.

6. Clique com botão direito do **analítico** nó e selecione **atualizar.** Controlar registros deve ser no centro painel visível.

A imagem a seguir mostra os eventos de rastreamento no Visualizador de eventos:

![Captura de tela mostrando o Visualizador de eventos que registros de acompanhamento.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Registrando um ID específico do aplicativo provedor

Se os eventos precisam ser gravados em um log do aplicativo específico, siga estas etapas para registrar o novo manifesto do provedor.

1. Declare a identificação do provedor no arquivo de configuração do aplicativo.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Copiar o arquivo de manifesto de %windir%\Microsoft.NET\Framework\\< a versão mais recente do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man para um local temporário e renomeie-o como Microsoft.Windows.ApplicationServer.Applications_Provider1.man

3. Altere o GUID no arquivo de manifesto a nova GUID.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. Altere o nome do provedor se você não desejar desinstalar o provedor padrão.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. Se você alterou o nome do provedor na etapa anterior, altere os nomes de canal no arquivo de manifesto para o novo nome do provedor.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Gerencia o DLL de recurso seguindo estas etapas.

    1. Instalar o Windows SDK. O SDK do Windows inclui o compilador de mensagens ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) e o compilador de recurso ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).

    2. Em um prompt de comando do Windows SDK, execução mc.exe no novo arquivo de manifesto.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Executar rc.exe no arquivo de recurso gerado na etapa anterior.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. Crie um arquivo vazio de Cs chamado NewProviderReg.cs.

    5. Criar uma DLL de recurso usando o compilador C#.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Altere o nome da dll de recurso e a mensagem no arquivo de manifesto de `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` para o novo nome de dll.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. Use [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) para registrar o manifesto.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Consulte também

- [Monitoramento do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitoramento de aplicativos com a malha de aplicativos](https://go.microsoft.com/fwlink/?LinkId=201275)
