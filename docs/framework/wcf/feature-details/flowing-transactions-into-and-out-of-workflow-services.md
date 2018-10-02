---
title: Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: f53bfa3c745a0d487a8daf23f399c1420e36c8ec
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036046"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
Os clientes e serviços de fluxo de trabalho podem participar de transações.  Para uma operação de serviço se tornar parte de uma transação de ambiente, coloque um <xref:System.ServiceModel.Activities.Receive> atividade dentro de um <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade. Todas as chamadas feitas por um <xref:System.ServiceModel.Activities.Send> ou um <xref:System.ServiceModel.Activities.SendReply> atividade dentro de <xref:System.ServiceModel.Activities.TransactedReceiveScope> também serão feitas dentro da transação de ambiente. Um aplicativo de cliente de fluxo de trabalho pode criar uma transação de ambiente usando o <xref:System.Activities.Statements.TransactionScope> atividade e chamar operações de serviço usando a transação de ambiente. Este tópico explica como criar um serviço de fluxo de trabalho e um cliente de fluxo de trabalho que participam nas transações.  
  
> [!WARNING]
>  Se uma instância de serviço de fluxo de trabalho é carregada em uma transação e o fluxo de trabalho contém um <xref:System.Activities.Statements.Persist> atividade, a instância de fluxo de trabalho permanecerá lá até que a transação de tempo limite.  
  
> [!IMPORTANT]
>  Sempre que você usar um <xref:System.ServiceModel.Activities.TransactedReceiveScope> -é recomendável colocar Receives todos no fluxo de trabalho dentro de <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividades.  
  
> [!IMPORTANT]
>  Ao usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> e as mensagens chegam na ordem incorreta, o fluxo de trabalho será anulado durante a tentativa de entregar a mensagem fora de ordem primeiro. Você deve verificar se que seu fluxo de trabalho está sempre em um processo consistente parando ponto quando o fluxo de trabalho fica ociosa. Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior o fluxo de trabalho deve ser anulado.  
  
### <a name="create-a-shared-library"></a>Criar uma biblioteca compartilhada  
  
1.  Crie uma solução do Visual Studio vazio novo.  
  
2.  Adicionar um novo projeto de biblioteca de classes chamado `Common`. Adicione referências aos assemblies a seguir:  
  
    -   System.Activities.dll  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceModel.Activities.dll  
  
    -   System.Transactions.dll  
  
3.  Adicionar uma nova classe chamada `PrintTransactionInfo` para o `Common` projeto. Essa classe é derivada de <xref:System.Activities.NativeActivity> e sobrecarrega o <xref:System.Activities.NativeActivity.Execute%2A> método.  
  
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
  
     Esta é uma atividade nativa que exibe informações sobre a transação de ambiente e é usada para o serviço e o cliente fluxos de trabalho usados neste tópico. Compile a solução para disponibilizar essa atividade na **comuns** seção o **caixa de ferramentas**.  
  
### <a name="implement-the-workflow-service"></a>Implementar o serviço de fluxo de trabalho  
  
