---
title: "Transações de fluxo de entrada e saída de serviços de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d097068720bb937911316fdb29a83ba0e8e67713
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Transações de fluxo de entrada e saída de serviços de fluxo de trabalho
Serviços de fluxo de trabalho e os clientes podem participar de transações.  Para uma operação de serviço fazer parte de uma transação de ambiente, coloque uma <xref:System.ServiceModel.Activities.Receive> atividade dentro de um <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade. Todas as chamadas feitas por um <xref:System.ServiceModel.Activities.Send> ou um <xref:System.ServiceModel.Activities.SendReply> atividade dentro de <xref:System.ServiceModel.Activities.TransactedReceiveScope> também será feita dentro da transação de ambiente. Um aplicativo de cliente de fluxo de trabalho pode criar uma transação de ambiente usando o <xref:System.Activities.Statements.TransactionScope> atividade e chamar operações de serviço usando a transação de ambiente. Este tópico orienta a criação de um serviço de fluxo de trabalho e o cliente de fluxo de trabalho que participam em transações.  
  
> [!WARNING]
>  Se uma instância de serviço de fluxo de trabalho está carregada em uma transação e o fluxo de trabalho contém um <xref:System.Activities.Statements.Persist> atividade, a instância de fluxo de trabalho parará até que a transação de tempo limite.  
  
> [!IMPORTANT]
>  Sempre que você usar um <xref:System.ServiceModel.Activities.TransactedReceiveScope> é recomendável colocar todos os Receives no fluxo de trabalho em <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividades.  
  
> [!IMPORTANT]
>  Ao usar <xref:System.ServiceModel.Activities.TransactedReceiveScope> e as mensagens chegam na ordem incorreta, o fluxo de trabalho será anulado ao tentar entregar a primeira mensagem fora de ordem. Você deve se certificar de que o fluxo de trabalho está sempre em um estado parando ponto quando o fluxo de trabalho ocioso. Isso permitirá que você reinicie o fluxo de trabalho de um ponto de persistência anterior o fluxo de trabalho deve ser anulado.  
  
### <a name="create-a-shared-library"></a>Criar uma biblioteca compartilhada  
  
1.  Crie uma solução do Visual Studio vazio novo.  
  
2.  Adicionar um novo projeto de biblioteca de classe chamado `Common`. Adicione referências aos assemblies a seguir:  
  
    -   System.Activities.dll  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceModel.Activities.dll  
  
    -   System.Transactions.dll  
  
3.  Adicionar uma nova classe chamada `PrintTransactionInfo` para o `Common` projeto. Essa classe é derivada de <xref:System.Activities.NativeActivity> e sobrecargas de <xref:System.Activities.NativeActivity.Execute%2A> método.  
  
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
  
     Esta é uma atividade nativo que exibe informações sobre a transação de ambiente e é usada para o serviço e o cliente fluxos de trabalho usados neste tópico. Compile a solução para disponibilizar essa atividade no **comuns** seção o **caixa de ferramentas**.  
  
### <a name="implement-the-workflow-service"></a>Implementar o serviço de fluxo de trabalho  
  
