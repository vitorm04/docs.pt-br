---
title: 'Instruções passo a passo: implementando um formulário que usa uma operação em segundo plano'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
ms.openlocfilehash: 28b1ac924fb9b6b8cbc09db62ee33c6780bee820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542074"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>Instruções passo a passo: implementando um formulário que usa uma operação em segundo plano
Se você tem uma operação que levará algum tempo para ser concluída, e não desejar sua interface de usuário (UI) parar de responder ou "travar", você pode usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.  
  
 Este passo a passo ilustra como usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar cálculos demorados "em"segundo plano, enquanto a interface do usuário permanece responsiva.  Quando terminar, você terá um aplicativo que calcula números de Fibonacci de forma assíncrona. Embora o cálculo de um número de Fibonacci grande possa levar um tempo considerável, o thread de interface do usuário principal não será interrompido por esse atraso e o formulário será responsivo durante o cálculo.  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criando um aplicativo baseado no Windows  
  
-   Criando um <xref:System.ComponentModel.BackgroundWorker> no formulário  
  
-   Adição de manipuladores de evento assíncrono  
  
-   Adicionando relatórios de progresso e suporte a cancelamento  
  
 Para obter uma listagem completa do código usado neste exemplo, consulte [Como implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>Como criar um formulário que usa uma operação em segundo plano  
  
1.  Crie um projeto de aplicativos do baseado em Windows chamado `BackgroundWorkerExample`. Para obter detalhes, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Form1** e escolha **Renomear** no menu de atalho. Altere o nome de arquivo para `FibonacciCalculator`. Clique no botão **Sim** quando solicitado se desejar renomear todas as referências ao elemento de código '`Form1`'.  
  
3.  Arraste um <xref:System.Windows.Forms.NumericUpDown> controlar do **caixa de ferramentas** para o formulário. Definir o <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> propriedade `1` e o <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> propriedade `91`.  
  
4.  Adicionar dois <xref:System.Windows.Forms.Button> controles ao formulário.  
  
5.  Renomeie o primeiro <xref:System.Windows.Forms.Button> controle `startAsyncButton` e defina o <xref:System.Windows.Forms.Control.Text%2A> propriedade `Start Async`. Renomeie o segundo <xref:System.Windows.Forms.Button> controle `cancelAsyncButton`e defina o <xref:System.Windows.Forms.Control.Text%2A> propriedade `Cancel Async`. Definir seu <xref:System.Windows.Forms.Control.Enabled%2A> propriedade `false`.  
  
6.  Criar um manipulador de eventos para ambos os <xref:System.Windows.Forms.Button> dos controles <xref:System.Windows.Forms.Control.Click> eventos. Para detalhes, consulte [Como criar manipuladores de eventos usando o Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
7.  Arraste um <xref:System.Windows.Forms.Label> controlar do **caixa de ferramentas** para o formulário e renomeie- `resultLabel`.  
  
8.  Arraste um <xref:System.Windows.Forms.ProgressBar> controlar do **caixa de ferramentas** para o formulário.  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>Usando um BackgroundWorker no seu formulário  
 Você pode criar o <xref:System.ComponentModel.BackgroundWorker> para sua operação assíncrona usando o **Windows** **Forms Designer**.  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>Como criar um BackgroundWorker com o Designer  
  
-   Do **componentes** guia do **caixa de ferramentas**, arraste um <xref:System.ComponentModel.BackgroundWorker> para o formulário.  
  
## <a name="adding-asynchronous-event-handlers"></a>Adição de manipuladores de evento assíncrono  
 Agora você está pronto para adicionar manipuladores de eventos para o <xref:System.ComponentModel.BackgroundWorker> eventos assíncronos do componente. A operação demorada que será executada em segundo plano, que calcula os números de Fibonacci, é chamada por um desses manipuladores de eventos.  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>Como implementar manipuladores de evento assíncrono  
  
1.  No **propriedades** janela, com o <xref:System.ComponentModel.BackgroundWorker> componente ainda selecionado, clique no **eventos** botão. Clique duas vezes o <xref:System.ComponentModel.BackgroundWorker.DoWork> e <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> eventos para criar manipuladores de eventos. Para mais informações sobre como usar os manipuladores de evento, consulte [Como criar manipuladores de eventos usando o Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
2.  Crie um novo método, chamado `ComputeFibonacci`, no formulário. Esse método faz o trabalho real e ele será executado em segundo plano. Esse código demonstra a implementação recursiva do algoritmo de Fibonacci, que é notavelmente ineficiente, demorando mais tempo para concluir o cálculo de números maiores. Ele é usado aqui para fins ilustrativos, para mostrar uma operação que pode introduzir longos atrasos em seu aplicativo.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  No <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos, adicione uma chamada para o `ComputeFibonacci` método. Executar o primeiro parâmetro para `ComputeFibonacci` do <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> propriedade do <xref:System.ComponentModel.DoWorkEventArgs>. O <xref:System.ComponentModel.BackgroundWorker> e <xref:System.ComponentModel.DoWorkEventArgs> parâmetros serão usados posteriormente para o relatório de progresso e cancelamento de suporte. Atribuir o valor de retorno `ComputeFibonacci` para o <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> propriedade o <xref:System.ComponentModel.DoWorkEventArgs>. Esse resultado estará disponível para o <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos.  
  
    > [!NOTE]
    >  O <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos não faz referência a `backgroundWorker1` variável da instância diretamente, pois isso seria acoplar este manipulador de eventos para uma instância específica do <xref:System.ComponentModel.BackgroundWorker>. Em vez disso, uma referência para o <xref:System.ComponentModel.BackgroundWorker> que gerado esse evento é recuperado do `sender` parâmetro. Isso é importante quando o formulário hospeda mais de um <xref:System.ComponentModel.BackgroundWorker>. Também é importante não manipular quaisquer objetos de interface do usuário no seu <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos. Em vez disso, se comunicar com a interface do usuário por meio de <xref:System.ComponentModel.BackgroundWorker> eventos.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  No `startAsyncButton` do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos, adicione o código que inicia a operação assíncrona.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  No <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos, atribua o resultado do cálculo para o `resultLabel` controle.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>Adicionando relatórios de progresso e suporte a cancelamento  
 Para operações assíncronas que levarão um longo tempo, muitas vezes é desejável relatar o progresso ao usuário e permitir que o usuário cancele a operação. O <xref:System.ComponentModel.BackgroundWorker> classe fornece um evento que permite que você envie o andamento como seu prossegue de operação em segundo plano. Ele também fornece um sinalizador que permite que seu código de trabalho detectar uma chamada para <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> e interromper a mesmo.  
  
#### <a name="to-implement-progress-reporting"></a>Como implementar o relatório de progresso  
  
1.  Na janela **Propriedades**, selecione `backgroundWorker1`. Defina as propriedades <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> e <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> como `true`.  
  
2.  Declare duas variáveis no formulário `FibonacciCalculator`. Elas serão usadas para acompanhar o progresso.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  Adicionar um manipulador de eventos para o <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> evento. No <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> manipulador de eventos, atualize o <xref:System.Windows.Forms.ProgressBar> com o <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> propriedade do <xref:System.ComponentModel.ProgressChangedEventArgs> parâmetro.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>Como implementar o suporte ao cancelamento  
  
1.  No `cancelAsyncButton` do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos, adicione o código que cancela a operação assíncrona.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  Os fragmentos de código a seguir no relatório de método `ComputeFibonacci` progridem e dão suporte ao cancelamento.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Neste ponto, você pode compilar e executar o aplicativo Calculadora Fibonacci.  
  
#### <a name="to-test-your-project"></a>Como testar o projeto  
  
-   Pressione F5 para compilar e executar o aplicativo.  
  
     Enquanto o cálculo é executado em segundo plano, você verá o <xref:System.Windows.Forms.ProgressBar> exibir o progresso de cálculo até a conclusão. Você também pode cancelar a operação pendente.  
  
     Para números pequenos, o cálculo deve ser muito rápido, mas, para números maiores, você deve ver um atraso considerável. Se inserir um valor de 30 ou mais, você deverá ver um atraso de alguns segundos, dependendo da velocidade do seu computador. Para valores maiores que 40, poderá levar minutos ou horas para concluir o cálculo. Enquanto a calculadora estiver ocupada calculando um número de Fibonacci grande, observe que você pode movimentar livremente o formulário, minimizar, maximizar e até mesmo descartá-lo. Isso ocorre porque o thread da interface do usuário principal não está aguardando concluir o cálculo.  
  
## <a name="next-steps"></a>Próximas etapas  
 Agora que você implementou um formulário que usa um <xref:System.ComponentModel.BackgroundWorker> componente para executar uma computação em segundo plano, você pode explorar outras possibilidades para operações assíncronas:  
  
-   Usar vários <xref:System.ComponentModel.BackgroundWorker> objetos para várias operações simultâneas.  
  
-   Para depurar seu aplicativo multi-threaded, consulte [Como usar a janela Threads](/visualstudio/debugger/how-to-use-the-threads-window).  
  
-   Implemente seu próprio componente que dá suporte ao modelo de programação assíncrona. Para mais informações, consulte [Visão geral sobre o padrão assíncrono baseado em evento](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  O uso de multithreading de qualquer tipo pode expor o computador a bugs muito sérios e complexos. Consulte as [Melhores práticas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md) antes de implementar qualquer solução que use multithreading.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Práticas recomendadas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Multithreading em componentes](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [NÃO ESTÁ NO BUILD: multithreading no Visual Basic](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Como implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Passo a passo: executando uma operação em segundo plano](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [Componente BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