1.  Adicionar um novo serviço de fluxo de trabalho do WCF, chamado `WorkflowService` para o `Common` projeto. Para isso, clique em direito a `Common` projeto, selecione **Add**, **Novo Item...** , Selecione **fluxo de trabalho** sob **modelos instalados** e selecione **serviço de fluxo de trabalho WCF**.  
  
     ![Adição de um serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")  
  
2.  Excluir o padrão `ReceiveRequest` e `SendResponse` atividades.  
  
3.  Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade para o `Sequential Service` atividade. Defina a propriedade text como `"Workflow Service starting ..."` conforme mostrado no exemplo a seguir.  
  
     ![Adicionando uma atividade WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")  
  
4.  Arraste e solte uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> depois que o <xref:System.Activities.Statements.WriteLine> atividade. O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada na **Messaging** seção o **caixa de ferramentas**. O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta por duas seções **solicitar** e **corpo**. O **solicitar** seção contém a <xref:System.ServiceModel.Activities.Receive> atividade. O **corpo** seção contém as atividades sejam executadas dentro de uma transação depois que uma mensagem foi recebida.  
  
     ![Adicionando uma atividade de TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")  
  
5.  Selecione o <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade e clique em de **variáveis** botão. Adicione as seguintes variáveis.  
  
     ![Adicionando variáveis ao TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")  
  
    > [!NOTE]
    >  Você pode excluir a variável de dados que está lá por padrão. Você também pode usar a variável de identificador existente.  
  
6.  Arrastar e soltar um <xref:System.ServiceModel.Activities.Receive> atividade dentro de **solicitar** seção do <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade. Defina as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |CanCreateInstance|True (a caixa de seleção)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     O fluxo de trabalho deve ter esta aparência:  
  
     ![Adicionando uma atividade de recebimento](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")  
  
7.  Clique o **defina...**  link no <xref:System.ServiceModel.Activities.Receive> atividade e fazer as seguintes configurações:  
  
     ![Definindo configurações de mensagem para a atividade de receber](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")  
  
8.  Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade na seção de corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Dentro do <xref:System.Activities.Statements.Sequence> atividade de arrastar e soltar dois <xref:System.Activities.Statements.WriteLine> atividades e defina o <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir.  
  
    |Atividade|Valor|  
    |--------------|-----------|  
    |1º WriteLine|"Serviço: receber concluído"|  
    |2º WriteLine|"Serviço: recebido =" + requestMessage|  
  
     Agora, o fluxo de trabalho deve ser assim:  
  
     ![Adicionando atividades de WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")  
  
9. Arraste e solte a `PrintTransactionInfo` atividade após a segunda <xref:System.Activities.Statements.WriteLine> atividade na **corpo** no <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.  
  
     ![Depois de adicionar PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")  
  
10. Arraste e solte uma <xref:System.Activities.Statements.Assign> atividade após a `PrintTransactionInfo` atividade e defina suas propriedades de acordo com a tabela a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |Para|replyMessage|  
    |Valor|"Serviço: enviar resposta."|  
  
11. Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.Activities.Statements.Assign> atividade e conjunto seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "serviço: começar a resposta."  
  
     Agora, o fluxo de trabalho deve ser assim:  
  
     ![Depois de adicionar atribuir e WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")  
  
12. Clique com botão direito do <xref:System.ServiceModel.Activities.Receive> atividade e selecione **criar SendReply** e cole-o depois do último <xref:System.Activities.Statements.WriteLine> atividade. Clique o **defina...**  link no `SendReplyToReceive` atividade e verifique as configurações a seguir.  
  
     ![Configurações de mensagem de resposta](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")  
  
13. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a `SendReplyToReceive` atividade e conjunto tem <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "serviço: resposta enviada."  
  
14. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade na parte inferior do fluxo de trabalho e definido seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "serviço: termina de fluxo de trabalho, pressione ENTER para sair."  
  
     O fluxo de trabalho de serviço concluída deve ter esta aparência:  
  
     ![Concluir o fluxo de trabalho de serviço](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")  
  
### <a name="implement-the-workflow-client"></a>Implementar o cliente de fluxo de trabalho  
  
1.  Adicionar um novo aplicativo de fluxo de trabalho WCF, chamado `WorkflowClient` para o `Common` projeto. Para isso, clique em direito a `Common` projeto, selecione **Add**, **Novo Item...** , Selecione **fluxo de trabalho** sob **modelos instalados** e selecione **atividade**.  
  
     ![Adicionar um projeto de atividade](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")  
  
2.  Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade na superfície de design.  
  
3.  Dentro de <xref:System.Activities.Statements.Sequence> atividade arrastar e soltar um <xref:System.Activities.Statements.WriteLine> atividade e conjunto de seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para `"Client: Workflow starting"`. Agora, o fluxo de trabalho deve ser assim:  
  
     ![Adicionar uma atividade WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")  
  
4.  Arraste e solte uma <xref:System.Activities.Statements.TransactionScope> atividade após a <xref:System.Activities.Statements.WriteLine> atividade.  Selecione o <xref:System.Activities.Statements.TransactionScope> atividade, clique as variáveis de botão e adicione as seguintes variáveis.  
  
     ![Adicione variáveis ao TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")  
  
5.  Arraste e solte uma <xref:System.Activities.Statements.Sequence> atividade no corpo do <xref:System.Activities.Statements.TransactionScope> atividade.  
  
6.  Arraste e solte um `PrintTransactionInfo` atividade dentro de <xref:System.Activities.Statements.Sequence>  
  
7.  Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a `PrintTransactionInfo` atividade e conjunto seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "Cliente: início enviar". Agora, o fluxo de trabalho deve ser assim:  
  
     ![Adicionando atividades](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")  
  
8.  Arraste e solte uma <xref:System.ServiceModel.Activities.Send> atividade após a <xref:System.Activities.Statements.Assign> atividade e defina as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Agora, o fluxo de trabalho deve ser assim:  
  
     ![Definindo as propriedades de atividade de envio](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")  
  
9. Clique o **defina...**  link e verifique as configurações a seguir:  
  
     ![Configurações de mensagem de atividade de envio](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")  
  
10. Clique com botão direito do <xref:System.ServiceModel.Activities.Send> atividade e selecione **crie ReceiveReply**. O <xref:System.ServiceModel.Activities.ReceiveReply> atividade será automaticamente colocada após o <xref:System.ServiceModel.Activities.Send> atividade.  
  
11. Clique em... a definir um link na atividade ReceiveReplyForSend e verifique as configurações a seguir:  
  
     ![Definindo a mensagem receiveforsend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")  
  
12. Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade entre o <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "cliente: enviar completa."  
  
13. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade após a <xref:System.ServiceModel.Activities.ReceiveReply> atividade e conjunto seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "do lado do cliente: resposta recebida =" + replyMessage  
  
14. Arraste e solte uma `PrintTransactionInfo` atividade após a <xref:System.Activities.Statements.WriteLine> atividade.  
  
15. Arraste e solte uma <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e definido seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "Termina de fluxo de trabalho do cliente". O fluxo de trabalho de cliente concluído deve parecer com o diagrama a seguir.  
  
     ![O cliente concluído workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")  
  
16. Compile a solução.  
  
### <a name="create-the-service-application"></a>Criar o aplicativo de serviço  
  
1.  Adicionar um novo projeto de aplicativo de Console chamado `Service` à solução. Adicione referências aos assemblies a seguir:  
  
    1.  System.Activities.dll  
  
    2.  System.ServiceModel.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
2.  Abra o arquivo Program.cs gerado e o código a seguir:  
  
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
  
3.  Adicione o seguinte arquivo App. config para o projeto.  
  
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
  
1.  Adicionar um novo projeto de aplicativo de Console chamado `Client` à solução. Adicione uma referência ao System.Activities.dll.  
  
2.  Abra o arquivo program.cs e adicione o código a seguir.  
  
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