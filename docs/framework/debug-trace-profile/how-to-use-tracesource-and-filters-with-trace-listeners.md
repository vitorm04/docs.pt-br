---
title: Como usar TraceSource e filtros com ouvintes de rastreamento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 73a91d081a1e59995d52f3ef6927db12dd7e4599
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>Como usar TraceSource e filtros com ouvintes de rastreamento
Um dos novos recursos do .NET Framework versão 2.0 é um sistema de rastreamento aprimorado. A premissa básica permanece inalterada: mensagens de rastreamento são enviadas por meio de comutadores para ouvintes, que relatam os dados para um meio de saída associado. Uma diferença principal para a versão 2.0 é que os rastreamentos podem ser iniciados por meio de instâncias da classe <xref:System.Diagnostics.TraceSource>. A <xref:System.Diagnostics.TraceSource> destina-se a funcionar como um sistema de rastreamento aprimorado e pode ser usada no lugar dos métodos estáticos das classes de rastreamento antigas <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug>. As classes <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> familiares ainda existem, mas a prática recomendada é usar a classe <xref:System.Diagnostics.TraceSource> para o rastreamento.  
  
 Este tópico descreve o uso de um <xref:System.Diagnostics.TraceSource> juntamente com um arquivo de configuração de aplicativo.  É possível, embora não recomendado, rastrear usando um <xref:System.Diagnostics.TraceSource> sem o uso de um arquivo de configuração. Para obter informações sobre rastreamento sem um arquivo de configuração, consulte [Como criar e inicializar origens de rastreamento](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).  
  
### <a name="to-create-and-initialize-your-trace-source"></a>Criar e inicializar a origem do rastreamento  
  
1.  A primeira etapa para instrumentar um aplicativo com o rastreamento é criar uma origem do rastreamento. Em projetos grandes com vários componentes, você pode criar uma origem do rastreamento separada para cada componente. A prática recomendada é usar o nome do aplicativo como o nome da origem do rastreamento. Isso tornará mais fácil manter os rastreamentos diferentes separados. O código a seguir cria uma nova origem do rastreamento (`mySource)`) e chama um método (`Activity1`) que rastreia eventos.  As mensagens de rastreamento são gravadas pelo ouvinte de rastreamento padrão.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>Criar e inicializar ouvintes de rastreamento e filtros  
  
1.  O código no primeiro procedimento não identifica programaticamente nenhum ouvinte de rastreamento ou filtro. O resultado do código, por si só, é que as mensagens de rastreamento são gravadas para o ouvinte de rastreamento padrão. Para configurar os ouvintes de rastreamento específicos e os respectivos filtros associados, edite o arquivo de configuração que corresponde ao nome do seu aplicativo. Nesse arquivo, você pode adicionar ou remover um ouvinte, definir as propriedades e o filtro para um ouvinte ou remover ouvintes. O exemplo de arquivo de configuração a seguir mostra como inicializar um ouvinte de rastreamento do console e um ouvinte de rastreamento do text writer na origem de rastreamento criada no procedimento anterior. Além de configurar os ouvintes de rastreamento, o arquivo de configuração cria filtros para ambos os ouvintes e cria uma opção de origem para a origem de rastreamento. Duas técnicas são mostradas para a adição de ouvintes de rastreamento: adicionar o ouvinte diretamente à origem de rastreamento e adicionar um ouvinte à coleção de ouvintes compartilhados e, em seguida, adicioná-lo pelo nome à origem de rastreamento. Os filtros identificados para os dois ouvintes são inicializados com níveis de origem diferentes. Isso resulta na gravação de algumas mensagens por apenas um dos dois ouvintes.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>Para alterar o nível no qual um ouvinte grava uma mensagem de rastreamento  
  
1.  O arquivo de configuração inicializa as configurações para a origem de rastreamento no momento em que o aplicativo é inicializado. Para alterar essas configurações, você deve alterar o arquivo de configuração e reiniciar o aplicativo ou atualizar o aplicativo de forma programática usando o método <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=fullName>. O aplicativo pode alterar dinamicamente as propriedades definidas pelo arquivo de configuração para substituir as configurações especificadas pelo usuário.  Por exemplo, talvez você deseje assegurar que as mensagens críticas sejam sempre enviadas para um arquivo de texto, independentemente das definições de configuração atuais.  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified   
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =   
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures   
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners   
                // for all event types. This statement will override   
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,   
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,   
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 <xref:System.Diagnostics.ConsoleTraceListener>   
 <xref:System.Diagnostics.EventTypeFilter>   
 [Como criar e inicializar origens de rastreamento](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)   
 [Ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/trace-listeners.md)

