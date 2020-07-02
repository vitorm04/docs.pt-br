---
title: MDA streamWriterBufferedDataLost
description: Examine o MDA (Assistente de depuração gerenciada) streamWriterBufferedDataLost, que pode ser ativado se um StreamWriter não gravar os últimos 1 a 4 KB de dados em um arquivo.
ms.date: 03/30/2017
helpviewer_keywords:
- StreamWriter class, data buffering problems
- managed debugging assistants (MDAs), StreamWriter data buffering
- buffers, StreamWriter problems
- MDAs (managed debugging assistants), StreamWriter data buffering
- StreamWriter buffered data lost
- data buffering problems
- streamWriterBufferedDataLost MDA
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
ms.openlocfilehash: 0c10ea6bb9dc0aaafa2ac1798696579af7592895
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803476"
---
# <a name="streamwriterbuffereddatalost-mda"></a><span data-ttu-id="064e7-103">MDA streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="064e7-103">streamWriterBufferedDataLost MDA</span></span>
<span data-ttu-id="064e7-104">O MDA (assistente para depuração gerenciada) de `streamWriterBufferedDataLost` é ativado quando um <xref:System.IO.StreamWriter> é gravado, mas o método <xref:System.IO.StreamWriter.Flush%2A> ou <xref:System.IO.StreamWriter.Close%2A> não é chamado posteriormente antes da destruição da instância do <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="064e7-104">The `streamWriterBufferedDataLost` managed debugging assistant (MDA) is activated when a <xref:System.IO.StreamWriter> is written to, but the <xref:System.IO.StreamWriter.Flush%2A> or <xref:System.IO.StreamWriter.Close%2A> method is not subsequently called before the instance of the <xref:System.IO.StreamWriter> is destroyed.</span></span> <span data-ttu-id="064e7-105">Quando esse MDA está habilitado, o runtime determina se todos os dados armazenados em buffer ainda existem no <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="064e7-105">When this MDA is enabled, the runtime determines whether any buffered data still exists within the <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="064e7-106">Se os dados armazenados em buffer existirem, o MDA será ativado.</span><span class="sxs-lookup"><span data-stu-id="064e7-106">If buffered data does exist, the MDA is activated.</span></span> <span data-ttu-id="064e7-107">A chamada aos métodos <xref:System.GC.Collect%2A> e <xref:System.GC.WaitForPendingFinalizers%2A> pode forçar os finalizadores a serem executados.</span><span class="sxs-lookup"><span data-stu-id="064e7-107">Calling the <xref:System.GC.Collect%2A> and <xref:System.GC.WaitForPendingFinalizers%2A> methods can force finalizers to run.</span></span> <span data-ttu-id="064e7-108">Caso contrário, os finalizadores serão executados em horários aparentemente arbitrários e, possivelmente, não na saída do processo.</span><span class="sxs-lookup"><span data-stu-id="064e7-108">Finalizers will otherwise run at seemingly arbitrary times, and possibly not at all on process exit.</span></span> <span data-ttu-id="064e7-109">A execução explícita dos finalizadores com esse MDA habilitado ajudará a reproduzir esse tipo de problema de maneira mais confiável.</span><span class="sxs-lookup"><span data-stu-id="064e7-109">Explicitly running finalizers with this MDA enabled will help to more reliably reproduce this type of problem.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="064e7-110">Sintomas</span><span class="sxs-lookup"><span data-stu-id="064e7-110">Symptoms</span></span>  
 <span data-ttu-id="064e7-111">Um <xref:System.IO.StreamWriter> não grava os últimos 1-4 KB de dados em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="064e7-111">A <xref:System.IO.StreamWriter> does not write the last 1–4 KB of data to a file.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="064e7-112">Causa</span><span class="sxs-lookup"><span data-stu-id="064e7-112">Cause</span></span>  
 <span data-ttu-id="064e7-113">O <xref:System.IO.StreamWriter> armazena os dados em buffer internamente, o que exige que o método <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> seja chamado para gravar os dados em buffer no armazenamento de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="064e7-113">The <xref:System.IO.StreamWriter> buffers data internally, which requires that the <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> method be called to write the buffered data to the underlying data store.</span></span> <span data-ttu-id="064e7-114">Se <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> não for chamado corretamente, os dados armazenados em buffer na instância <xref:System.IO.StreamWriter> poderão não ser gravados como esperado.</span><span class="sxs-lookup"><span data-stu-id="064e7-114">If <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> is not appropriately called, data buffered in the <xref:System.IO.StreamWriter> instance might not be written as expected.</span></span>  
  
 <span data-ttu-id="064e7-115">Veja a seguir um exemplo de um código mal escrito que esse MDA deverá capturar.</span><span class="sxs-lookup"><span data-stu-id="064e7-115">The following is an example of poorly written code that this MDA should catch.</span></span>  
  
