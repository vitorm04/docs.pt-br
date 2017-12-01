---
title: "Implementando o padrão assíncrono baseado em evento"
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
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b4df5e4df914d932c7413e9330e8663753456c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementando o padrão assíncrono baseado em evento
Se você estiver escrevendo uma classe com algumas operações que podem causar atrasos notáveis, considere fornecendo funcionalidade assíncrona implementando [baseado em evento visão geral do padrão assíncrono](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 O padrão assíncrono baseado em evento fornece uma maneira padronizada para empacotar uma classe que tem recursos assíncronos. Se implementado com classes auxiliares como <xref:System.ComponentModel.AsyncOperationManager>, sua classe funcionará corretamente em qualquer modelo de aplicativo, incluindo [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplicativos de Console e aplicativos do Windows Forms.  
  
 Para obter um exemplo que implementa o padrão assíncrono baseado em evento, consulte [como: implementar um componente compatível com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Para operações assíncronas simples, você pode obter o <xref:System.ComponentModel.BackgroundWorker> componente adequado. Para obter mais informações sobre <xref:System.ComponentModel.BackgroundWorker>, consulte [como: executar uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 A lista a seguir descreve os recursos do que o padrão assíncrono baseado em evento discutidos neste tópico.  
  
-   Oportunidades para implementar o padrão assíncrono baseado em evento  
  
-   Métodos assíncronos de nomenclatura  
  
-   Se desejar oferecer suporte ao cancelamento  
  
-   Opcionalmente, oferece suporte à propriedade IsBusy  
  
-   Se desejar fornecer suporte para relatórios de andamento  
  
-   Opcionalmente, fornecer suporte para retornar resultados Incremental  
  
-   Tratamento de Out e Ref parâmetros em métodos  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Oportunidades para implementar o padrão assíncrono baseado em evento  
 Considere implementar o padrão assíncrono baseado em evento quando:  
  
-   Os clientes da sua classe não é necessário <xref:System.Threading.WaitHandle> e <xref:System.IAsyncResult> objetos disponíveis para operações assíncronas, o que significa que a sondagem e <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> precisam ser criados pelo cliente.  
  
-   Você deseja que as operações assíncronas para serem gerenciados pelo cliente com o modelo de evento/delegado familiarizado.  
  
 Qualquer operação é um candidato para uma implementação assíncrona, mas aqueles que esperar a incidência de latências de tempo devem ser considerados. Especialmente apropriadas são operações em que os clientes chamar um método em notificados após a conclusão, sem necessidade de intervenção adicional. Também apropriadas são operações que são executados continuamente, notificando periodicamente os clientes de andamento, resultados incrementais ou alterações de estado.  
  
 Para obter mais informações sobre como decidir quando compatíveis com o padrão assíncrono baseado em evento, consulte [Decidindo quando implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Métodos assíncronos de nomenclatura  
 Para cada método síncrono *MethodName* para a qual você deseja fornecer uma cópia assíncrona:  
  
 Definir um *MethodName* `Async` método que:  
  
-   Retorna `void`.  
  
-   Usa os mesmos parâmetros como o *MethodName* método.  
  
-   Aceita várias invocações.  
  
 Opcionalmente, definir um *MethodName* `Async` sobrecarga, idêntica ao *MethodName*`Async`, mas com um parâmetro adicional com valor de objeto chamado `userState`. Faça isso se você está preparado para gerenciar várias chamadas simultâneas do seu método, caso em que o `userState` valor será entregue novamente para todos os manipuladores de eventos para distinguir invocações do método. Você também pode optar por fazer isso simplesmente como um local para armazenar o estado do usuário para recuperação posterior.  
  
 Para cada separado *MethodName* `Async` assinatura do método:  
  
1.  Defina o evento a seguir a mesma classe que o método:  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Definir o representante a seguir e <xref:System.ComponentModel.AsyncCompletedEventArgs>. Eles provavelmente serão definidos fora de classe em si, mas no mesmo namespace.  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   Certifique-se de que o *MethodName* `CompletedEventArgs` classe expõe seus membros como propriedades somente leitura e não os campos, como campos de impedir que a associação de dados.  
  
    -   Não definir qualquer <xref:System.ComponentModel.AsyncCompletedEventArgs>-derivadas de classes para métodos que não produzirá os resultados. Basta usar uma instância de <xref:System.ComponentModel.AsyncCompletedEventArgs> em si.  
  
        > [!NOTE]
        >  É perfeitamente aceitável, quando apropriado, a reutilização de representante e viável e <xref:System.ComponentModel.AsyncCompletedEventArgs> tipos. Nesse caso, o nome não será mais consistente com o nome do método, desde um determinado representante e <xref:System.ComponentModel.AsyncCompletedEventArgs> não seja vinculado a um único método.  
  
## <a name="optionally-support-cancellation"></a>Se desejar oferecer suporte ao cancelamento  
 Se sua classe oferecerão suporte a operações assíncronas de cancelamento, cancelamento deve ser exposto ao cliente, conforme descrito abaixo. Observe que há dois pontos de decisão que precisam ser alcançado antes de definir o suporte ao cancelamento de:  
  
-   Sua classe, incluindo futuros antecipados, tem apenas uma operação assíncrona que oferece suporte ao cancelamento?  
  
-   É possível operações assíncronas que oferecem suporte a várias operações pendentes suporte ao cancelamento? Ou seja, o *MethodName* `Async` método take um `userState` parâmetro, e permitir várias invocações antes de aguardar a conclusão?  
  
 Use as respostas a essas duas perguntas na tabela a seguir para determinar o que deve ser a assinatura para o método de cancelamento.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Várias operações simultâneas com suporte|Apenas uma operação de cada vez|  
|------|------------------------------------------------|----------------------------------|  
|Uma operação assíncrona na classe inteira|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Várias operações assíncronas em classe|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Várias operações simultâneas com suporte|Apenas uma operação de cada vez|  
|------|------------------------------------------------|----------------------------------|  
|Uma operação assíncrona na classe inteira|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Várias operações assíncronas em classe|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Se você definir o `CancelAsync(object userState)` método, os clientes devem ser cuidadoso ao escolher seus valores de estado para torná-los capaz de distinguir entre todos os métodos assíncronos chamados no objeto e não apenas entre todas as invocações de um único método assíncrono.  
  
 A decisão para a versão de única AsyncOperation *MethodName* `AsyncCancel` baseia-se em ser capaz de descobrir mais facilmente o método em um ambiente de design como IntelliSense do Visual Studio. Isso agrupa os membros relacionados e distingue-los de outros membros que têm relação com funcionalidade assíncrona. Se você espera que pode haver mais operações assíncronas adicionados em versões subsequentes, é melhor definir `CancelAsync`.  
  
 Não defina vários métodos da tabela acima na mesma classe. Que não faça sentido, ou ele será sobrecarregar a interface de classe com a proliferação de métodos.  
  
 Esses métodos normalmente retornará imediatamente, e a operação pode ou não pode realmente cancelar. No manipulador de eventos para o *MethodName* `Completed` evento, o *MethodName* `CompletedEventArgs` objeto contém um `Cancelled` campo, o que os clientes podem usar para determinar se a cancelamento tenha ocorrido.  
  
 Obedecer a semântica de cancelamento descrita em [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>Opcionalmente, oferece suporte à propriedade IsBusy  
 Se sua classe não oferece suporte a várias chamadas simultâneas, considere a possibilidade de expor um `IsBusy` propriedade. Isso permite que desenvolvedores determinar se um *MethodName* `Async` método está sendo executado sem capturando uma exceção do *MethodName* `Async` método.  
  
 Obedecer a `IsBusy` semântica descrito em [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>Se desejar fornecer suporte para relatórios de andamento  
 É recomendável com frequência para uma operação assíncrona para relatar o progresso durante sua operação. O padrão assíncrono baseado em evento fornece orientação para fazer isso.  
  
-   Opcionalmente, defina um evento a ser gerado pela operação assíncrona e invocado no thread apropriado. O <xref:System.ComponentModel.ProgressChangedEventArgs> objeto transporta um indicador de progresso com valor de inteiro deve estar entre 0 e 100.  
  
-   Nomeie esse evento da seguinte maneira:  
  
    -   `ProgressChanged`Se a classe tem várias operações assíncronas (ou deve crescer para incluir várias operações assíncronas em versões futuras);  
  
    -   *MethodName* `ProgressChanged` se a classe tiver uma única operação assíncrona.  
  
     Essa opção de nomenclatura comparável ao que feitas para o método de cancelamento, conforme descrito na seção, opcionalmente, o suporte ao cancelamento.  
  
 Esse evento deve usar o <xref:System.ComponentModel.ProgressChangedEventHandler> assinatura do delegado e o <xref:System.ComponentModel.ProgressChangedEventArgs> classe. Como alternativa, se um indicador de progresso mais específica de domínio pode ser fornecido (por instância, leitura de bytes e total de bytes para uma operação de download), em seguida, você deve definir uma classe derivada de <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Observe que há apenas um `ProgressChanged` ou *MethodName* `ProgressChanged` evento para a classe, independentemente do número de métodos assíncronos que ele suporta. Os clientes devem usar o `userState` objeto que é passado para o *MethodName* `Async` métodos para distinguir entre as atualizações de andamento em várias operações simultâneas.  
  
 Pode haver situações em que várias operações de suporte para progresso e cada retorna um indicador diferente para o andamento. Em um único caso, `ProgressChanged` evento não é apropriado, e você pode considerar o suporte a vários `ProgressChanged` eventos. Nesse caso, use um padrão de nomeação de *MethodName* `ProgressChanged` para cada *MethodName* `Async` método.  
  
 Obedecer a semântica de relatórios de progresso descrita [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>Opcionalmente, fornecer suporte para retornar resultados Incremental  
 Às vezes, uma operação assíncrona pode retornar resultados incrementais antes da conclusão. Há várias opções que podem ser usados para oferecer suporte a esse cenário. Seguem alguns exemplos.  
  
### <a name="single-operation-class"></a>Operação única classe  
 Se sua classe só dá suporte a uma única operação assíncrona, e essa operação é capaz de retornar resultados incrementais, em seguida:  
  
-   Estender o <xref:System.ComponentModel.ProgressChangedEventArgs> digite para carregar os dados de resultado incremental e definir um *MethodName* `ProgressChanged` eventos com essa dados estendidos.  
  
-   Gerar isso *MethodName* `ProgressChanged` eventos quando há um resultado incremental ao relatório.  
  
 Essa solução se aplica especificamente para uma classe AsyncOperation único porque não há nenhum problema com o mesmo evento ocorrendo retornar resultados incrementais em "todas as operações", como o *MethodName* `ProgressChanged` does do evento.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Classe de várias operações com resultados Incremental homogêneos  
 Nesse caso, sua classe oferece suporte a vários métodos assíncronos, cada capaz de retornar resultados incrementais, e esses resultados incrementais todos têm o mesmo tipo de dados.  
  
 Siga o modelo descrito acima para classes de operação única, como o mesmo <xref:System.EventArgs> estrutura funciona para todos os resultados incrementais. Definir um `ProgressChanged` eventos em vez de um *MethodName* `ProgressChanged` evento, desde que ela se aplica a vários métodos assíncronos.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Classe de várias operações com resultados Incremental heterogêneos  
 Se sua classe oferece suporte a vários métodos assíncronos, cada retornando um tipo diferente de dados, você deve:  
  
-   Separe o resultado incremental relatórios a partir de seu relatório de progresso.  
  
-   Definir um separado *MethodName* `ProgressChanged` evento com apropriado <xref:System.EventArgs> para cada método assíncrono manipular dados de resultado incremental desse método.  
  
 Invocar o manipulador de eventos no thread apropriada conforme descrito em [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Tratamento de Out e Ref parâmetros em métodos  
 Embora o uso de `out` e `ref` é, em geral, desencorajado no .NET Framework, aqui estão as regras a seguir quando elas estiverem presentes:  
  
 Dado um método síncrono *MethodName*:  
  
-   `out`parâmetros para *MethodName* não deve fazer parte de *MethodName*`Async`. Em vez disso, eles devem fazer parte de *MethodName* `CompletedEventArgs` com o mesmo nome como seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).  
  
-   `ref`parâmetros para *MethodName* devem aparecer como parte do *MethodName*`Async`e como parte do *MethodName* `CompletedEventArgs` com o mesmo nome de seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).  
  
 Por exemplo, dado:  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 O método assíncrono e sua <xref:System.ComponentModel.AsyncCompletedEventArgs> classe teria esta aparência:  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Como implementar um componente compatível com o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Como executar uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Como implementar um formulário que usa uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Decidindo quando implementar o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Programação multi-threaded com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
