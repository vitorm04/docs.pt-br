---
title: MDA streamWriterBufferedDataLost
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b35e6ab4de699126b4b3b5f74d7a9a8dacfa4a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117385"
---
# <a name="streamwriterbuffereddatalost-mda"></a>MDA streamWriterBufferedDataLost
O MDA (assistente para depuração gerenciada) de `streamWriterBufferedDataLost` é ativado quando um <xref:System.IO.StreamWriter> é gravado, mas o método <xref:System.IO.StreamWriter.Flush%2A> ou <xref:System.IO.StreamWriter.Close%2A> não é chamado posteriormente antes da destruição da instância do <xref:System.IO.StreamWriter>. Quando esse MDA está habilitado, o tempo de execução determina se todos os dados armazenados em buffer ainda existem no <xref:System.IO.StreamWriter>. Se os dados armazenados em buffer existirem, o MDA será ativado. A chamada aos métodos <xref:System.GC.Collect%2A> e <xref:System.GC.WaitForPendingFinalizers%2A> pode forçar os finalizadores a serem executados. Caso contrário, os finalizadores serão executados em horários aparentemente arbitrários e, possivelmente, não na saída do processo. A execução explícita dos finalizadores com esse MDA habilitado ajudará a reproduzir esse tipo de problema de maneira mais confiável.  
  
## <a name="symptoms"></a>Sintomas  
 Um <xref:System.IO.StreamWriter> não grava os últimos 1-4 KB de dados em um arquivo.  
  
## <a name="cause"></a>Causa  
 O <xref:System.IO.StreamWriter> armazena os dados em buffer internamente, o que exige que o método <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> seja chamado para gravar os dados em buffer no armazenamento de dados subjacente. Se <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> não for chamado corretamente, os dados armazenados em buffer na instância <xref:System.IO.StreamWriter> poderão não ser gravados como esperado.  
  
 Veja a seguir um exemplo de um código mal escrito que esse MDA deverá capturar.  
  
```csharp  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 O código anterior ativará esse MDA de maneira mais confiável se uma coleta de lixo for disparada e, em seguida, suspensa até a conclusão dos finalizadores. Para rastrear esse tipo de problema, adicione o código a seguir ao final do método anterior em um build de depuração. Isso ajudará a ativar o MDA de maneira confiável, mas obviamente, não corrige a causa do problema.  
  
```csharp
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## <a name="resolution"></a>Resolução  
 Chame <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> no <xref:System.IO.StreamWriter> antes de fechar um aplicativo ou qualquer bloco de códigos que tem uma instância de um <xref:System.IO.StreamWriter>. Um dos melhores mecanismos para fazer isso é criar a instância com um bloco `using` do C# (`Using` no Visual Basic), o que garantirá a invocação do método <xref:System.IO.StreamWriter.Dispose%2A> para o gravador, resultando no fechamento correto da instância.  
  
```csharp
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 O código a seguir mostra a mesma solução, usando `try/finally` em vez de `using`.  
  
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
  
 Se nenhuma dessas soluções puder ser usada (por exemplo, se um <xref:System.IO.StreamWriter> for armazenado em uma variável estática e não for possível executar o código facilmente ao final de seu tempo de vida), a chamada a <xref:System.IO.StreamWriter.Flush%2A> no <xref:System.IO.StreamWriter> após seu último uso ou a configuração da propriedade <xref:System.IO.StreamWriter.AutoFlush%2A> como `true` antes de seu primeiro uso deverá evitar esse problema.  
  
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
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem nenhum efeito sobre o tempo de execução.  
  
## <a name="output"></a>Saída  
 Uma mensagem que indica que essa violação ocorreu.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO.StreamWriter>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
