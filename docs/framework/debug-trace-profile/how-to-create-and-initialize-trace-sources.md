---
title: 'Como: criar e inicializar fontes de rastreamento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 346fb3399993246eb8d90f7fa900ab382ae12c71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194884"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="003c4-102">Como: criar e inicializar fontes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="003c4-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="003c4-103">A classe <xref:System.Diagnostics.TraceSource> é usada por aplicativos para produzir rastreamentos que podem ser associados ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="003c4-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <xref:System.Diagnostics.TraceSource> <span data-ttu-id="003c4-104">fornece métodos de rastreamento que permitem que você facilmente os eventos de rastreamento, dados de rastreamento e emitir rastreamentos informativos.</span><span class="sxs-lookup"><span data-stu-id="003c4-104">provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="003c4-105">A saída de rastreamento de <xref:System.Diagnostics.TraceSource> pode ser criada e inicializada com ou sem o uso de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="003c4-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="003c4-106">Este tópico fornece instruções para ambas as opções.</span><span class="sxs-lookup"><span data-stu-id="003c4-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="003c4-107">No entanto, recomendamos o uso de arquivos de configuração para facilitar a reconfiguração dos rastreamentos produzidos por origens de rastreamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="003c4-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="003c4-108">Para criar e inicializar uma origem de rastreamento usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="003c4-108">To create and initialize a trace source using a configuration file</span></span>  
  
1.  <span data-ttu-id="003c4-109">Crie um projeto de aplicativo de console do Visual Studio e substitua o código fornecido pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="003c4-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="003c4-110">Esse código registra erros e avisos e gera alguns deles no console e outros no arquivo myListener que é criado pelas entradas no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="003c4-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  <span data-ttu-id="003c4-111">Adicione um arquivo de configuração de aplicativo, caso um não esteja presente, ao projeto para inicializar a origem de rastreamento chamada `TraceSourceApp` no exemplo de código da etapa 1.</span><span class="sxs-lookup"><span data-stu-id="003c4-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3.  <span data-ttu-id="003c4-112">Substitua o conteúdo do arquivo de configuração padrão pelas configurações a seguir para inicializar um ouvinte de rastreamento do console e um ouvinte de rastreamento do text writer na origem de rastreamento que foi criada na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="003c4-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
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
  
     <span data-ttu-id="003c4-113">Além de configurar os ouvintes de rastreamento, o arquivo de configuração cria filtros para ambos os ouvintes e cria uma opção de origem para a origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="003c4-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="003c4-114">Duas técnicas são mostradas para a adição de ouvintes de rastreamento: adicionar o ouvinte diretamente à origem de rastreamento e adicionar um ouvinte à coleção de ouvintes compartilhados e, em seguida, adicioná-lo pelo nome à origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="003c4-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="003c4-115">Os filtros identificados para os dois ouvintes são inicializados com níveis de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="003c4-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="003c4-116">Isso resulta na gravação de algumas mensagens por apenas um dos dois ouvintes.</span><span class="sxs-lookup"><span data-stu-id="003c4-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="003c4-117">O arquivo de configuração inicializa as configurações para a origem de rastreamento no momento em que o aplicativo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="003c4-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="003c4-118">O aplicativo pode alterar dinamicamente as propriedades definidas pelo arquivo de configuração para substituir as configurações especificadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="003c4-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="003c4-119">Por exemplo, talvez você deseje garantir que as mensagens críticas sejam sempre enviadas para um arquivo de texto, independentemente das definições de configuração atuais.</span><span class="sxs-lookup"><span data-stu-id="003c4-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="003c4-120">O exemplo de código demonstra como substituir as configurações do arquivo de configuração para garantir que as mensagens críticas sejam geradas para os ouvintes de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="003c4-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="003c4-121">A alteração das configurações do arquivo de configuração durante a execução do aplicativo não altera as configurações iniciais.</span><span class="sxs-lookup"><span data-stu-id="003c4-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="003c4-122">Para alterar as configurações, reinicie o aplicativo ou atualize o aplicativo de forma programática usando o método <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="003c4-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="003c4-123">Para inicializar origens de rastreamento, ouvintes e filtros sem um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="003c4-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="003c4-124">Use o exemplo de código a seguir para habilitar o rastreamento por meio de uma origem de rastreamento sem usar um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="003c4-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="003c4-125">Essa não é uma prática recomendada, mas pode haver circunstâncias em que você não deseja depender dos arquivos de configuração para garantir o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="003c4-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="003c4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="003c4-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="003c4-127">Rastreamento e instrumentação de aplicativos</span><span class="sxs-lookup"><span data-stu-id="003c4-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
