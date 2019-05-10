---
title: Ouvintes de rastreamento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5657e55856845404c5f8f063bd69d51614a234c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614277"
---
# <a name="trace-listeners"></a><span data-ttu-id="9d66e-102">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9d66e-102">Trace Listeners</span></span>
<span data-ttu-id="9d66e-103">Ao usar **Trace**, **Debug** e <xref:System.Diagnostics.TraceSource>, você deve ter um mecanismo para coletar e registrar as mensagens que são enviadas.</span><span class="sxs-lookup"><span data-stu-id="9d66e-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="9d66e-104">As mensagens de rastreamento são recebidas por *ouvintes*.</span><span class="sxs-lookup"><span data-stu-id="9d66e-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="9d66e-105">A finalidade de um ouvinte é coletar, armazenar e rotear mensagens de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9d66e-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="9d66e-106">Os ouvintes direcionam a saída de rastreamento para um destino apropriado, como um log, uma janela ou um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="9d66e-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="9d66e-107">Os ouvintes estão disponíveis para as classes **Debug**, **Trace** e <xref:System.Diagnostics.TraceSource>, cada uma das quais pode enviar sua saída para a uma variedade de objetos de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="9d66e-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="9d66e-108">Veja a seguir os ouvintes predefinidos mais usados:</span><span class="sxs-lookup"><span data-stu-id="9d66e-108">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="9d66e-109">Um <xref:System.Diagnostics.TextWriterTraceListener> redireciona a saída para uma instância da classe <xref:System.IO.TextWriter> ou para qualquer coisa que seja uma classe <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="9d66e-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="9d66e-110">Ele também pode gravar no console ou em um arquivo, pois eles são classes <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="9d66e-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="9d66e-111">Um <xref:System.Diagnostics.EventLogTraceListener> redireciona a saída para um log de eventos.</span><span class="sxs-lookup"><span data-stu-id="9d66e-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="9d66e-112">Um <xref:System.Diagnostics.DefaultTraceListener> emite mensagens **Write** e **WriteLine** para os métodos **OutputDebugString** e **Debugger.Log**.</span><span class="sxs-lookup"><span data-stu-id="9d66e-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="9d66e-113">No Visual Studio, isso faz com que as mensagens de depuração sejam exibidas na janela de Saída.</span><span class="sxs-lookup"><span data-stu-id="9d66e-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="9d66e-114">Mensagens **Fail** e **Assert** com falha também são emitidas para a API do Windows **OutputDebugString** e o método **Debugger.Log**, e também fazem com que uma caixa de mensagem seja exibida.</span><span class="sxs-lookup"><span data-stu-id="9d66e-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="9d66e-115">Esse comportamento é o comportamento padrão de mensagens **Debug** e **Trace**, pois **DefaultTraceListener** é incluído automaticamente em cada coleção `Listeners` e é o único ouvinte incluído automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9d66e-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="9d66e-116">Um <xref:System.Diagnostics.ConsoleTraceListener> direciona a saída do rastreamento ou da depuração para a saída padrão ou para o fluxo de erro padrão.</span><span class="sxs-lookup"><span data-stu-id="9d66e-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="9d66e-117">Um <xref:System.Diagnostics.DelimitedListTraceListener> direciona a saída de rastreamento ou de depuração para um text writer, como um gravador de fluxo ou para um fluxo, como um fluxo de arquivos.</span><span class="sxs-lookup"><span data-stu-id="9d66e-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="9d66e-118">A saída de rastreamento está em um formato de texto delimitado que usa o delimitador especificado pela propriedade <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d66e-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="9d66e-119">Um <xref:System.Diagnostics.XmlWriterTraceListener> direciona a saída de rastreamento ou de depuração como dados codificados em XML para um <xref:System.IO.TextWriter> ou <xref:System.IO.Stream>, como um <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="9d66e-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="9d66e-120">Se você deseja que qualquer ouvinte além do <xref:System.Diagnostics.DefaultTraceListener> receba a saída **Debug**, **Trace** e <xref:System.Diagnostics.TraceSource>, adicione-o à coleção `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="9d66e-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="9d66e-121">Para obter mais informações, confira [Como: Criar e inicializar ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) e [como: Usar TraceSource e filtros com ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="9d66e-121">For more information, see [How to: Create and Initialize Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="9d66e-122">Qualquer ouvinte da coleção **Listeners** obtém as mesmas mensagens dos métodos de saída de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9d66e-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="9d66e-123">Por exemplo, suponha que você configure dois ouvintes: um **TextWriterTraceListener** e um **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="9d66e-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="9d66e-124">Cada ouvinte recebe a mesma mensagem.</span><span class="sxs-lookup"><span data-stu-id="9d66e-124">Each listener receives the same message.</span></span> <span data-ttu-id="9d66e-125">O **TextWriterTraceListener** direcionará sua saída para um fluxo e o **EventLogTraceListener** direcionará sua saída para um log de eventos.</span><span class="sxs-lookup"><span data-stu-id="9d66e-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="9d66e-126">O exemplo a seguir mostra como enviar a saída para a coleção **Listeners**.</span><span class="sxs-lookup"><span data-stu-id="9d66e-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="9d66e-127">A depuração e o rastreamento compartilham a mesma coleção **Listeners**. Portanto, se você adicionar um objeto de ouvinte a uma coleção **Debug.Listeners** no aplicativo, ele será adicionado à coleção **Trace.Listeners** também.</span><span class="sxs-lookup"><span data-stu-id="9d66e-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="9d66e-128">O exemplo a seguir mostra como usar um ouvinte para enviar informações de rastreamento para um console:</span><span class="sxs-lookup"><span data-stu-id="9d66e-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="9d66e-129">Ouvintes definidos pelo desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="9d66e-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="9d66e-130">Você pode definir seus próprios ouvintes herdando a classe base **TraceListener** e substituindo seus métodos por métodos personalizados.</span><span class="sxs-lookup"><span data-stu-id="9d66e-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="9d66e-131">Para obter mais informações sobre como criar ouvintes definidos pelo desenvolvedor, consulte <xref:System.Diagnostics.TraceListener> na referência do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d66e-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d66e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d66e-132">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="9d66e-133">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="9d66e-133">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="9d66e-134">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9d66e-134">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