1.  Adicionar um novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço de fluxo de trabalho, chamado `WorkflowService` para o `Common` projeto. Para isso, clique em direito a `Common` projeto, selecione **adicionar**, **Novo Item...** , Selecione **fluxo de trabalho** em **modelos instalados** e selecione **serviço de fluxo de trabalho WCF**.  
  
     ![Adicionando um serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")  
  
2.  Excluir o padrão `ReceiveRequest` e `SendResponse` atividades.  
  
3.  Arraste e solte um <xref:System.Activities.Statements.WriteLine> atividade de `Sequential Service` atividade. Defina a propriedade de texto como `"Workflow Service starting ..."` conforme mostrado no exemplo a seguir.  
  
     ![Adicionando uma atividade WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")  
  
4.  Arraste e solte um <xref:System.ServiceModel.Activities.TransactedReceiveScope> depois que o <xref:System.Activities.Statements.WriteLine> atividade. O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade pode ser encontrada no **mensagens** seção o **caixa de ferramentas**. O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade é composta de duas seções **solicitação** e **corpo**. O **solicitação** seção contém o <xref:System.ServiceModel.Activities.Receive> atividade. O **corpo** seção contém as atividades sejam executadas em uma transação depois que uma mensagem foi recebida.  
  
     ![Adicionando uma atividade de TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")  
  
5.  Selecione o <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade e clique no **variáveis** botão. Adicione as seguintes variáveis.  
  
     ![Adicionar variáveis ao TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")  
  
    > [!NOTE]
    >  Você pode excluir a variável de dados que existe por padrão. Você também pode usar a variável de identificador existente.  
  
6.  Arrastar e soltar uma <xref:System.ServiceModel.Activities.Receive> atividade dentro a **solicitação** seção o <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade. Defina as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |CanCreateInstance|True (a caixa de seleção)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     O fluxo de trabalho deve ter esta aparência:  
  
     ![Adicionando uma atividade Receive](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")  
  
7.  Clique o **definir...**  link no <xref:System.ServiceModel.Activities.Receive> atividade e faça as seguintes configurações:  
  
     ![Definindo configurações de mensagem para a atividade de receber](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")  
  
8.  Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade na seção de corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Dentro de <xref:System.Activities.Statements.Sequence> atividade arrastar e soltar dois <xref:System.Activities.Statements.WriteLine> atividades e o conjunto a <xref:System.Activities.Statements.WriteLine.Text%2A> propriedades conforme mostrado na tabela a seguir.  
  
    |Atividade|Valor|  
    |--------------|-----------|  
    |1º de WriteLine|"Serviço: receber concluído"|  
    |2º WriteLine|"Serviço: recebidos =" + requestMessage|  
  
     Agora, o fluxo de trabalho deve ser assim:  
  
     ![Adicionando atividades de WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")  
  
9. Arraste e solte o `PrintTransactionInfo` atividade depois que o segundo <xref:System.Activities.Statements.WriteLine> atividade no **corpo** no <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.  
  
     ![Depois de adicionar PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")  
  
10. Arraste e solte um <xref:System.Activities.Statements.Assign> atividade após o `PrintTransactionInfo` atividade e defina suas propriedades de acordo com a tabela a seguir.  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |Para|replyMessage|  
    |Valor|"Serviço: enviar resposta."|  
  
11. Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o <xref:System.Activities.Statements.Assign> atividade e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "serviço: começar a resposta."  
  
     Agora, o fluxo de trabalho deve ser assim:  
  
     ![Depois de adicionar atribuir e WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")  
  
12. Clique com botão direito do <xref:System.ServiceModel.Activities.Receive> atividade e selecione **criar SendReply** e colá-lo após a última <xref:System.Activities.Statements.WriteLine> atividade. Clique o **definir...**  link no `SendReplyToReceive` atividade e faça as seguintes configurações.  
  
     ![Configurações de mensagem de resposta](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")  
  
13. Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o `SendReplyToReceive` atividade e o conjunto tem <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "serviço: resposta enviada."  
  
14. Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e definir seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "serviço: termina de fluxo de trabalho, pressione ENTER para sair."  
  
     O fluxo de trabalho do serviço completo deve ter esta aparência:  
  
     ![Concluir o fluxo de trabalho do serviço](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")  
  
### <a name="implement-the-workflow-client"></a>Implementar o cliente do fluxo de trabalho  
  
1.  Adicionar um novo aplicativo de fluxo de trabalho WCF, chamado `WorkflowClient` para o `Common` projeto. Para isso, clique em direito a `Common` projeto, selecione **adicionar**, **Novo Item...** , Selecione **fluxo de trabalho** em **modelos instalados** e selecione **atividade**.  
  
     ![Adicionar um projeto de atividade](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")  
  
2.  Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade na superfície de design.  
  
3.  Dentro de <xref:System.Activities.Statements.Sequence> atividade arrastar e soltar um <xref:System.Activities.Statements.WriteLine> atividade e o conjunto de seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade `"Client: Workflow starting"`. Agora, o fluxo de trabalho deve ser assim:  
  
     ![Adicionar uma atividade WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")  
  
4.  Arraste e solte um <xref:System.Activities.Statements.TransactionScope> atividade após o <xref:System.Activities.Statements.WriteLine> atividade.  Selecione o <xref:System.Activities.Statements.TransactionScope> atividade, clique botão de variáveis e adicione as seguintes variáveis.  
  
     ![Adicionar variáveis ao TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")  
  
5.  Arraste e solte um <xref:System.Activities.Statements.Sequence> atividade no corpo do <xref:System.Activities.Statements.TransactionScope> atividade.  
  
6.  Arraste e solte um `PrintTransactionInfo` atividade dentro de<xref:System.Activities.Statements.Sequence>  
  
7.  Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o `PrintTransactionInfo` atividade e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade como "Cliente: início enviar". Agora, o fluxo de trabalho deve ser assim:  
  
     ![Adicionando atividades](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")  
  
8.  Arraste e solte um <xref:System.ServiceModel.Activities.Send> atividade após o <xref:System.Activities.Statements.Assign> atividade e defina as seguintes propriedades:  
  
    |Propriedade|Valor|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Agora, o fluxo de trabalho deve ser assim:  
  
     ![Definir as propriedades da atividade enviar](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")  
  
9. Clique o **definir...**  link e verifique as seguintes configurações:  
  
     ![Configurações de mensagem de atividade de envio](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")  
  
10. Clique com botão direito do <xref:System.ServiceModel.Activities.Send> atividade e selecione **ReceiveReply criar**. O <xref:System.ServiceModel.Activities.ReceiveReply> atividade será colocada automaticamente após o <xref:System.ServiceModel.Activities.Send> atividade.  
  
11. Clique em... a definir um link na atividade ReceiveReplyForSend e verifique as seguintes configurações:  
  
     ![Definindo a mensagem receiveforsend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")  
  
12. Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade entre o <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "cliente: enviar completa."  
  
13. Arrastar e soltar uma <xref:System.Activities.Statements.WriteLine> atividade após o <xref:System.ServiceModel.Activities.ReceiveReply> atividade e defina seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade para "do lado do cliente: resposta recebida =" + replyMessage  
  
14. Arraste e solte um `PrintTransactionInfo` atividade após o <xref:System.Activities.Statements.WriteLine> atividade.  
  
15. Arraste e solte um <xref:System.Activities.Statements.WriteLine> atividade no final do fluxo de trabalho e definir seu <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade "Extremidades do fluxo de trabalho do cliente." O fluxo de trabalho do cliente deve se parecer com o diagrama a seguir.  
  
     ![O cliente workfliow](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")  
  
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
  
1.  Adicionar um novo projeto de aplicativo de Console chamado `Client` à solução. Adicione uma referência a System.Activities.dll.  
  
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
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Visão geral de transações do Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [Uso de TransactedReceiveScope](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
