---
title: "Par&#226;metros e valores de retorno para procedimentos multithread (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Par&#226;metros e valores de retorno para procedimentos multithread (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Fornecer e retornar valores em um aplicativo multithread é complicado porque o construtor para a classe thread deve ser passado como uma referência para um procedimento que não leva argumentos e não retorna nenhum valor. As seções a seguir mostram algumas maneiras simples de fornecer parâmetros e retornar valores de procedimentos em segmentos separados.  
  
## Fornecer parâmetros para procedimentos multithread  
 A melhor maneira de fornecer parâmetros para uma chamada de método com vários segmentos é encapsular o método de destino em uma classe e definir campos para a classe que servirá como parâmetros para o novo thread. A vantagem dessa abordagem é que você pode criar uma nova instância da classe, com seus próprios parâmetros, toda vez que você deseja iniciar um novo segmento. Por exemplo, suponha que você tenha uma função que calcula a área de um triângulo, como no seguinte código:  
  
```c#  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Você pode escrever uma classe que encapsula o `CalcArea` de função e cria campos para armazenar parâmetros de entrada, da seguinte maneira:  
  
```c#  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 Para usar o `AreaClass`, você pode criar um `AreaClass` do objeto e defina a `Base` e `Height` propriedades conforme mostrado no código a seguir:  
  
```c#  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 Observe que o `TestArea` procedimento verifica se o valor da `Area` campo depois de chamar o `CalcArea` método. Porque `CalcArea` é executado em um thread separado, o `Area` campo não é garantido para ser definido se você verificar imediatamente depois de chamar `Thread.Start`. A próxima seção discute uma melhor forma para retornar valores de procedimentos multithread.  
  
## Retornar valores de procedimentos multithread  
 Retornar valores de procedimentos executados em segmentos separados é complicado pelo fato de que os procedimentos não podem ser funções e não é possível usar `ByRef` argumentos. A maneira mais fácil de retornar valores é usar o <xref:System.ComponentModel.BackgroundWorker> componente para gerenciar seus segmentos e disparar um evento quando a tarefa estiver concluída e processar os resultados com um manipulador de eventos.  
  
 O exemplo a seguir retorna um valor ao disparar um evento de um procedimento em execução em um thread separado:  
  
```c#  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 Você pode fornecer parâmetros e retornar valores para segmentos de pool de segmentos usando opcional `ByVal` variável de objeto de estado de <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> método. Segmentos timer de segmento também oferecem suporte a um objeto de estado para essa finalidade. Para obter informações sobre o pool de segmento e timers de thread, consulte [Thread Pooling \(c\#\)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) e [Timers de thread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).  
  
## Consulte também  
 [Passo a passo: Multithreading com o componente BackgroundWorker \(c\#\)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)   
 [Thread Pooling \(c\#\)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)   
 [Sincronização de thread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)   
 [Eventos](../../../../csharp/programming-guide/events/index.md)   
 [Aplicativos multithread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Delegados](../../../../csharp/programming-guide/delegates/index.md)   
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)