---
title: "Práticas recomendadas para a implementação do padrão assíncrono baseado em evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 4acd2094-4f46-4eff-9190-92d0d9ff47db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6a98c6854bc935eb8b319bd8a26dba8f12380ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Práticas recomendadas para a implementação do padrão assíncrono baseado em evento
O padrão assíncrono baseado em eventos proporciona uma maneira eficiente de expor o comportamento assíncrono nas classes, com evento familiar e semântica de representante. Para implementá-lo, você deve seguir alguns requisitos de comportamento específicos. As seções a seguir descrevem os requisitos e as diretrizes a serem considerados ao implementar uma classe que segue o padrão assíncrono baseado em eventos.  
  
 Para obter uma visão geral, consulte [Implementando o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Garantias comportamentais necessárias  
 Se implementar o padrão assíncrono baseado em eventos, você deve fornecer diversas garantias para assegurar que a classe se comportará corretamente e que os clientes da classe podem confiar nesse comportamento.  
  
### <a name="completion"></a>Conclusão  
 Sempre chamar o *MethodName* `Completed` manipulador de eventos quando você tiver um cancelamento, um erro ou conclusão com êxito. Os aplicativos nunca devem permanecer inativos sem que a conclusão ocorra. Uma exceção a essa regra é se a própria operação assíncrona for projetada para nunca concluir.  
  
### <a name="completed-event-and-eventargs"></a>Evento e argumentos de eventos concluídos  
 Para cada separado *MethodName* `Async` método, aplique os seguintes requisitos de design:  
  
-   Definir um *MethodName* `Completed` eventos na mesma classe como o método.  
  
-   Definir um <xref:System.EventArgs> classe e o representante fornecido para o *MethodName* `Completed` eventos que deriva de <xref:System.ComponentModel.AsyncCompletedEventArgs> classe. O nome da classe padrão deve estar no formato *MethodName*`CompletedEventArgs`.  
  
-   Certifique-se de que o <xref:System.EventArgs> classe é específica para os valores de retorno de *MethodName* método. Ao usar a classe <xref:System.EventArgs>, você nunca deve solicitar que os desenvolvedores convertam o resultado.  
  
     O exemplo de código a seguir mostra as implementações correta e incorreta desse requisito, respectivamente.  
  
```csharp  
// Good design  
private void Form1_MethodNameCompleted(object sender, xxxCompletedEventArgs e)   
{   
    DemoType result = e.Result;  
}  
  
// Bad design  
private void Form1_MethodNameCompleted(object sender, MethodNameCompletedEventArgs e)   
{   
    DemoType result = (DemoType)(e.Result);  
}  
```  
  
-   Não defina uma classe <xref:System.EventArgs> para os métodos de retorno que retornam `void`. Em vez disso, use uma instância da classe <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
-   Certifique-se de que você sempre gerar o *MethodName* `Completed` eventos. Esse evento deve ser usado quando a conclusão for realizada com êxito, em caso de erro ou em caso de cancelamento. Os aplicativos nunca devem permanecer inativos sem que a conclusão ocorra.  
  
-   Você deve capturar todas as exceções que ocorrerem na operação assíncrona e atribuir a exceção de captura à propriedade <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>.  
  
-   Caso ocorra um erro ao concluir a tarefa, os resultados não devem estar acessíveis. Quando a propriedade <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> não for `null`, verifique se o acesso a qualquer propriedade na estrutura <xref:System.EventArgs> gera uma exceção. Use o método <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> para fazer essa verificação.  
  
-   Defina o tempo limite como um erro. Quando ocorre um tempo limite, gerar o *MethodName* `Completed` eventos e atribuir um <xref:System.TimeoutException> para o <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> propriedade.  
  
-   Se sua classe oferece suporte a várias chamadas simultâneas, certifique-se de que o *MethodName* `Completed` evento contém apropriada `userSuppliedState` objeto.  
  
-   Certifique-se de que o *MethodName* `Completed` é gerado no segmento apropriado e no momento apropriado do ciclo de vida do aplicativo. Para obter mais informações, consulte a seção Threads e contextos.  
  
### <a name="simultaneously-executing-operations"></a>Operações em execução simultânea  
  
-   Se sua classe oferece suporte a várias chamadas simultâneas, permitem ao desenvolvedor acompanhar cada invocação separadamente, definindo o *MethodName* `Async` sobrecarga que utiliza um parâmetro com valor de objeto de estado ou a ID da tarefa, chamado `userSuppliedState`. Esse parâmetro deve ser sempre o último parâmetro no *MethodName* `Async` assinatura do método.  
  
-   Se sua classe define o *MethodName* `Async` sobrecarga que utiliza um parâmetro com valor de objeto de estado ou a ID da tarefa, certifique-se rastrear o tempo de vida da operação com esse ID de tarefa e certifique-se de fornecê-lo de volta para a conclusão manipulador. Há algumas classes auxiliares disponíveis para ajudar. Para obter mais informações sobre o gerenciamento de simultaneidade, consulte [passo a passo: Implementando um componente compatível com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
-   Se sua classe define o *MethodName* `Async` método sem o parâmetro de estado e não oferece suporte a várias chamadas simultâneas, certifique-se de que qualquer tentativa de invocar *MethodName* `Async` antes anterior *MethodName* `Async` invocação concluiu gera um <xref:System.InvalidOperationException>.  
  
-   Em geral, não gerar uma exceção se o *MethodName* `Async` método sem o `userSuppliedState` parâmetro é chamado várias vezes para que haja várias operações pendentes. Você pode gerar uma exceção quando a classe não puder explicitamente lidar com essa situação, e você deduzir que os desenvolvedores podem lidar com esses diversos retornos de chamada indistinguíveis.  
  
### <a name="accessing-results"></a>Acessando os resultados  
  
-   Caso ocorra um erro durante a execução da operação assíncrona, os resultados não devem estar acessíveis. Verifique se o acesso a qualquer propriedade no <xref:System.ComponentModel.AsyncCompletedEventArgs> quando <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> não for `null`, gera a exceção usada como referência por <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. A classe <xref:System.ComponentModel.AsyncCompletedEventArgs> fornece o método <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> para esse propósito.  
  
-   Verifique se todas as tentativas de acessar o resultado geram um <xref:System.InvalidOperationException>, indicando que a operação foi cancelada. Use o método <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> para fazer essa verificação.  
  
### <a name="progress-reporting"></a>Relatórios de progresso  
  
-   Permita o uso de relatórios de progresso, se possível. Isso permite que os desenvolvedores melhorem a experiência dos usuários do aplicativo quando eles usam sua classe.  
  
-   Se você implementar um `ProgressChanged` / *MethodName* `ProgressChanged` eventos, certifique-se de que não há nenhum tais eventos gerados por uma determinada operação assíncrona após essa operação *MethodName* `Completed` evento foi gerado.  
  
-   Se o <xref:System.ComponentModel.ProgressChangedEventArgs> padrão estiver sendo preenchido, verifique se <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> sempre pode ser identificado como uma porcentagem. A porcentagem não precisa ser precisa, mas deve representar uma porcentagem. Se a métrica do relatório de progresso não tiver que ser uma porcentagem, derive uma classe da classe <xref:System.ComponentModel.ProgressChangedEventArgs> e deixe <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> como 0. Evite usar outras métricas além de porcentagem nos relatórios.  
  
-   Verifique se o evento `ProgressChanged` é gerado no thread certo e no momento certo do ciclo de vida do aplicativo. Para obter mais informações, consulte a seção Threads e contextos.  
  
### <a name="isbusy-implementation"></a>Implementação IsBusy  
  
-   Não exponha a propriedade `IsBusy` se a classe for compatível com diversas invocações simultâneas. Por exemplo, os proxies de serviço Web XML não expõem a propriedade `IsBusy` porque permitem usar diversas invocações simultâneas de métodos assíncronos.  
  
-   O `IsBusy` deve retornar a propriedade `true` depois que o *MethodName* `Async` método foi chamado e antes do *MethodName* `Completed` evento foi gerado. Caso contrário, ela deve retornar `false`. Os componentes <xref:System.ComponentModel.BackgroundWorker> e <xref:System.Net.WebClient> são exemplos de classes que expõem uma propriedade `IsBusy`.  
  
### <a name="cancellation"></a>Cancelamento  
  
-   Permita o cancelamento, se possível. Isso permite que os desenvolvedores melhorem a experiência dos usuários do aplicativo quando eles usam sua classe.  
  
-   Em caso de cancelamento, defina o sinalizador <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> no objeto <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
-   Verifique se todas as tentativas de acessar o resultado geram um <xref:System.InvalidOperationException>, indicando que a operação foi cancelada. Use o método <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> para fazer essa verificação.  
  
-   Verifique se as chamadas de um método de cancelamento sempre retornam com êxito e nunca geram uma exceção. Em geral, o cliente não é notificado se a operação pode mesmo ser cancelada a qualquer momento, nem se o cancelamento emitido foi realizado. No entanto, o aplicativo sempre recebe uma notificação quando o cancelamento é realizado. Isso acontece porque o aplicativo participa do status de conclusão.  
  
-   Gerar o *MethodName* `Completed` evento quando a operação foi cancelada.  
  
### <a name="errors-and-exceptions"></a>Erros e exceções  
  
-   Capture todas as exceções que ocorrerem na operação assíncrona e defina o valor da propriedade <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> para essa exceção.  
  
### <a name="threading-and-contexts"></a>Threads e contextos  
 Para que sua classe opere corretamente, é essencial que os indicadores de eventos do cliente sejam invocados no thread ou contexto certo de acordo com o modelo do aplicativo, incluindo [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] e aplicativos Windows Forms. Duas importantes classes auxiliares são fornecidas para garantir que a classe assíncrona se comporte corretamente em qualquer modelo de aplicativo: <xref:System.ComponentModel.AsyncOperation> e <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> fornece um método, <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, que retorna um <xref:System.ComponentModel.AsyncOperation>. O *MethodName* `Async` chamadas de método <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> e sua classe usa retornado <xref:System.ComponentModel.AsyncOperation> para rastrear o tempo de vida da tarefa assíncrona.  
  
 Para criar relatórios de progresso, resultados incrementais e conclusão para o cliente, chame os métodos <xref:System.ComponentModel.AsyncOperation.Post%2A> e <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> no <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> é responsável por fazer marshaling de chamadas para os identificadores de eventos de cliente para o thread ou contexto adequado.  
  
> [!NOTE]
>  Você pode driblar essas regras se quiser explicitamente ir contra a política de modelo de aplicativos, e ainda aproveitar outras vantagens do padrão assíncrono baseado em eventos. Por exemplo, uma classe pode operar no Windows Forms para ter threads livres. Você pode criar uma classe de thread livre, contanto que os desenvolvedores conheçam as restrições inerentes. Os aplicativos de console não sincronizam a execução das chamadas de <xref:System.ComponentModel.AsyncOperation.Post%2A>. Isso pode fazer com que os eventos `ProgressChanged` sejam gerados fora de ordem. Se quiser que as chamadas <xref:System.ComponentModel.AsyncOperation.Post%2A> sejam executadas em série, implemente e instale uma classe <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType>.  
  
 Para obter mais informações sobre como usar <xref:System.ComponentModel.AsyncOperation> e <xref:System.ComponentModel.AsyncOperationManager> para habilitar as operações assíncronas, consulte [passo a passo: Implementando um componente compatível com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Diretrizes  
  
-   De modo ideal, cada invocação de método deve ser independente das demais. Você deve evitar o agrupamento de invocações e recursos compartilhados. Se for necessário compartilhar os recursos entre as invocações, será necessário fornecer um mecanismo de sincronização adequado na sua implementação.  
  
-   Não recomendamos o uso de designs que requerem que o cliente implemente a sincronização. Por exemplo, você pode ter um método assíncrono que recebe um objeto estático global como parâmetro, e diversas invocações simultâneas desse método podem resultar em dados corrompidos ou deadlocks.  
  
-   Se você implementar um método com sobrecarga de diversas invocações (`userState` na assinatura), sua classe precisará gerenciar uma coleção de estados dos usuários ou IDs de tarefas e suas respectivas operações pendentes. Essa coleção deve ser protegida com as regiões `lock` porque as diversas invocações adicionam e removem `userState` objetos da coleção.  
  
-   Considere reutilizar as classes `CompletedEventArgs` quando possível e adequado. Nesse caso, a nomenclatura não é consistente com o nome do método porque um determinado representante e o tipo <xref:System.EventArgs> não são vinculados a um único método. No entanto, forçar os desenvolvedores a converter o valor recuperado de uma propriedade no <xref:System.EventArgs> nunca é aceitável.  
  
-   Se você estiver criando uma classe que deriva de <xref:System.ComponentModel.Component>, não implemente nem instale sua própria classe <xref:System.Threading.SynchronizationContext>. Os modelos do aplicativo, e não os componentes, controlam o <xref:System.Threading.SynchronizationContext> usado.  
  
-   Ao usar multithreading de qualquer tipo, você pode enfrentar bugs muito sérios e complexos. Antes de implementar qualquer solução que usa multithreading, consulte [gerenciados Threading práticas recomendadas](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Implementando o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Programação multi-threaded com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Decidindo quando implementar o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Como usar componentes compatíveis com o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Instruções passo a passo: implementando um componente compatível com o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
