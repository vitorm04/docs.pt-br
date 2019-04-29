---
title: 'Como: criar e inicializar ouvintes de rastreamento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea5db2ba1060479f55bbd7f67266d36085a2535f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754369"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="119e9-102">Como: criar e inicializar ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="119e9-102">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="119e9-103">As classes <xref:System.Diagnostics.Debug?displayProperty=nameWithType> e <xref:System.Diagnostics.Trace?displayProperty=nameWithType> enviam mensagens para objetos chamados ouvintes, que recebem e processam essas mensagens.</span><span class="sxs-lookup"><span data-stu-id="119e9-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="119e9-104">Um ouvinte desse tipo, o <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, é criado e inicializado automaticamente quando a depuração ou o rastreamento é habilitado.</span><span class="sxs-lookup"><span data-stu-id="119e9-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="119e9-105">Se você desejar que a saída <xref:System.Diagnostics.Trace> ou <xref:System.Diagnostics.Debug> seja direcionada para outras fontes, crie e inicialize ouvintes de rastreamento adicionais.</span><span class="sxs-lookup"><span data-stu-id="119e9-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="119e9-106">Os ouvintes criados devem refletir as necessidades do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="119e9-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="119e9-107">Por exemplo, se desejar obter um registro de texto de toda a saída de rastreamento, crie um ouvinte <xref:System.Diagnostics.TextWriterTraceListener>, que grava toda a saída para um novo arquivo de texto quando ele é habilitado.</span><span class="sxs-lookup"><span data-stu-id="119e9-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="119e9-108">Por outro lado, se desejar exibir a saída somente durante a execução do aplicativo, crie um ouvinte <xref:System.Diagnostics.ConsoleTraceListener>, que direciona toda a saída para uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="119e9-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="119e9-109">O <xref:System.Diagnostics.EventLogTraceListener> pode direcionar a saída de rastreamento para um log de eventos.</span><span class="sxs-lookup"><span data-stu-id="119e9-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="119e9-110">Para obter mais informações, consulte [Ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="119e9-110">For more information, see [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span></span>

<span data-ttu-id="119e9-111">Crie ouvintes de rastreamento em um [arquivo de configuração de aplicativo](../../../docs/framework/configure-apps/index.md) ou no código.</span><span class="sxs-lookup"><span data-stu-id="119e9-111">You can create trace listeners in an [application configuration file](../../../docs/framework/configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="119e9-112">Recomendamos o uso de arquivos de configuração de aplicativo, porque eles permitem adicionar, modificar ou remover ouvintes de rastreamento sem a necessidade de alterar o código.</span><span class="sxs-lookup"><span data-stu-id="119e9-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="119e9-113">Para criar e usar um ouvinte de rastreamento usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="119e9-113">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="119e9-114">Declare o ouvinte de rastreamento no arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="119e9-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="119e9-115">Se o ouvinte que você está criando exigir outros objetos, declare-os também.</span><span class="sxs-lookup"><span data-stu-id="119e9-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="119e9-116">O exemplo a seguir mostra como criar um ouvinte chamado `myListener` que grava no arquivo de texto `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="119e9-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

    ```xml
    <configuration>
      <system.diagnostics>
        <trace autoflush="false" indentsize="4">
          <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />
            <remove name="Default" />
          </listeners>
        </trace>
      </system.diagnostics>
    </configuration>
    ```

2. <span data-ttu-id="119e9-117">Use a classe <xref:System.Diagnostics.Trace> no código para gravar uma mensagem nos ouvintes de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="119e9-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

    ```vb
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="119e9-118">Para criar e usar um ouvinte de rastreamento no código</span><span class="sxs-lookup"><span data-stu-id="119e9-118">To create and use a trace listener in code</span></span>

- <span data-ttu-id="119e9-119">Adicione o ouvinte de rastreamento à coleção <xref:System.Diagnostics.Trace.Listeners%2A> e envie informações de rastreamento para os ouvintes.</span><span class="sxs-lookup"><span data-stu-id="119e9-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

    ```vb
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

    <span data-ttu-id="119e9-120">\- ou -</span><span class="sxs-lookup"><span data-stu-id="119e9-120">\- or -</span></span>

- <span data-ttu-id="119e9-121">Se você não desejar que o ouvinte receba a saída de rastreamento, não adicione-a à coleção <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="119e9-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="119e9-122">Emita a saída por meio de um ouvinte independente da coleção <xref:System.Diagnostics.Trace.Listeners%2A> chamando os próprios métodos de saída do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="119e9-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="119e9-123">O exemplo a seguir mostra como gravar uma linha em um ouvinte que não está na coleção <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="119e9-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

    ```vb
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")
    myListener.WriteLine("Test message.")
    ' You must close or flush the trace listener to empty the output buffer.
    myListener.Flush()
    ```

    ```csharp
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");
    myListener.WriteLine("Test message.");
    // You must close or flush the trace listener to empty the output buffer.
    myListener.Flush();
    ```

## <a name="see-also"></a><span data-ttu-id="119e9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="119e9-124">See also</span></span>

- [<span data-ttu-id="119e9-125">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="119e9-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="119e9-126">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="119e9-126">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="119e9-127">Como: Adicionar instruções de rastreamento ao código do aplicativo</span><span class="sxs-lookup"><span data-stu-id="119e9-127">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="119e9-128">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="119e9-128">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
