---
title: Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 7926c5a8ce1ca1ba3e24c4d1681ae12c18039924
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963337"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
Os serviços de fluxo de trabalho e os clientes podem participar de transações.  Para que uma operação de serviço se torne parte de uma transação de ambiente <xref:System.ServiceModel.Activities.Receive> , coloque uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade em uma atividade. Todas as chamadas feitas por <xref:System.ServiceModel.Activities.Send> uma ou <xref:System.ServiceModel.Activities.SendReply> uma atividade dentro <xref:System.ServiceModel.Activities.TransactedReceiveScope> do também serão feitas dentro da transação de ambiente. Um aplicativo cliente de fluxo de trabalho pode criar uma transação de <xref:System.Activities.Statements.TransactionScope> ambiente usando a atividade e chamar operações de serviço usando a transação de ambiente. Este tópico o orienta na criação de um serviço de fluxo de trabalho e cliente de fluxo de trabalho que participam de transações.  
  
> [!WARNING]
>  Se uma instância do serviço de fluxo de trabalho for carregada em uma transação e <xref:System.Activities.Statements.Persist> o fluxo de trabalho contiver uma atividade, a instância do fluxo de trabalho será bloqueada até que a transação expire.  
  
> [!IMPORTANT]
> Sempre que você usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> um, é recomendável fazer todos os recebimentos no <xref:System.ServiceModel.Activities.TransactedReceiveScope> fluxo de trabalho dentro das atividades.  
  
> [!IMPORTANT]
> Ao usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> o e as mensagens chegarem na ordem incorreta, o fluxo de trabalho será anulado ao tentar entregar a primeira mensagem fora de ordem. Você deve verificar se o fluxo de trabalho está sempre em um ponto de interrupção consistente quando o fluxo de trabalho está ocioso. Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior caso o fluxo de trabalho seja anulado.  
  
### <a name="create-a-shared-library"></a>Criar uma biblioteca compartilhada  
  
1. Crie uma nova solução vazia do Visual Studio.  
  
