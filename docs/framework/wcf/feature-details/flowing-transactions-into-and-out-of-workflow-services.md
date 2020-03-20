---
title: Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185272"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
Serviços de fluxo de trabalho e clientes podem participar de transações.  Para que uma operação de serviço se <xref:System.ServiceModel.Activities.Receive> torne parte <xref:System.ServiceModel.Activities.TransactedReceiveScope> de uma transação ambiental, coloque uma atividade dentro de uma atividade. Quaisquer chamadas feitas <xref:System.ServiceModel.Activities.Send> por <xref:System.ServiceModel.Activities.SendReply> uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> ou uma atividade dentro do também serão feitas dentro da transação ambiental. Um aplicativo cliente de fluxo de trabalho <xref:System.Activities.Statements.TransactionScope> pode criar uma transação ambiente usando as operações de atividade e serviço de chamada usando a transação ambiente. Este tópico orienta você a criar um cliente de serviço de fluxo de trabalho e fluxo de trabalho que participe de transações.  
  
> [!WARNING]
> Se uma instância de serviço de fluxo de trabalho <xref:System.Activities.Statements.Persist> for carregada dentro de uma transação e o fluxo de trabalho contiver uma atividade, a instância do fluxo de trabalho será bloqueada até que a transação seja ativada.  
  
> [!IMPORTANT]
> Sempre que <xref:System.ServiceModel.Activities.TransactedReceiveScope> você usar um é recomendado colocar todos <xref:System.ServiceModel.Activities.TransactedReceiveScope> os Recebeds no fluxo de trabalho dentro das atividades.  
  
> [!IMPORTANT]
> Ao <xref:System.ServiceModel.Activities.TransactedReceiveScope> usar e as mensagens chegarem na ordem incorreta, o fluxo de trabalho será abortado ao tentar entregar a primeira mensagem fora do pedido. Você deve ter certeza de que seu fluxo de trabalho está sempre em um ponto de parada consistente quando o fluxo de trabalho está ocioso. Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior caso o fluxo de trabalho seja abortado.  
  
### <a name="create-a-shared-library"></a>Crie uma biblioteca compartilhada  
  
1. Crie uma nova solução de estúdio visual vazia.  
  
2. Adicione um novo projeto `Common`de biblioteca de classe chamado . Adicione referências aos assemblies a seguir:  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Adicione uma nova `PrintTransactionInfo` classe `Common` chamada ao projeto. Esta classe é <xref:System.Activities.NativeActivity> derivada e <xref:System.Activities.NativeActivity.Execute%2A> sobrecarrega o método.  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     Esta é uma atividade nativa que exibe informações sobre a transação ambiental e é usada tanto nos fluxos de serviço quanto nos fluxos de trabalho do cliente usados neste tópico. Construa a solução para disponibilizar essa atividade na seção **Comum** da **Caixa de Ferramentas**.  
  
### <a name="implement-the-workflow-service"></a>Implementar o serviço de fluxo de trabalho  
  
