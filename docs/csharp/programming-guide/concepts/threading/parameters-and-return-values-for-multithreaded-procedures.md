---
title: "Parâmetros e valores retornados para procedimentos multi-threaded (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fec0ad955439f0cd683ad56c8d6433eed2417304
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>Parâmetros e valores retornados para procedimentos multi-threaded (C#)
Fornecer e retornar valores em um aplicativo multithread é complicado porque o construtor para a classe thread deve ser passado como uma referência para um procedimento que não leva argumentos e não retorna nenhum valor. As seções a seguir mostram algumas maneiras simples de fornecer parâmetros e retornar valores de procedimentos em threads separados.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Fornecendo parâmetros para procedimentos multithread  
 A melhor maneira de fornecer parâmetros para uma chamada de método multithread é encapsular o método de destino em uma classe e definir campos para essa classe que servirão de parâmetros para o novo thread. A vantagem dessa abordagem é que você pode criar uma nova instância da classe, com seus próprios parâmetros, toda vez que desejar iniciar um novo thread. Por exemplo, suponha que você tenha uma função que calcula a área de um triângulo, como no código a seguir:  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Você pode escrever uma classe que encapsula a função `CalcArea` e cria campos para armazenar parâmetros de entrada, da seguinte maneira:  
  
```csharp  
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
  
 Para usar o `AreaClass`, você pode criar um objeto `AreaClass` e definir as propriedades `Base` e `Height` conforme mostrado no código a seguir:  
  
```csharp  
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
  
 Observe que o procedimento `TestArea` não verifica o valor do campo `Area` após chamar o método `CalcArea`. Como o `CalcArea` é executado em um thread separado, não há garantia de que o campo `Area` estará definido se você o verificar imediatamente após chamar `Thread.Start`. A próxima seção discute uma maneira melhor de retornar valores de procedimentos multithread.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Retornando valores de procedimentos multithread  
 Retornar valores de procedimentos executados em threads separados é complicado pelo fato de que os procedimentos não podem ser funções e não podem usar argumentos `ByRef`. A maneira mais fácil de retornar valores é usar o componente <xref:System.ComponentModel.BackgroundWorker> para gerenciar os threads e acionar um evento quando a tarefa estiver concluída e processar os resultados com um manipulador de eventos.  
  
 O exemplo a seguir retorna um valor acionando um evento de um procedimento em execução em um thread separado:  
  
```csharp  
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
  
 Você pode fornecer parâmetros e retornar valores para threads de pool de threads usando a variável de objeto de estado `ByVal` do método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>. Os threads do temporizador de thread também dão suporte a um objeto de estado para essa finalidade. Para obter informações sobre o pooling de threads e os temporizadores de thread, consulte [Pooling de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) e [Temporizadores de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instruções passo a passo: multithreading com o componente BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Pooling de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [Sincronização de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [Eventos](../../../../csharp/programming-guide/events/index.md)  
 [Aplicativos com multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegados](../../../../csharp/programming-guide/delegates/index.md)  
 [Multithreading em componentes](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
