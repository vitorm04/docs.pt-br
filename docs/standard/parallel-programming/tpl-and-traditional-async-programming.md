---
title: "TPL e programação assíncrona do .NET Framework"
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
helpviewer_keywords: tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f29ca819fa7a59edeb105720d74a25512e95bdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL e programação assíncrona do .NET Framework
O .NET Framework fornece dois seguintes padrões para executar operações assíncronas vinculada à e/S e vinculada à computação:  
  
-   Modelo APM (Asynchronous Programming), no qual as operações assíncronas são representadas por um par de métodos Begin/End como <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> e <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
-   Evento padrão assíncrono baseado (EAP), na qual as operações assíncronas é representada por um par de método/evento que é nomeado *OperationName*Async e *OperationName*concluída, por exemplo, <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> e <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (O EAP foi introduzido no .NET Framework versão 2.0.)  
  
 O biblioteca paralela de tarefas (TPL) pode ser usado de várias maneiras, junto com qualquer um dos padrões assíncronos. Você pode expor operações APM e EAP como tarefas para os consumidores de biblioteca, ou você pode expor os padrões APM mas use objetos de tarefa para implementá-los internamente. Em ambos os cenários, por meio de objetos de tarefa, você pode simplificar o código e aproveitar as seguintes funcionalidades úteis:  
  
-   Registre retornos de chamada, na forma de continuação de tarefas, a qualquer momento depois que a tarefa foi iniciada.  
  
-   Coordenar várias operações executam em resposta a um `Begin_` método usando o <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> e <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> métodos, ou o <xref:System.Threading.Tasks.Task.WaitAll%2A> método ou o <xref:System.Threading.Tasks.Task.WaitAny%2A> método.  
  
-   Encapsule as operações assíncronas vinculada à e/S e vinculada à computação no mesmo objeto de tarefa.  
  
-   Monitore o status do objeto de tarefa.  
  
-   Empacotar o status de uma operação para um objeto de tarefa usando <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>Encapsulando Operações APM em uma Tarefa  
 Tanto o <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> e <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> classes fornecem várias sobrecargas do <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> métodos que permitem que você encapsulam um par de métodos Begin/End APM em um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> instância. Várias sobrecargas acomodam qualquer par de métodos Begin/End que têm de zero a três parâmetros de entrada.  
  
 Para os pares que têm `End` métodos que retornam um valor (`Function` no Visual Basic), use os métodos em <xref:System.Threading.Tasks.TaskFactory%601> que criar um <xref:System.Threading.Tasks.Task%601>. Para `End` métodos que retornam void (`Sub` no Visual Basic), use os métodos em <xref:System.Threading.Tasks.TaskFactory> que criar um <xref:System.Threading.Tasks.Task>.  
  
 Para esses poucos casos em que o `Begin` tem mais de três parâmetros de método ou contém `ref` ou `out` parâmetros adicionais `FromAsync` sobrecargas que encapsulam apenas o `End` método são fornecidos.  
  
 O exemplo a seguir mostra a assinatura para o `FromAsync` sobrecarga que corresponde a <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> e <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> métodos. Essa sobrecarga tem três parâmetros de entrada, da seguinte maneira.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 O primeiro parâmetro é um <xref:System.Func%606> que corresponde à assinatura do delegado a <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> método. O segundo parâmetro é um <xref:System.Func%602> delegado que utiliza um <xref:System.IAsyncResult> e retorna um `TResult`. Porque <xref:System.IO.FileStream.EndRead%2A> retorna um inteiro, o compilador infere o tipo de `TResult` como <xref:System.Int32> e o tipo de tarefa como <xref:System.Threading.Tasks.Task>. Os últimos quatro parâmetros são idênticos na <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> método:  
  
-   O buffer no qual armazenar os dados de arquivo.  
  
-   O deslocamento do buffer no qual começar a gravar dados.  
  
-   A quantidade máxima de dados para ler o arquivo.  
  
