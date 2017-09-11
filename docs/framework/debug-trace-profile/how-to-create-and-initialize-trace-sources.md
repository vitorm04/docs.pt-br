---
title: Como criar e inicializar fontes de rastreamento
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
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
caps.latest.revision: 10
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1df5f06afaf23795a0efd6af763e29193ba82d90
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="0a066-102">Como criar e inicializar fontes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="0a066-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="0a066-103">A classe <xref:System.Diagnostics.TraceSource> é usada por aplicativos para produzir rastreamentos que podem ser associados ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0a066-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="0a066-104"><xref:System.Diagnostics.TraceSource> fornece métodos de rastreamento que permitem rastrear eventos com facilidade, rastrear dados e emitir rastreamentos informativos.</span><span class="sxs-lookup"><span data-stu-id="0a066-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="0a066-105">A saída de rastreamento de <xref:System.Diagnostics.TraceSource> pode ser criada e inicializada com ou sem o uso de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="0a066-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="0a066-106">Este tópico fornece instruções para ambas as opções.</span><span class="sxs-lookup"><span data-stu-id="0a066-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="0a066-107">No entanto, recomendamos o uso de arquivos de configuração para facilitar a reconfiguração dos rastreamentos produzidos por origens de rastreamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0a066-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="0a066-108">Para criar e inicializar uma origem de rastreamento usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="0a066-108">To create and initialize a trace source using a configuration file</span></span>  
  
1.  <span data-ttu-id="0a066-109">Crie um projeto de aplicativo de console do Visual Studio e substitua o código fornecido pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0a066-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="0a066-110">Esse código registra erros e avisos e gera alguns deles no console e outros no arquivo myListener que é criado pelas entradas no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0a066-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     <span data-ttu-id="0a066-111">[!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]  [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="0a066-111">[!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]  [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]</span></span>  
  
2.  <span data-ttu-id="0a066-112">Adicione um arquivo de configuração de aplicativo, caso um não esteja presente, ao projeto para inicializar a origem de rastreamento chamada `TraceSourceApp` no exemplo de código da etapa 1.</span><span class="sxs-lookup"><span data-stu-id="0a066-112">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3.  <span data-ttu-id="0a066-113">Substitua o conteúdo do arquivo de configuração padrão pelas configurações a seguir para inicializar um ouvinte de rastreamento do console e um ouvinte de rastreamento do text writer na origem de rastreamento que foi criada na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="0a066-113">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="0a066-114">Além de configurar os ouvintes de rastreamento, o arquivo de configuração cria filtros para ambos os ouvintes e cria uma opção de origem para a origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a066-114">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="0a066-115">Duas técnicas são mostradas para a adição de ouvintes de rastreamento: adicionar o ouvinte diretamente à origem de rastreamento e adicionar um ouvinte à coleção de ouvintes compartilhados e, em seguida, adicioná-lo pelo nome à origem de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a066-115">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="0a066-116">Os filtros identificados para os dois ouvintes são inicializados com níveis de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="0a066-116">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="0a066-117">Isso resulta na gravação de algumas mensagens por apenas um dos dois ouvintes.</span><span class="sxs-lookup"><span data-stu-id="0a066-117">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="0a066-118">O arquivo de configuração inicializa as configurações para a origem de rastreamento no momento em que o aplicativo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="0a066-118">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="0a066-119">O aplicativo pode alterar dinamicamente as propriedades definidas pelo arquivo de configuração para substituir as configurações especificadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0a066-119">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="0a066-120">Por exemplo, talvez você deseje garantir que as mensagens críticas sejam sempre enviadas para um arquivo de texto, independentemente das definições de configuração atuais.</span><span class="sxs-lookup"><span data-stu-id="0a066-120">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="0a066-121">O exemplo de código demonstra como substituir as configurações do arquivo de configuração para garantir que as mensagens críticas sejam geradas para os ouvintes de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a066-121">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="0a066-122">A alteração das configurações do arquivo de configuração durante a execução do aplicativo não altera as configurações iniciais.</span><span class="sxs-lookup"><span data-stu-id="0a066-122">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="0a066-123">Para alterar as configurações, reinicie o aplicativo ou atualize o aplicativo de forma programática usando o método <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="0a066-123">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=fullName> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="0a066-124">Para inicializar origens de rastreamento, ouvintes e filtros sem um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="0a066-124">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="0a066-125">Use o exemplo de código a seguir para habilitar o rastreamento por meio de uma origem de rastreamento sem usar um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0a066-125">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="0a066-126">Essa não é uma prática recomendada, mas pode haver circunstâncias em que você não deseja depender dos arquivos de configuração para garantir o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a066-126">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     <span data-ttu-id="0a066-127">[!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]  [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="0a066-127">[!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]  [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a066-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a066-128">See Also</span></span>  
 <span data-ttu-id="0a066-129"><xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="0a066-129"><xref:System.Diagnostics.TraceSource></span></span>   
 <span data-ttu-id="0a066-130"><xref:System.Diagnostics.TextWriterTraceListener></span><span class="sxs-lookup"><span data-stu-id="0a066-130"><xref:System.Diagnostics.TextWriterTraceListener></span></span>   
 <span data-ttu-id="0a066-131"><xref:System.Diagnostics.ConsoleTraceListener></span><span class="sxs-lookup"><span data-stu-id="0a066-131"><xref:System.Diagnostics.ConsoleTraceListener></span></span>   
 <span data-ttu-id="0a066-132"><xref:System.Diagnostics.EventTypeFilter></span><span class="sxs-lookup"><span data-stu-id="0a066-132"><xref:System.Diagnostics.EventTypeFilter></span></span>   
 [<span data-ttu-id="0a066-133">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="0a066-133">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)

