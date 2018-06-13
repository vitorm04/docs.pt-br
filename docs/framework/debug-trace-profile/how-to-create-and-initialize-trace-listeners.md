---
title: Como criar e inicializar ouvintes de rastreamento
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
ms.openlocfilehash: 943621b953fbe158b3be6ae0695ba7692b7c517f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389194"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a>Como criar e inicializar ouvintes de rastreamento
As classes <xref:System.Diagnostics.Debug?displayProperty=nameWithType> e <xref:System.Diagnostics.Trace?displayProperty=nameWithType> enviam mensagens para objetos chamados ouvintes, que recebem e processam essas mensagens. Um ouvinte desse tipo, o <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, é criado e inicializado automaticamente quando a depuração ou o rastreamento é habilitado. Se você desejar que a saída <xref:System.Diagnostics.Trace> ou <xref:System.Diagnostics.Debug> seja direcionada para outras fontes, crie e inicialize ouvintes de rastreamento adicionais.  
  
 Os ouvintes criados devem refletir as necessidades do aplicativo. Por exemplo, se desejar obter um registro de texto de toda a saída de rastreamento, crie um ouvinte <xref:System.Diagnostics.TextWriterTraceListener>, que grava toda a saída para um novo arquivo de texto quando ele é habilitado. Por outro lado, se desejar exibir a saída somente durante a execução do aplicativo, crie um ouvinte <xref:System.Diagnostics.ConsoleTraceListener>, que direciona toda a saída para uma janela do console. O <xref:System.Diagnostics.EventLogTraceListener> pode direcionar a saída de rastreamento para um log de eventos. Para obter mais informações, consulte [Ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Crie ouvintes de rastreamento em um [arquivo de configuração de aplicativo](../../../docs/framework/configure-apps/index.md) ou no código. Recomendamos o uso de arquivos de configuração de aplicativo, porque eles permitem adicionar, modificar ou remover ouvintes de rastreamento sem a necessidade de alterar o código.  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a>Para criar e usar um ouvinte de rastreamento usando um arquivo de configuração  
  
1.  Declare o ouvinte de rastreamento no arquivo de configuração de aplicativo. Se o ouvinte que você está criando exigir outros objetos, declare-os também. O exemplo a seguir mostra como criar um ouvinte chamado `myListener` que grava no arquivo de texto `TextWriterOutput.log`.  
  
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
  
2.  Use a classe <xref:System.Diagnostics.Trace> no código para gravar uma mensagem nos ouvintes de rastreamento.  
  
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
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a>Para criar e usar um ouvinte de rastreamento no código  
  
-   Adicione o ouvinte de rastreamento à coleção <xref:System.Diagnostics.Trace.Listeners%2A> e envie informações de rastreamento para os ouvintes.  
  
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
  
     - ou –  
  
-   Se você não desejar que o ouvinte receba a saída de rastreamento, não adicione-a à coleção <xref:System.Diagnostics.Trace.Listeners%2A>. Emita a saída por meio de um ouvinte independente da coleção <xref:System.Diagnostics.Trace.Listeners%2A> chamando os próprios métodos de saída do ouvinte. O exemplo a seguir mostra como gravar uma linha em um ouvinte que não está na coleção <xref:System.Diagnostics.Trace.Listeners%2A>.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Opções de rastreamento](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Como adicionar instruções de rastreamento ao código do aplicativo](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Rastreando e instrumentando aplicativos](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