1. Adicione um novo Serviço de `WorkflowService` Fluxo `Common` de Trabalho WCF, chamado ao projeto. Para fazer isso `Common` com o botão direito do mouse no projeto, **selecione Adicionar**, **Novo Item ...**, Selecione Fluxo de **trabalho** em **Modelos instalados** e selecione **WCF Workflow Service**.  
  
     ![Adicionando um serviço de fluxo de trabalho](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Exclua `ReceiveRequest` o `SendResponse` padrão e as atividades.  
  
3. Arraste e <xref:System.Activities.Statements.WriteLine> solte `Sequential Service` uma atividade na atividade. Defina a `"Workflow Service starting ..."` propriedade de texto como mostrado no exemplo a seguir.  
  
     ! [Adicionar uma atividade WriteLine à atividade serviço seqüencial(./mídia/fluxo-transações-em-e-sair-do-fluxo de trabalho-serviços/add-writeline-sequencial-service.jpg)  
  
4. Arraste e <xref:System.ServiceModel.Activities.TransactedReceiveScope> solte um após a <xref:System.Activities.Statements.WriteLine> atividade. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada na seção **De Mensagens** da **Caixa de Ferramentas**. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta por duas seções **Solicitação** e **Corpo**. A **Request** seção <xref:System.ServiceModel.Activities.Receive> Solicitar contém a atividade. A seção **Corpo** contém as atividades a serem executadas dentro de uma transação após o recebimento de uma mensagem.  
  
     ![Adicionando uma atividade TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Selecione <xref:System.ServiceModel.Activities.TransactedReceiveScope> a atividade e clique no botão **Variáveis.** Adicione as seguintes variáveis.  
  
     ![Adicionando variáveis ao TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Você pode excluir a variável de dados que está lá por padrão. Você também pode usar a variável de alça existente.  
  
6. Arraste e <xref:System.ServiceModel.Activities.Receive> solte uma atividade <xref:System.ServiceModel.Activities.TransactedReceiveScope> na seção **Solicitar** da atividade. Defina as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |CanCreateInstance|True (verifique a caixa de seleção)|  
    |OperationName|Sample|  
    |ServiceContractName|ITransactionSample|  
  
     O fluxo de trabalho deve ser assim:  
  
     ![Adicionando uma atividade Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Clique no **link Definir...** na <xref:System.ServiceModel.Activities.Receive> atividade e faça as seguintes configurações:  
  
     ![Definindo as configurações de mensagem para a atividade Receber](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Arraste e <xref:System.Activities.Statements.Sequence> solte uma atividade <xref:System.ServiceModel.Activities.TransactedReceiveScope>na seção Corpo do . Dentro <xref:System.Activities.Statements.Sequence> da atividade arraste e solte duas <xref:System.Activities.Statements.WriteLine> atividades e defina as <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir.  
  
    |Atividade|Valor|  
    |--------------|-----------|  
    |1ª WriteLine|"Serviço: Receber Concluído"|  
    |2ª WriteLine|"Serviço: Recebido = + requestMessage|  
  
     O fluxo de trabalho agora deve ser assim:  
  
     ![Seqüência após adicionar atividades writeLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Arraste e `PrintTransactionInfo` solte <xref:System.Activities.Statements.WriteLine> a atividade após <xref:System.ServiceModel.Activities.TransactedReceiveScope> a segunda atividade no **Corpo** na atividade.  
  
     ![Seqüência após adicionar PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Arraste e <xref:System.Activities.Statements.Assign> solte `PrintTransactionInfo` uma atividade após a atividade e defina suas propriedades de acordo com a tabela a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |Para|respostaMensagem|  
    |Valor|"Serviço: envio de resposta."|  
  
11. Arraste e <xref:System.Activities.Statements.WriteLine> solte <xref:System.Activities.Statements.Assign> uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> após a atividade e defina sua propriedade como "Serviço: Inicie a resposta".  
  
     O fluxo de trabalho agora deve ser assim:  
  
     ![Depois de adicionar WriteLine e atribuir](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Clique com <xref:System.ServiceModel.Activities.Receive> o botão direito do mouse na <xref:System.Activities.Statements.WriteLine> atividade e selecione **Criar EnviarResponder** e cole-a após a última atividade. Clique no **link Definir...** na `SendReplyToReceive` atividade e faça as seguintes configurações.  
  
     ![Configurações da mensagem de resposta](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Arraste e <xref:System.Activities.Statements.WriteLine> solte `SendReplyToReceive` uma atividade após <xref:System.Activities.Statements.WriteLine.Text%2A> a atividade e defina sua propriedade como "Serviço: Resposta enviada".  
  
14. Arraste e <xref:System.Activities.Statements.WriteLine> solte uma atividade na parte <xref:System.Activities.Statements.WriteLine.Text%2A> inferior do fluxo de trabalho e defina sua propriedade como "Serviço: termina o fluxo de trabalho, pressione ENTER para sair".  
  
     O fluxo de trabalho de serviço concluído deve ser assim:  
  
     ![Concluir o fluxo de trabalho do serviço](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementar o cliente do fluxo de trabalho  
  
1. Adicione um novo aplicativo wcf `WorkflowClient` workflow, chamado para o `Common` projeto. Para fazer isso `Common` com o botão direito do mouse no projeto, **selecione Adicionar**, **Novo Item ...**, Selecione Fluxo de **trabalho** em **Modelos instalados** e selecione **Atividade**.  
  
     ![Adicionar um projeto de atividade](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Arraste e <xref:System.Activities.Statements.Sequence> solte uma atividade na superfície do projeto.  
  
3. Dentro <xref:System.Activities.Statements.Sequence> da atividade arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para `"Client: Workflow starting"`. O fluxo de trabalho agora deve ser assim:  
  
     ![Adicionar uma atividade WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Arraste e <xref:System.Activities.Statements.TransactionScope> solte <xref:System.Activities.Statements.WriteLine> uma atividade após a atividade.  Selecione <xref:System.Activities.Statements.TransactionScope> a atividade, clique no botão Variáveis e adicione as seguintes variáveis.  
  
     ![Adicionar variáveis ao TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Arraste e <xref:System.Activities.Statements.Sequence> solte uma <xref:System.Activities.Statements.TransactionScope> atividade no corpo da atividade.  
  
6. Arraste e `PrintTransactionInfo` solte uma atividade dentro do<xref:System.Activities.Statements.Sequence>  
  
7. Arraste e <xref:System.Activities.Statements.WriteLine> solte `PrintTransactionInfo` uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> após a atividade e defina sua propriedade como "Cliente: Iniciar envio". O fluxo de trabalho agora deve ser assim:  
  
     ![Adicionando cliente: iniciando atividades de envio](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Arraste e <xref:System.ServiceModel.Activities.Send> solte <xref:System.Activities.Statements.Assign> uma atividade após a atividade e defina as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |EndpointConfigurationName|fluxo de trabalhoServiceEndpoint|  
    |OperationName|Sample|  
    |ServiceContractName|ITransactionSample|  
  
     O fluxo de trabalho agora deve ser assim:  
  
     ![Definindo as propriedades da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Clique no **link Definir...** e faça as seguintes configurações:  
  
     ![Configurações de mensagem da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Clique com <xref:System.ServiceModel.Activities.Send> o botão direito do mouse na atividade e selecione **Criar ReceberResposta**. A <xref:System.ServiceModel.Activities.ReceiveReply> atividade será automaticamente colocada <xref:System.ServiceModel.Activities.Send> após a atividade.  
  
11. Clique em Definir... link na atividade ReceiveReplyForSend e faça as seguintes configurações:  
  
     ![Definindo as configurações de mensagem de ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Arraste e <xref:System.Activities.Statements.WriteLine> solte <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> entre as atividades e defina sua propriedade como "Cliente: Enviar completo".  
  
13. Arraste e <xref:System.Activities.Statements.WriteLine> solte <xref:System.ServiceModel.Activities.ReceiveReply> uma atividade <xref:System.Activities.Statements.WriteLine.Text%2A> após a atividade e defina sua propriedade como "Lado cliente: Resposta recebida = " + respostaMessage  
  
14. Arraste e `PrintTransactionInfo` solte <xref:System.Activities.Statements.WriteLine> uma atividade após a atividade.  
  
15. Arraste e <xref:System.Activities.Statements.WriteLine> solte uma atividade no final <xref:System.Activities.Statements.WriteLine.Text%2A> do fluxo de trabalho e defina sua propriedade como "Extremidades do fluxo de trabalho do cliente". O fluxo de trabalho do cliente concluído deve parecer com o seguinte diagrama.  
  
     ![O fluxo de trabalho do cliente concluído](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Compile a solução.  
  
### <a name="create-the-service-application"></a>Crie o aplicativo Serviço  
  
1. Adicione um novo projeto `Service` de aplicativo de console chamado à solução. Adicione referências aos assemblies a seguir:  
  
    1. System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. System.ServiceModel.Activities.dll  
  
2. Abra o arquivo Program.cs gerado e o seguinte código:  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };
          }  
    ```  
  
3. Adicione o seguinte arquivo app.config ao projeto.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a>Crie o aplicativo cliente  
  
1. Adicione um novo projeto `Client` de aplicativo de console chamado à solução. Adicione uma referência ao System.Activities.dll.  
  
2. Abra o arquivo program.cs e adicione o seguinte código.  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Confira também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Visão geral de transações do Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
