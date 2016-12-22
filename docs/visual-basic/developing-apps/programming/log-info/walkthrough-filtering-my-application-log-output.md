---
title: "Instru&#231;&#245;es passo a passo: filtrando a sa&#237;da de My.Application.Log (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Objeto My. log, filtragem de saída"
  - "Objeto My.Application.Log, filtragem de saída"
  - "logs de eventos do aplicativo, a filtragem de saída"
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: filtrando a sa&#237;da de My.Application.Log (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este passo a passo demonstra como alterar a filtragem de log padrão de `My.Application.Log` objeto, para controlar quais informações são passadas do `Log` objeto para os ouvintes e quais informações são escritas pelos ouvintes. Você pode alterar o comportamento de log mesmo após a criação do aplicativo, porque as informações de configuração são armazenadas no arquivo de configuração do aplicativo.  
  
## <a name="getting-started"></a>Guia de Introdução  
 Cada mensagem que `My.Application.Log` gravações possui um nível de gravidade associado, os mecanismos de filtragem usam para controlar a saída de log. Este aplicativo de exemplo usa `My.Application.Log` métodos para gravar diversas mensagens de log com diferentes níveis de severidade.  
  
#### <a name="to-build-the-sample-application"></a>Para criar o aplicativo de exemplo  
  
1.  Abra um novo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto aplicativo do Windows.  
  
2.  Adicione um botão denominado Button1 para Form1.  
  
3.  No <xref:System.Windows.Forms.Control.Click> manipulador de eventos para Button1, adicione o seguinte código:  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  Execute o aplicativo no depurador.  
  
5.  Pressione **Button1**.  
  
     O aplicativo grava as informações a seguir ao arquivo de saída e de log de depuração do aplicativo.  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  Feche o aplicativo.  
  
     Para obter informações sobre como exibir a janela de saída de depuração do aplicativo, consulte [janela saída](/visual-studio/ide/reference/output-window). Para obter informações sobre o local do arquivo de log do aplicativo, consulte [passo a passo: Determinando onde My.Application.Log grava informações](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md).  
  
    > [!NOTE]
    >  Por padrão, o aplicativo libera a saída do arquivo de log quando o aplicativo é fechado.  
  
     No exemplo acima, a segunda chamada para o <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> método e a chamada para o <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> método produz saída de log, enquanto as primeira e última chamadas para o `WriteEntry` método não. Isso ocorre porque os níveis de severidade de `WriteEntry` e `WriteException` são "Information" e "Error", ambos que são permitidas pelo `My.Application.Log` do objeto filtragem de log padrão. No entanto, os eventos com níveis de gravidade "Start" e "Stop" são impedidos de produzir saída de log.  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>Filtragem de todos os ouvintes de My.Application.Log  
 O `My.Application.Log` objeto usa um <xref:System.Diagnostics.SourceSwitch> chamado `DefaultSwitch` para controlar quais mensagens ele passa da `WriteEntry` e `WriteException` métodos para os ouvintes de log. Você pode configurar `DefaultSwitch` no arquivo de configuração do aplicativo, definindo seu valor como um do <xref:System.Diagnostics.SourceLevels> valores de enumeração. Por padrão, seu valor é "Informações".  
  
 Esta tabela mostra o nível de gravidade necessário para o Log gravar uma mensagem para os ouvintes, fornecida uma determinada `DefaultSwitch` configuração.  
  
|||  
|-|-|  
|Valor DefaultSwitch|Gravidade da mensagem necessária para saída|  
|`Critical`|`Critical`|  
|`Error`|`Critical` ou `Error`|  
|`Warning`|`Critical`, `Error`, or `Warning`|  
|`Information`|`Critical`, `Error`, `Warning` ou `Information`|  
|`Verbose`|`Critical`, `Error`, `Warning`, `Information`, or `Verbose`|  
|`ActivityTracing`|`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`|  
|`All`|Todas as mensagens são permitidas.|  
|`Off`|Todas as mensagens são bloqueadas.|  
  
> [!NOTE]
>  O `WriteEntry` e `WriteException` os métodos têm uma sobrecarga que não especifica um nível de severidade. O nível de gravidade implícito para a `WriteEntry` sobrecarga é "Information" e o nível de gravidade implícito para a `WriteException` sobrecarga é "Error".  
  
 Esta tabela explica a saída de log mostrada no exemplo anterior: com o padrão `DefaultSwitch` configuração de "Information", apenas a segunda chamada para o `WriteEntry` método e a chamada para o `WriteException` método produzem saída de log.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Log de eventos de rastreamento de atividade apenas  
  
