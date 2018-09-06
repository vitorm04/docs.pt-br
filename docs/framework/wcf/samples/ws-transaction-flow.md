---
title: Fluxo de transação WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 35af3090c0f898578a5f8dfb81d02d22a0074ad2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43802574"
---
# <a name="ws-transaction-flow"></a>Fluxo de transação WS
Este exemplo demonstra o uso de uma transação de coordenadas de cliente e as opções de cliente e servidor para transações de fluxo usando o protocolo WS-AT ou OleTransactions. Este exemplo é baseado na [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de Calculadora, mas as operações são atribuídas para demonstrar o uso da `TransactionFlowAttribute` com o **TransactionFlowOption** enumeração para determinar para qual transação grau fluxo está habilitado. Dentro do escopo da transação fluída, um log das operações solicitados é escrito para um banco de dados e persiste até que a transação de coordenadas de cliente seja concluída - se a transação do cliente não for concluída, a transação de serviço Web garante que o as atualizações adequadas no banco de dados não são confirmadas.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Depois de iniciar uma conexão ao serviço e uma transação, o cliente acessa várias operações do serviço. O contrato para o serviço é definido da seguinte maneira com cada uma das operações que demonstra uma configuração diferente para o `TransactionFlowOption`.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 Isso define as operações na ordem em que eles devem ser processadas:  
  
-   Um `Add` solicitação de operação deve incluir uma transação fluída.  
  
-   Um `Subtract` solicitação de operação pode incluir uma transação fluída.  
  
-   Um `Multiply` solicitação de operação não deve incluir uma transação fluída por meio da configuração explícita de NotAllowed.  
  
-   Um `Divide` solicitação de operação não deve incluir uma transação fluída por meio da omissão de um `TransactionFlow` atributo.  
  
 Para habilitar o fluxo de transações, associações com o [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriedade habilitada deve ser usada além dos atributos operação apropriada. Neste exemplo, a configuração do serviço expõe um ponto de extremidade TCP e um ponto de extremidade HTTP, além de um ponto de extremidade de troca de metadados. O ponto de extremidade TCP e o ponto de extremidade HTTP usam as seguintes associações, ambos com o [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriedade habilitada.  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  A netTcpBinding fornecido pelo sistema permite a especificação da transactionProtocol enquanto o wsHttpBinding fornecido pelo sistema usa apenas o protocolo WSAtomicTransactionOctober2004 mais interoperável. Use os OleTransactions protocolo só está disponível para pelos clientes do Windows Communication Foundation (WCF).  
  
 Para a classe que implementa o `ICalculator` interface, todos os métodos são atribuídos com <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade definida como `true`. Essa configuração declara que todas as ações tomadas dentro do método ocorrem dentro do escopo de uma transação. Nesse caso, as ações tomadas incluem a gravação no banco de dados de log. Se a solicitação de operação inclui uma transação fluída, em seguida, ocorrem as ações dentro do escopo de transação de entrada ou um novo escopo de transação é gerado automaticamente.  
  
> [!NOTE]
>  O <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade define o comportamento local para as implementações de método de serviço e não define a capacidade do cliente ou o requisito para o fluxo de uma transação.  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 No cliente, o serviço `TransactionFlowOption` configurações nas operações são refletidas na definição gerada do cliente a `ICalculator` interface. Do Além disso, o serviço `transactionFlow` as configurações de propriedade são refletidas na configuração de aplicativo do cliente. O cliente pode selecionar o transporte e protocolo selecionando apropriado `endpointConfigurationName`.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  O comportamento observado deste exemplo é o mesmo, não importa qual transporte ou protocolo é escolhido.  
  
 Que você iniciou a conexão ao serviço, o cliente cria um novo `TransactionScope` em torno de chamadas para as operações de serviço.  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 As chamadas para as operações são da seguinte maneira:  
  
-   O `Add` solicitação flui a transação necessária para o serviço e ações do serviço ocorrerem dentro do escopo de transação do cliente.  
  
-   A primeira `Subtract` solicitação também flui a transação permitida para o serviço e novamente as ações do serviço ocorrem dentro do escopo de transação do cliente.  
  
-   A segunda `Subtract` solicitação é executada dentro de um novo escopo de transação declarado com o `TransactionScopeOption.Suppress` opção. Isso elimina a transação do cliente inicial externa e a solicitação não fluir uma transação para o serviço. Essa abordagem permite que um cliente explicitamente recusar e proteger contra o fluxo de uma transação para um serviço quando não é necessária. Ações do serviço ocorrem dentro do escopo de uma transação nova e desconectada.  
  
-   O `Multiply` solicitação não fluir uma transação para o serviço porque a definição de gerada do cliente do `ICalculator` interface inclui um <xref:System.ServiceModel.TransactionFlowAttribute> definido como <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.  
  
-   O `Divide` solicitação não fluir uma transação para o serviço porque novamente o cliente gerada pelo definição do `ICalculator` interface não incluir um `TransactionFlowAttribute`. Ações de serviço novamente ocorrem dentro do escopo de outra transação nova e desconectada.  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 O registro em log as solicitações de operação de serviço são exibidos na janela do console do serviço. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Após a execução bem-sucedida, o escopo de transação do cliente é concluída e todas as ações tomadas dentro do escopo são confirmadas. Especificamente, os registros de 5 observados são persistidos no banco de dados do serviço. O primeiro 2 deles ter ocorrido dentro do escopo de transação do cliente.  
  
 Se ocorreu uma exceção em qualquer lugar dentro do cliente `TransactionScope` e em seguida, a transação não pode concluir. Isso faz com que os registros feitos no log dentro do escopo não ser confirmado no banco de dados. Esse efeito pode ser observado, repetindo o exemplo de execução após comentar a chamada para concluir o externo `TransactionScope`. Em tal uma execução, somente as ações últimos 3 (da segunda `Subtract`, o `Multiply` e o `Divide` solicitações) são registrados porque a transação do cliente não fluir para aqueles.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Para compilar a versão c# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  Certifique-se de que você tenha instalado o SQL Server Express Edition ou SQL Server e que a cadeia de caracteres de conexão foi definida corretamente no arquivo de configuração de aplicativo do serviço. Para executar o exemplo sem usar um banco de dados, defina o `usingSql` valor no arquivo de configuração de aplicativo do serviço para `false`  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Para configuração entre computadores, habilite o coordenador de transações distribuídas usando as instruções abaixo e usar a ferramenta de WsatConfig.exe do SDK do Windows para habilitar o suporte de rede de transações do WCF. Ver [Configurando o suporte a transações WS-Atomic](https://go.microsoft.com/fwlink/?LinkId=190370) para obter informações sobre como configurar WsatConfig.exe.  
  
 Se você executar o exemplo no mesmo computador ou em computadores diferentes, você deve configurar o Microsoft Distributed Transaction coordenador (MSDTC) para habilitar o fluxo de transações de rede e usar a ferramenta de WsatConfig.exe para habilitar o suporte de rede de transações do WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Para configurar o Microsoft Distributed Transaction coordenador (MSDTC) para dar suporte à execução do exemplo  
  
1.  Em um computador de serviço que executam o Windows Server 2003 ou Windows XP, configure o MSDTC para permitir transações de rede de entrada seguindo estas instruções.  
  
    1.  Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.  
  
    2.  Expandir **serviços de componentes**. Abra o **computadores** pasta.  
  
    3.  Clique com botão direito **meu computador** e selecione **propriedades**.  
  
    4.  Sobre o **MSDTC** , clique em **configuração de segurança**.  
  
    5.  Verifique **acesso DTC de rede** e **permitir entrada**.  
  
    6.  Clique em **Okey**, em seguida, clique em **Sim** para reiniciar o serviço MSDTC.  
  
    7.  Clique em **OK** para fechar a caixa de diálogo.  
  
2.  Em um computador de serviço que executam o Windows Server 2008 ou Windows Vista, configure o MSDTC para permitir transações de rede de entrada seguindo estas instruções.  
  
    1.  Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.  
  
    2.  Expandir **serviços de componentes**. Abra o **computadores** pasta. Selecione **coordenador de transações distribuídas**.  
  
    3.  Clique com botão direito **DTC coordenador** e selecione **propriedades**.  
  
    4.  Sobre o **segurança** guia, seleção **acesso DTC de rede** e **permitir entrada**.  
  
    5.  Clique em **Okey**, em seguida, clique em **Sim** para reiniciar o serviço MSDTC.  
  
    6.  Clique em **OK** para fechar a caixa de diálogo.  
  
3.  O computador cliente, configure o MSDTC para permitir transações de rede de saída:  
  
    1.  Do **iniciar** menu, navegue até `Control Panel`, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.  
  
    2.  Clique com botão direito **meu computador** e selecione **propriedades**.  
  
    3.  Sobre o **MSDTC** , clique em **configuração de segurança**.  
  
    4.  Verifique **acesso DTC de rede** e **permitir saída**.  
  
    5.  Clique em **Okey**, em seguida, clique em **Sim** para reiniciar o serviço MSDTC.  
  
    6.  Clique em **OK** para fechar a caixa de diálogo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