2. Adicione um novo projeto de biblioteca de `Common`classes chamado. Adicione referências aos assemblies a seguir:  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Adicione uma nova classe chamada `PrintTransactionInfo` `Common` ao projeto. Essa classe é derivada de <xref:System.Activities.NativeActivity> e sobrecarrega o <xref:System.Activities.NativeActivity.Execute%2A> método.  
  
    ```  
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
  
     Essa é uma atividade nativa que exibe informações sobre a transação de ambiente e é usada nos fluxos de trabalho de serviço e cliente usados neste tópico. Crie a solução para tornar essa atividade disponível na seção **comum** da caixa de **ferramentas**.  
  
### <a name="implement-the-workflow-service"></a>Implementar o serviço de fluxo de trabalho  
  
1. Adicione um novo serviço de fluxo de trabalho `WorkflowService` WCF, `Common` chamado para o projeto. Para fazer isso, clique com `Common` o botão direito do mouse no projeto, selecione **Adicionar**, **novo item...** , selecione **fluxo de trabalho** em **modelos instalados** e selecione **serviço de fluxo de trabalho WCF**.  
  
     ![Adicionando um serviço de fluxo de trabalho](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Exclua o `ReceiveRequest` padrão `SendResponse` e as atividades.  
  
3. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade `Sequential Service` na atividade. Defina a propriedade `"Workflow Service starting ..."` Text como, conforme mostrado no exemplo a seguir.  
  
     ! [Adicionando uma atividade WriteLine à atividade de serviço sequencial (./Media/flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. Arraste e solte um <xref:System.ServiceModel.Activities.TransactedReceiveScope> após a <xref:System.Activities.Statements.WriteLine> atividade. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada na seção **mensagens** da caixa de **ferramentas**. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta de duas seções **solicitação** e **corpo**. A seção **solicitação** contém a <xref:System.ServiceModel.Activities.Receive> atividade. A seção **corpo** contém as atividades a serem executadas em uma transação depois que uma mensagem é recebida.  
  
     ![Adicionando uma atividade TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Selecione a <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade e clique no botão **variáveis** . Adicione as variáveis a seguir.  
  
     ![Adicionando variáveis ao TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Você pode excluir a variável de dados que está lá por padrão. Você também pode usar a variável de identificador existente.  
  
6. Arraste e solte uma <xref:System.ServiceModel.Activities.Receive> atividade dentro da seção de **solicitação** da <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade. Defina as propriedades a seguir:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |CanCreateInstance|True (marque a caixa de seleção)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     O fluxo de trabalho deve ser assim:  
  
     ![Adicionando uma atividade Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Clique no link **definir...** na <xref:System.ServiceModel.Activities.Receive> atividade e faça as seguintes configurações:  
  
     ![Definindo as configurações de mensagem para a atividade receber](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade na seção corpo <xref:System.ServiceModel.Activities.TransactedReceiveScope>do. Na atividade, arraste e solte duas <xref:System.Activities.Statements.WriteLine> atividades e defina as <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir. <xref:System.Activities.Statements.Sequence>  
  
    |Atividade|Valor|  
    |--------------|-----------|  
    |1º WriteLine|Serviço Recebimento concluído "|  
    |2º WriteLine|Serviço Received = "+ requestMessage|  
  
     O fluxo de trabalho agora deve ser assim:  
  
     ![Sequência após adicionar atividades WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Arraste e solte a `PrintTransactionInfo` atividade após a segunda <xref:System.Activities.Statements.WriteLine> atividade <xref:System.ServiceModel.Activities.TransactedReceiveScope> no **corpo** da atividade.  
  
     ![Sequência após adicionar PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Arraste e solte uma <xref:System.Activities.Statements.Assign> atividade após a `PrintTransactionInfo` atividade e defina suas propriedades de acordo com a tabela a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |Para|replyMessage|  
    |Valor|Serviço Enviando resposta ".|  
  
11. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.Activities.Statements.Assign> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "Service: Iniciar resposta ".  
  
     O fluxo de trabalho agora deve ser assim:  
  
     ![Depois de adicionar WriteLine e atribuir](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Clique com o <xref:System.ServiceModel.Activities.Receive> botão direito do mouse na atividade e selecione **criar SendReply** e <xref:System.Activities.Statements.WriteLine> Cole-a após a última atividade. Clique no link **definir...** na `SendReplyToReceive` atividade e faça as seguintes configurações.  
  
     ![Configurações da mensagem de resposta](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a `SendReplyToReceive` <xref:System.Activities.Statements.WriteLine.Text%2A> atividade e defina sua propriedade como "serviço: Resposta enviada. "  
  
14. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade na parte inferior do fluxo de trabalho e defina <xref:System.Activities.Statements.WriteLine.Text%2A> sua propriedade como "serviço: Fluxo de trabalho termina, pressione ENTER para sair ".  
  
     O fluxo de trabalho do serviço concluído deve ter a seguinte aparência:  
  
     ![Concluir o fluxo de trabalho do serviço](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementar o cliente de fluxo de trabalho  
  
1. Adicione um novo aplicativo de fluxo de trabalho `WorkflowClient` do WCF `Common` , chamado para o projeto. Para fazer isso, clique com `Common` o botão direito do mouse no projeto, selecione **Adicionar**, **novo item...** , selecione **fluxo de trabalho** em **modelos instalados** e selecione **atividade**.  
  
     ![Adicionar um projeto de atividade](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade na superfície de design.  
  
3. Na atividade, arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como `"Client: Workflow starting"`. <xref:System.Activities.Statements.Sequence> O fluxo de trabalho agora deve ser assim:  
  
     ![Adicionar uma atividade WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Arraste e solte uma <xref:System.Activities.Statements.TransactionScope> atividade após a <xref:System.Activities.Statements.WriteLine> atividade.  Selecione a <xref:System.Activities.Statements.TransactionScope> atividade, clique no botão variáveis e adicione as variáveis a seguir.  
  
     ![Adicionar variáveis ao TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade no corpo <xref:System.Activities.Statements.TransactionScope> da atividade.  
  
6. Arraste e solte uma `PrintTransactionInfo` atividade dentro do<xref:System.Activities.Statements.Sequence>  
  
7. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a `PrintTransactionInfo` atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "cliente: Começando envio ". O fluxo de trabalho agora deve ser assim:  
  
     ![Adicionando cliente: Iniciando atividades de envio](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Arraste e solte uma <xref:System.ServiceModel.Activities.Send> atividade após a <xref:System.Activities.Statements.Assign> atividade e defina as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     O fluxo de trabalho agora deve ser assim:  
  
     ![Definindo as propriedades da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Clique no link **definir...** e faça as seguintes configurações:  
  
     ![Configurações de mensagem da atividade Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Clique com o <xref:System.ServiceModel.Activities.Send> botão direito do mouse na atividade e selecione **criar ReceiveReply**. A <xref:System.ServiceModel.Activities.ReceiveReply> atividade será colocada automaticamente após a <xref:System.ServiceModel.Activities.Send> atividade.  
  
11. Clique no botão Definir... link na atividade ReceiveReplyForSend e faça as seguintes configurações:  
  
     ![Definindo as configurações de mensagem de ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade entre as <xref:System.ServiceModel.Activities.Send> atividades <xref:System.ServiceModel.Activities.ReceiveReply> e e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "cliente: Envio concluído. "  
  
13. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.ServiceModel.Activities.ReceiveReply> atividade e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "lado do cliente: Resposta recebida = "+ replyMessage  
  
14. Arraste e solte uma `PrintTransactionInfo` atividade após a <xref:System.Activities.Statements.WriteLine> atividade.  
  
15. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e defina sua <xref:System.Activities.Statements.WriteLine.Text%2A> Propriedade como "término do fluxo de trabalho do cliente". O fluxo de trabalho do cliente concluído deve ser semelhante ao diagrama a seguir.  
  
     ![O fluxo de trabalho do cliente concluído](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Compile a solução.  
  
### <a name="create-the-service-application"></a>Criar o aplicativo de serviço  
  
1. Adicione um novo projeto de aplicativo de `Service` console chamado à solução. Adicione referências aos assemblies a seguir:  
  
    1. System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. System.ServiceModel.Activities.dll  
  
2. Abra o arquivo Program.cs gerado e o seguinte código:  
  
    ```  
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
  
3. Adicione o seguinte arquivo app. config ao projeto.  
  
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
  
### <a name="create-the-client-application"></a>Criar o aplicativo cliente  
  
1. Adicione um novo projeto de aplicativo de `Client` console chamado à solução. Adicione uma referência a System. Activities. dll.  
  
2. Abra o arquivo program.cs e adicione o código a seguir.  
  
    ```  
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
  
## <a name="see-also"></a>Consulte também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Visão geral de transações do Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