-   Um objeto opcional que armazena dados de estado definido pelo usuário para passar para o retorno de chamada.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Usando ContinueWith para a Funcionalidade do Retorno de Chamada  
 Se você precisar de acesso aos dados no arquivo, em vez de apenas o número de bytes, o <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> método não é suficiente. Em vez disso, use <xref:System.Threading.Tasks.Task>, cujo `Result` propriedade contém os dados de arquivo. Você pode fazer isso adicionando uma continuação para a tarefa original. A continuação realiza o trabalho que normalmente seria executado pelo <xref:System.AsyncCallback> delegate. Ele é invocado quando o antecessor for concluída e o buffer de dados tenha sido preenchido. (O <xref:System.IO.FileStream> objeto deve ser fechado antes de retornar.)  
  
 O exemplo a seguir mostra como retornar um <xref:System.Threading.Tasks.Task> que encapsula o par de BeginRead/EndRead do <xref:System.IO.FileStream> classe.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 O método pode ser chamado, da seguinte maneira.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Fornecendo Dados de Estado Personalizados  
 Típicas <xref:System.IAsyncResult> operações, se seu <xref:System.AsyncCallback> delegado requer alguns dados de estado personalizado, você precisa passar no último parâmetro no `Begin` método, para que os dados podem ser empacotados no <xref:System.IAsyncResult> objeto eventualmente passado para o método de retorno de chamada. Isso normalmente não é necessário quando o `FromAsync` métodos são usados. Se os dados personalizados são conhecidos para a continuação, ela poderá ser capturada diretamente no delegado de continuação. O exemplo a seguir é semelhante ao exemplo anterior, mas em vez de examinar o `Result` propriedade o antecessor a continuação examina os dados de estado personalizado que é diretamente acessíveis para o representante de usuário da continuação.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Sincronizando Várias Tarefas FromAsync  
 Estático <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> e <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> métodos fornecem flexibilidade adicional quando usado em conjunto com o `FromAsync` métodos. O exemplo a seguir mostra como iniciar várias operações de e/s assíncronas e aguarde até que todas elas sejam concluídas antes de executar a continuação.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Tarefas FromAsync Apenas Para o Método Final  
 Para esses poucos casos em que o `Begin` método requer mais de três parâmetros de entrada ou tem `ref` ou `out` parâmetros, você pode usar o `FromAsync` sobrecargas, por exemplo, <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, que representam apenas o `End`método. Esses métodos também podem ser usados em qualquer cenário em que recebem um <xref:System.IAsyncResult> e deseja encapsulá-lo em uma tarefa.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>Iniciando e Cancelando Tarefas FromAsync  
 A tarefa retornada por um `FromAsync` método tem um status de WaitingForActivation e será iniciado pelo sistema em algum momento depois que a tarefa é criada. Se você tentar chamar início em uma tarefa, será gerada uma exceção.  
  
 Você não pode cancelar uma `FromAsync` de tarefas, como as APIs do .NET Framework subjacente no momento não oferece suporte ao cancelamento em andamento do arquivo ou e/s de rede. Você pode adicionar a funcionalidade de cancelamento para um método que encapsula uma `FromAsync` chamada, mas você só pode responder ao cancelamento antes `FromAsync` é chamado ou depois dele concluída (por exemplo, em uma tarefa de continuação).  
  
 Algumas classes que oferecem suporte a EAP, por exemplo, <xref:System.Net.WebClient>, suporte ao cancelamento, e você pode integrar essa funcionalidade de cancelamento nativo usando tokens de cancelamento.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Expondo Operações EAP Complexas Como Tarefas  
 A TPL fornece os métodos que são projetados especificamente para encapsular uma operação assíncrona com base em eventos da mesma forma que o `FromAsync` família de métodos wrap o <xref:System.IAsyncResult> padrão. No entanto, a TPL fornecem o <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> classe, que pode ser usado para representar qualquer conjunto arbitrário de operações como um <xref:System.Threading.Tasks.Task%601>. As operações podem ser síncronas ou assíncronas e podem ser vinculados de e/s ou vinculada à computação ou ambos.  
  
 O exemplo a seguir mostra como usar um <xref:System.Threading.Tasks.TaskCompletionSource%601> para expor um conjunto de assíncrona <xref:System.Net.WebClient> operações ao código do cliente como básico <xref:System.Threading.Tasks.Task%601>. O método permite que você insira uma matriz de URLs da Web e um termo ou nome para pesquisar e, em seguida, retorna o número de vezes que o termo de pesquisa ocorre em cada site.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Para obter um exemplo mais completo, que inclui a manipulação de exceção adicionais e mostra como chamar o método no código do cliente, consulte [como: encapsular padrões de EAP em uma tarefa](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Lembre-se de que qualquer tarefa que é criada por um <xref:System.Threading.Tasks.TaskCompletionSource%601> será iniciada por esse TaskCompletionSource e, portanto, o código do usuário não deve chamar o método Start nessa tarefa.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Implementando o Padrão APM Usando Tarefas  
 Em alguns cenários, pode ser desejável para expor diretamente o <xref:System.IAsyncResult> padrão usando pares de métodos Begin/End em uma API. Por exemplo, talvez você queira manter a consistência com APIs existentes, ou você pode ter automatizada ferramentas que exigem esse padrão. Nesses casos, você pode usar tarefas para simplificar como o padrão do APM é implementado internamente.  
  
 O exemplo a seguir mostra como usar tarefas para implementar um par de métodos Begin/End do APM para um método de vinculada à computação de longa execução.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>Usando o Código de Exemplo StreamExtensions  
 O Streamextensions.cs de arquivo, em [exemplos de programação paralela com o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=165717) no site do MSDN, contém várias implementações de referência que usam objetos de tarefa de arquivo assíncrono e e/s de rede.  
  
## <a name="see-also"></a>Consulte também  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