1.  Clique com botão direito app. config no **Solution Explorer** e selecione **Abrir**.  
  
     - ou -  
  
     Se não houver nenhum arquivo App. config:  
  
    1.  Sobre o **projeto** menu, escolha **Adicionar Novo Item**.  
  
    2.  Do **Add New Item** caixa de diálogo, escolha **arquivo de configuração de aplicativo**.  
  
    3.  Clique em **Adicionar**.  
  
2.  Localize o `<switches>` seção, que é o `<system.diagnostics>` seção, que está no nível superior `<configuration>` seção.  
  
3.  Localize o elemento que adiciona `DefaultSwitch` à coleção de opções. Ele deve ser semelhante a este elemento:  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  Altere o valor de `value` atributo para "ActivityTracing".  
  
5.  O conteúdo do arquivo App. config deve ser semelhante ao XML a seguir:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  Execute o aplicativo no depurador.  
  
7.  Pressione **Button1**.  
  
     O aplicativo grava as informações a seguir ao arquivo de saída e de log de depuração do aplicativo:  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  Feche o aplicativo.  
  
9. Altere o valor de `value` como "Informações".  
  
    > [!NOTE]
    >  O `DefaultSwitch` Alternar apenas controles de configuração `My.Application.Log`. Ele não altera como a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Diagnostics.Trace?displayProperty=fullName> e <xref:System.Diagnostics.Debug?displayProperty=fullName> classes se comportam.  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>Indivíduo filtragem para ouvintes de My.Application.Log  
 O exemplo anterior mostra como alterar a filtragem para todos os `My.Application.Log` saída. Este exemplo demonstra como filtrar um ouvinte de log individuais. Por padrão, um aplicativo tem dois ouvintes que gravar a saída de depuração do aplicativo e o arquivo de log.  
  
 O arquivo de configuração controla o comportamento de ouvintes de log, permitindo que cada um tenha um filtro, que é semelhante a uma opção para `My.Application.Log`. Um ouvinte de log produzirá uma mensagem somente se a gravidade da mensagem for permitida por ambos os o log `DefaultSwitch` e filtro do ouvinte de log.  
  
 Este exemplo demonstra como configurar a filtragem para um novo ouvinte de depuração e adicioná-lo para o `Log` objeto. O ouvinte de depuração padrão deve ser removido o `Log` do objeto, por isso é que as mensagens de depuração são provenientes do novo ouvinte de depuração.  
  
#### <a name="to-log-only-activity-tracing-events"></a>Para registrar somente eventos de rastreamento de atividades  
  
1.  Clique com botão direito app. config no **Solution Explorer** e escolha **Abrir**.  
  
     - ou -  
  
     Se não houver nenhum arquivo App. config:  
  
    1.  Sobre o **projeto** menu, escolha **Adicionar Novo Item**.  
  
    2.  Do **Add New Item** caixa de diálogo, escolha **arquivo de configuração de aplicativo**.  
  
    3.  Clique em **Adicionar**.  
  
2.  Clique com botão direito app. config no **soluções**. Escolha **Abrir**.  
  
3.  Localize o `<listeners>` seção, o `<source>` seção com o `name` atributo "DefaultSource", que está sob o `<sources>` seção. O `<sources>` seção está sob o `<system.diagnostics>` seção superior `<configuration>` seção.  
  
4.  Adicionar esse elemento para o `<listeners>` seção:  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  Localize o `<sharedListeners>` seção, o `<system.diagnostics>` seção superior `<configuration>` seção.  
  
6.  Adicionar esse elemento a que `<sharedListeners>` seção:  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     O <xref:System.Diagnostics.EventTypeFilter> filtro escolhe uma da <xref:System.Diagnostics.SourceLevels> valores de enumeração como seu `initializeData` atributo.  
  
7.  O conteúdo do arquivo App. config deve ser semelhante ao XML a seguir:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  Execute o aplicativo no depurador.  
  
9. Pressione **Button1**.  
  
     O aplicativo grava as informações a seguir ao arquivo de log do aplicativo:  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     O aplicativo grava menos informações a saída de depuração do aplicativo devido à filtragem mais restritiva.  
  
     `Default Error   2   Error`  
  
10. Feche o aplicativo.  
  
 Para obter mais informações sobre como alterar as configurações de log após a implantação, consulte [trabalhar com Logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Determinando onde My.Application.Log grava informações](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)   
 [Passo a passo: Alterando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)   
 [Passo a passo: Criando ouvintes de Log personalizados](../Topic/Walkthrough:%20Creating%20Custom%20Log%20Listeners%20\(Visual%20Basic\).md)   
 [Como: gravar mensagens de Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [Opções de rastreamento](../Topic/Trace%20Switches.md)   
 [Informações de log do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)