```csharp  
// Poorly written code.  
void Write()
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 <span data-ttu-id="064e7-116">O código anterior ativará esse MDA de maneira mais confiável se uma coleta de lixo for disparada e, em seguida, suspensa até a conclusão dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="064e7-116">The preceding code will activate this MDA more reliably if a garbage collection is triggered and then suspended until finalizers have finished.</span></span> <span data-ttu-id="064e7-117">Para rastrear esse tipo de problema, adicione o código a seguir ao final do método anterior em um build de depuração.</span><span class="sxs-lookup"><span data-stu-id="064e7-117">To track down this type of problem, you can add the following code to the end of the preceding method in a debug build.</span></span> <span data-ttu-id="064e7-118">Isso ajudará a ativar o MDA de maneira confiável, mas obviamente, não corrige a causa do problema.</span><span class="sxs-lookup"><span data-stu-id="064e7-118">This will help to reliably activate the MDA, but of course it does not fix the cause of the problem.</span></span>  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a><span data-ttu-id="064e7-119">Resolução</span><span class="sxs-lookup"><span data-stu-id="064e7-119">Resolution</span></span>  
 <span data-ttu-id="064e7-120">Chame <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> no <xref:System.IO.StreamWriter> antes de fechar um aplicativo ou qualquer bloco de códigos que tem uma instância de um <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="064e7-120">Make sure you call <xref:System.IO.StreamWriter.Close%2A> or <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> before closing an application or any code block that has an instance of a <xref:System.IO.StreamWriter>.</span></span> <span data-ttu-id="064e7-121">Um dos melhores mecanismos para fazer isso é criar a instância com um bloco `using` do C# (`Using` no Visual Basic), o que garantirá a invocação do método <xref:System.IO.StreamWriter.Dispose%2A> para o gravador, resultando no fechamento correto da instância.</span><span class="sxs-lookup"><span data-stu-id="064e7-121">One of the best mechanisms for achieving this is creating the instance with a C# `using` block (`Using` in Visual Basic), which will ensure the <xref:System.IO.StreamWriter.Dispose%2A> method for the writer is invoked, resulting in the instance being correctly closed.</span></span>  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))
{  
    sw.WriteLine("Data");  
}  
```  
  
 <span data-ttu-id="064e7-122">O código a seguir mostra a mesma solução, usando `try/finally` em vez de `using`.</span><span class="sxs-lookup"><span data-stu-id="064e7-122">The following code shows the same solution, using `try/finally` instead of `using`.</span></span>  
  
```csharp
StreamWriter sw;  
try
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 <span data-ttu-id="064e7-123">Se nenhuma dessas soluções puder ser usada (por exemplo, se um <xref:System.IO.StreamWriter> for armazenado em uma variável estática e não for possível executar o código facilmente ao final de seu tempo de vida), a chamada a <xref:System.IO.StreamWriter.Flush%2A> no <xref:System.IO.StreamWriter> após seu último uso ou a configuração da propriedade <xref:System.IO.StreamWriter.AutoFlush%2A> como `true` antes de seu primeiro uso deverá evitar esse problema.</span><span class="sxs-lookup"><span data-stu-id="064e7-123">If neither of these solutions can be used (for example, if a <xref:System.IO.StreamWriter> is stored in a static variable and you cannot easily run code at the end of its lifetime), then calling <xref:System.IO.StreamWriter.Flush%2A> on the <xref:System.IO.StreamWriter> after its last use or setting the <xref:System.IO.StreamWriter.AutoFlush%2A> property to `true` before its first use should avoid this problem.</span></span>  
  
```csharp
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="064e7-124">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="064e7-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="064e7-125">Esse MDA não tem nenhum efeito sobre o runtime.</span><span class="sxs-lookup"><span data-stu-id="064e7-125">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="064e7-126">Saída</span><span class="sxs-lookup"><span data-stu-id="064e7-126">Output</span></span>  
 <span data-ttu-id="064e7-127">Uma mensagem que indica que essa violação ocorreu.</span><span class="sxs-lookup"><span data-stu-id="064e7-127">A message indicating that this violation occurred.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="064e7-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="064e7-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="064e7-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="064e7-129">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="064e7-130">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="064e7-130">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
