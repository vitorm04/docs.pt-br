---
title: "Instruções passo a passo: implementando um componente compatível com o padrão assíncrono baseado em evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150e4b27cc149774895574ddd196de5f9bc2acd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Instruções passo a passo: implementando um componente compatível com o padrão assíncrono baseado em evento
Se você estiver escrevendo uma classe com algumas operações que podem causar atrasos notáveis, considere fornecendo funcionalidade assíncrona Implementando o [baseado em evento visão geral do padrão assíncrono](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Este passo a passo ilustra como criar um componente que implementa o padrão assíncrono baseado em evento. Ele é implementado usando classes auxiliares do <xref:System.ComponentModel?displayProperty=nameWithType> namespace, o que garante que o componente funciona corretamente em qualquer modelo de aplicativo, incluindo [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplicativos de Windows Forms e aplicativos de Console. Este componente também é projetáveis com um <xref:System.Windows.Forms.PropertyGrid> controle e seus próprios designers personalizados.  
  
 Quando terminar, você terá um aplicativo que calcula números primos de forma assíncrona. Seu aplicativo terá um thread de interface do usuário do usuário principal e um thread para cada cálculo de números primos. Embora testar se é um grande número primo pode levar uma quantidade considerável de tempo, o thread de interface do usuário principal não será interrompido por esse atraso e o formulário será responsivo durante os cálculos. Você poderá executar como muitos cálculos como desejar simultaneamente e seletivamente Cancelar pendentes cálculos.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar o componente  
  
-   Definindo representantes e eventos assíncronos públicos  
  
-   Definindo privada delegados  
  
-   Implementando eventos públicos  
  
-   Implementando o método de conclusão  
  
-   Implementando os métodos de trabalho  
  
-   Implementação de início e cancelamento  
  
 Para copiar o código neste tópico como uma única lista, consulte [como: implementar um componente compatível com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Criar o componente  
 A primeira etapa é criar o componente que implementa o padrão assíncrono baseado em evento.  
  
#### <a name="to-create-the-component"></a>Para criar o componente  
  
-   Criar uma classe chamada `PrimeNumberCalculator` que herda de <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definindo representantes e eventos assíncronos públicos  
 O componente se comunica com clientes usando os eventos. O *MethodName* `Completed` clientes para a conclusão de uma tarefa assíncrona, alertas de eventos e o *MethodName* `ProgressChanged` evento informa os clientes do progresso de uma tarefa assíncrona.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Para definir eventos assíncronos para clientes do seu componente:  
  
1.  Importar o <xref:System.Threading?displayProperty=nameWithType> e <xref:System.Collections.Specialized?displayProperty=nameWithType> namespaces na parte superior do arquivo.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Antes do `PrimeNumberCalculator` definição, da classe declarar representantes para eventos de andamento e a conclusão.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  No `PrimeNumberCalculator` definição da classe, declare eventos para relatar o andamento e a conclusão aos clientes.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Após o `PrimeNumberCalculator` definição da classe, derivar o `CalculatePrimeCompletedEventArgs` classe para reportar o resultado de cada cálculo ao manipulador de eventos do cliente para o `CalculatePrimeCompleted`.event. Além de `AsyncCompletedEventArgs` propriedades, essa classe permite que o cliente determinar qual número foi testado, se ela é a principal e o divisor primeiro novidades se não for principal.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Neste ponto, você pode criar o componente.  
  
#### <a name="to-test-your-component"></a>Para testar seu componente  
  
-   Compile o componente.  
  
     Você receberá dois avisos do compilador:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Esses avisos serão removidos na próxima seção.  
  
## <a name="defining-private-delegates"></a>Definindo privada delegados  
 Os aspectos assíncronos do `PrimeNumberCalculator` componente são implementados internamente com um delegado especial conhecido como um <xref:System.Threading.SendOrPostCallback>. Um <xref:System.Threading.SendOrPostCallback> representa um método de retorno de chamada que é executado em um <xref:System.Threading.ThreadPool> thread. O método de retorno de chamada deve ter uma assinatura que usa um único parâmetro do tipo <xref:System.Object>, que significa que você precisará passar o estado entre delegates em uma classe wrapper. Para obter mais informações, consulte <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Para implementar o comportamento de assíncrono interno do componente:  
  
1.  Declare e crie o <xref:System.Threading.SendOrPostCallback> delega no `PrimeNumberCalculator` classe. Criar o <xref:System.Threading.SendOrPostCallback> objetos em um método de utilitário chamado `InitializeDelegates`.  
  
     Você precisará de dois delegados: uma para relatar o andamento para o cliente e outra para relatório de conclusão para o cliente.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Chamar o `InitializeDelegates` método no construtor do componente.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Declara um representante no `PrimeNumberCalculator` classe que manipula o trabalho real para ser executado de forma assíncrona. Este delegado encapsula o método de trabalho que verifica se um número é o principal. O representante aceitar um <xref:System.ComponentModel.AsyncOperation> parâmetro, que será usado para rastrear o tempo de vida da operação assíncrona.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Crie uma coleção para gerenciar o tempo de vida de operações assíncronas pendentes. O cliente precisa de uma maneira para rastrear as operações como elas são executadas e concluídas, e esse controle é feito ao exigir que o cliente passar um token exclusivo ou a ID da tarefa, quando o cliente faz a chamada para o método assíncrono. O `PrimeNumberCalculator` componente deve manter o controle de cada chamada ao associar a ID da tarefa de sua invocação correspondente. Se o cliente passa uma ID de tarefa que não é exclusiva, o `PrimeNumberCalculator` componente deve gerar uma exceção.  
  
     O `PrimeNumberCalculator` componente mantém o controle de ID da tarefa usando uma classe de coleção especial chamada um <xref:System.Collections.Specialized.HybridDictionary>. Na definição de classe, crie um <xref:System.Collections.Specialized.HybridDictionary> chamado `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementando eventos públicos  
 Componentes que implementam o padrão assíncrono baseado em evento se comunicar com clientes usando os eventos. Esses eventos são chamados no thread adequada com a Ajuda do <xref:System.ComponentModel.AsyncOperation> classe.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Para gerar eventos para clientes do componente:  
  
1.  Implemente eventos públicos para emissão de relatórios para os clientes. Você precisará de um evento para relatório de andamento e outro para relatório de conclusão.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementando o método de conclusão  
 O delegado de conclusão é o método que o comportamento assíncrono subjacente, free-thread chamará quando termina a operação assíncrona foi bem-sucedida, erro ou cancelamento. Esta chamada ocorre em um thread arbitrário.  
  
 Esse método é onde a ID da tarefa do cliente é removido da coleção interna de tokens de cliente exclusivo. Esse método também termina o tempo de vida de uma determinada operação assíncrona ao chamar o <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> método correspondente <xref:System.ComponentModel.AsyncOperation>. Essa chamada gera o evento de conclusão no thread que é apropriado para o modelo de aplicativo. Após o <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> método é chamado, esta instância do <xref:System.ComponentModel.AsyncOperation> não pode mais ser usado, e quaisquer tentativas subsequentes de usá-lo lançará uma exceção.  
  
 O `CompletionMethod` assinatura deve conter todos os estados necessárias para descrever o resultado da operação assíncrona. Ele mantém o estado para o número que foi testado por essa operação assíncrona específica, seja o número primo e o valor de seu primeiro divisor se não for um número primo. Ela também contém o estado que descreve qualquer exceção que ocorreu, e o <xref:System.ComponentModel.AsyncOperation> correspondente a essa tarefa específica.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>Para concluir uma operação assíncrona:  
  
-   Implemente o método de conclusão. Ele usa seis parâmetros, que são usados para preencher um `CalculatePrimeCompletedEventArgs` que é retornado ao cliente por meio do cliente `CalculatePrimeCompletedEventHandler`. Ele remove o token de ID de tarefa do cliente da coleção interna e ele termina o tempo de vida da operação assíncrona com uma chamada para <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. O <xref:System.ComponentModel.AsyncOperation> controla a chamada para o contexto apropriado para o modelo de aplicativo ou thread.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Neste ponto, você pode criar o componente.  
  
#### <a name="to-test-your-component"></a>Para testar seu componente  
  
-   Compile o componente.  
  
     Você receberá um aviso do compilador:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Esse aviso será resolvido na próxima seção.  
  
## <a name="implementing-the-worker-methods"></a>Implementando os métodos de trabalho  
 Até agora, você implementou o código de suporte assíncrono para o `PrimeNumberCalculator` componente. Agora você pode implementar o código que faz o trabalho real. Você irá implementar os três métodos: `CalculateWorker`, `BuildPrimeNumberList`, e `IsPrime`. Juntas, `BuildPrimeNumberList` e `IsPrime` compõem um algoritmo bem conhecido chamado Sieve de Eratosthenes, que determina se um número primo localizando todos os números primos até a raiz quadrada do número de teste. Se nenhum divisores forem encontrados por esse ponto, o número de teste é primos.  
  
 Este componente foram desenvolvido para máxima eficiência, ele seria Lembre-se de todos os números primos descobertos por várias invocações de números de teste diferente. Ele também deve verificar para divisores triviais como 2, 3 e 5. A intenção deste exemplo é demonstrar como demoradas operações podem ser executadas de forma assíncrona, no entanto, para que essas otimizações são deixadas como um exercício para você.  
  
 O `CalculateWorker` método é encapsulado em um representante e é invocado de forma assíncrona, com uma chamada para `BeginInvoke`.  
  
> [!NOTE]
>  Relatório de progresso é implementado no `BuildPrimeNumberList` método. Em computadores rápidos, `ProgressChanged` eventos podem ser gerados em sucessão rápida. O thread de cliente, em que esses eventos são gerados, deve ser capaz de lidar com essa situação. Código de interface do usuário pode ser inundada com mensagens e não é possível continuar, resultando no comportamento de deslocamento. Para uma interface de usuário de exemplo que manipula essa situação, consulte [como: implementar um cliente do padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Para executar o cálculo de número primo de forma assíncrona:  
  
1.  Implementar o `TaskCanceled` método utilitário. Isso verifica se a coleção de tempo de vida de tarefa para a ID de tarefa específica e retorna `true` se a ID da tarefa não foi encontrada.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Implementar o método de `CalculateWorker` . Ele usa dois parâmetros: um número para testar e um <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Implementar `BuildPrimeNumberList`. Ele usa dois parâmetros: o número para testar e um <xref:System.ComponentModel.AsyncOperation>. Ele usa o <xref:System.ComponentModel.AsyncOperation> para relatar o andamento e o resultado incremental. Isso garante que os manipuladores de eventos do cliente são chamados no thread adequada ou contexto para o modelo de aplicativo. Quando `BuildPrimeNumberList` localiza um número primo, relatar isso como um resultado incremental para manipulador de eventos do cliente para o `ProgressChanged` evento. Isso requer uma classe derivada de <xref:System.ComponentModel.ProgressChangedEventArgs>, chamado `CalculatePrimeProgressChangedEventArgs`, que tenha um adicionado propriedade chamada `LatestPrimeNumber`.  
  
     O `BuildPrimeNumberList` método também chama o `TaskCanceled` método e saídas se o método retornar `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Implementar `IsPrime`. Ele usa três parâmetros: uma lista de números primos de conhecidos, o número para testar e um parâmetro de saída para o divisor primeiro encontrado. Recebe a lista de números primos, determina se o teste de número primo.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Derivar `CalculatePrimeProgressChangedEventArgs` de <xref:System.ComponentModel.ProgressChangedEventArgs>. Essa classe é necessária para relatar resultados incrementais ao manipulador de eventos do cliente para o `ProgressChanged` evento. Ele tem uma propriedade adicional chamada `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Neste ponto, você pode criar o componente.  
  
#### <a name="to-test-your-component"></a>Para testar seu componente  
  
-   Compile o componente.  
  
     Tudo o que permanece a serem gravados é os métodos para iniciar e cancelar operações assíncronas, `CalculatePrimeAsync` e `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementando o início e métodos de cancelamento  
 Iniciar o método de trabalho em seu próprio thread chamando `BeginInvoke` sobre o delegado que encapsula a ele. Para gerenciar o tempo de vida de uma determinada operação assíncrona, você deve chamar o <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> método sobre o <xref:System.ComponentModel.AsyncOperationManager> classe auxiliar. Isso retorna um <xref:System.ComponentModel.AsyncOperation>, que realiza marshaling de chamadas em manipuladores de eventos do cliente para o contexto ou adequada da thread.  
  
 Cancelar uma determinada operação pendente chamando <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> em correspondente <xref:System.ComponentModel.AsyncOperation>. Isso encerra a operação e qualquer chamada subsequente para seus <xref:System.ComponentModel.AsyncOperation> lançará uma exceção.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>Para implementar o início e cancelar a funcionalidade:  
  
1.  Implementar o método de `CalculatePrimeAsync` . Verifique se que o token fornecido pelo cliente (ID da tarefa) é exclusivo em relação a todos os tokens que representam atualmente tarefas pendentes. Se o cliente passa um token não exclusivo, `CalculatePrimeAsync` gera uma exceção. Caso contrário, o token é adicionado à coleção de ID de tarefa.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Implementar o método de `CancelAsync` . Se o `taskId` parâmetro existe na coleção de token, ele será removido. Isso impede que tarefas canceladas que não foram iniciados de execução. Se a tarefa estiver em execução, o `BuildPrimeNumberList` método encerrado quando ele detecta que a ID da tarefa foi removida da coleção de tempo de vida.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Neste ponto, você pode criar o componente.  
  
#### <a name="to-test-your-component"></a>Para testar seu componente  
  
-   Compile o componente.  
  
 O `PrimeNumberCalculator` componente agora está concluído e pronto para uso.  
  
 Para um cliente de exemplo que usa o `PrimeNumberCalculator` componente, consulte [como: implementar um cliente do padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode preencher este exemplo escrevendo `CalculatePrime`, o equivalente síncrono `CalculatePrimeAsync` método. Isso tornará o `PrimeNumberCalculator` totalmente compatível com o padrão assíncrono baseado em evento do componente.  
  
 Você pode melhorar neste exemplo, mantendo a lista de todos os números primos descoberto por várias invocações de números de teste diferente. Usando essa abordagem, cada tarefa se beneficiam o trabalho realizado por tarefas anteriores. Tenha cuidado para proteger essa lista com `lock` regiões, portanto o acesso à lista por threads diferentes é serializado.  
  
 Você também pode melhorar este exemplo testando divisores triviais, como 2, 3 e 5.  
  
## <a name="see-also"></a>Consulte também  
 [Como executar uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NÃO está em compilação: Multithread no Visual Basic](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Como implementar um componente compatível com o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Programação multi-threaded com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
