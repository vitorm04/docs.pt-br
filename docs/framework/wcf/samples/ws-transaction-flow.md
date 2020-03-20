---
title: Fluxo de transação WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 8b037a2faa6ed5f7c77ea9347b92af7dc1ec2c27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183165"
---
# <a name="ws-transaction-flow"></a>Fluxo de transação WS
Esta amostra demonstra o uso de uma transação coordenada pelo cliente e das opções de fluxo de transações e cliente e servidor usando o protocolo WS-Atomic Transaction ou OleTransactions. Esta amostra é baseada no Getting Started que [implementa](../../../../docs/framework/wcf/samples/getting-started-sample.md) um serviço de calculadora, `TransactionFlowAttribute` mas as operações são atribuídas para demonstrar o uso do com a enumeração **TransactionFlowOption** para determinar até que ponto o fluxo de transação está habilitado. No escopo da transação fluída, um registro das operações solicitadas é gravado em um banco de dados e persiste até que a transação coordenada pelo cliente seja concluída - se a transação do cliente não for concluída, a transação de serviço web garante que a transação de serviço web assegure que a transação de serviço web atualizações apropriadas para o banco de dados não são cometidas.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Após o início de uma conexão com o serviço e uma transação, o cliente acessa diversas operações de atendimento. O contrato para o serviço é definido da seguinte forma com `TransactionFlowOption`cada uma das operações demonstrando um cenário diferente para o .  

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

 Isso define as operações na ordem em que devem ser processadas:  
  
- Uma `Add` solicitação de operação deve incluir uma transação fluída.  
  
- Uma `Subtract` solicitação de operação pode incluir uma transação fluída.  
  
- Uma `Multiply` solicitação de operação não deve incluir uma transação fluída através da configuração não permitida explícita.  
  
- Uma `Divide` solicitação de operação não deve incluir uma `TransactionFlow` transação fluída através da omissão de um atributo.  
  
 Para habilitar o fluxo de transações, as vinculações com a [ \<transaçãoFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriedade habilitada devem ser usadas, além dos atributos de operação apropriados. Nesta amostra, a configuração do serviço expõe um ponto final TCP e um ponto final HTTP, além de um ponto final do Metadata Exchange. O ponto final do TCP e o ponto final HTTP usam as seguintes vinculações, ambas com a [ \<propriedade transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) habilitada.  
  
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
> O netTcpBinding fornecido pelo sistema permite a especificação do transactionProtocol, enquanto o wsHttpBinding fornecido pelo sistema usa apenas o protocolo WSAtomicTransactionOctoberOctober2004 mais interoperável. O protocolo OleTransactions só está disponível para uso por clientes da Windows Communication Foundation (WCF).  
  
 Para a classe que `ICalculator` implementa a interface, todos <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> os métodos são atribuídos com a propriedade definida como `true`. Esta configuração declara que todas as ações tomadas dentro do método ocorrem no âmbito de uma transação. Neste caso, as ações tomadas incluem o registro no banco de dados de log. Se a solicitação de operação incluir uma transação fluída, as ações ocorrerão no escopo da transação recebida ou um novo escopo de transação será gerado automaticamente.  
  
> [!NOTE]
> A <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade define o comportamento local para as implementações do método de serviço e não define a capacidade ou exigência do cliente para fluir uma transação.  

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

 No cliente, as configurações do `TransactionFlowOption` serviço sobre as operações são refletidas `ICalculator` na definição gerada pelo cliente da interface. Além disso, as `transactionFlow` configurações de propriedade do serviço são refletidas na configuração do aplicativo do cliente. O cliente pode selecionar o transporte e `endpointConfigurationName`o protocolo selecionando o apropriado .  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> O comportamento observado desta amostra é o mesmo, não importa qual protocolo ou transporte seja escolhido.  
  
 Tendo iniciado a conexão com o `TransactionScope` serviço, o cliente cria uma nova em torno das chamadas para as operações de atendimento.  

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

 As chamadas para as operações são as seguintes:  
  
- A `Add` solicitação flui a transação necessária para o serviço e as ações do serviço ocorrem no âmbito da transação do cliente.  
  
- A `Subtract` primeira solicitação também flui a transação permitida para o serviço e novamente as ações do serviço ocorrem no âmbito da transação do cliente.  
  
- A `Subtract` segunda solicitação é realizada dentro de `TransactionScopeOption.Suppress` um novo escopo de transação declarado com a opção. Isso suprime a transação externa inicial do cliente e a solicitação não flui uma transação para o serviço. Essa abordagem permite que um cliente opte explicitamente e proteja contra o fluxo de uma transação para um serviço quando isso não é necessário. As ações do serviço ocorrem no âmbito de uma transação nova e não conectada.  
  
- A `Multiply` solicitação não flui uma transação para o serviço `ICalculator` porque a <xref:System.ServiceModel.TransactionFlowAttribute> definição <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`gerada pelo cliente da interface inclui um conjunto para .  
  
- A `Divide` solicitação não flui uma transação para o serviço porque `ICalculator` novamente a `TransactionFlowAttribute`definição gerada pelo cliente da interface não inclui um . As ações do serviço voltam a ocorrer no âmbito de outra transação nova e não conectada.  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
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
  
 O registro das solicitações de operação do serviço é exibido na janela do console do serviço. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Após uma execução bem-sucedida, o escopo de transação do cliente é concluído e todas as ações tomadas dentro desse escopo são cometidas. Especificamente, os 5 registros anotados são persistidos no banco de dados do serviço. As duas primeiras delas ocorreram no âmbito da transação do cliente.  
  
 Se uma exceção ocorreu em `TransactionScope` qualquer lugar dentro do cliente, então a transação não poderá ser concluída. Isso faz com que os registros registrados nesse escopo não sejam comprometidos no banco de dados. Este efeito pode ser observado repetindo a amostra executada após comentar `TransactionScope`a chamada para completar o exterior . Nessa execução, apenas as 3 últimas `Subtract`ações `Multiply` (a partir da segunda , as e as `Divide` solicitações) são registradas porque a transação do cliente não fluiu para essas.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para construir a versão C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2. Certifique-se de que você instalou o SQL Server Express Edition ou o SQL Server e que a seqüência de conexões foi configurada corretamente no arquivo de configuração do aplicativo do serviço. Para executar a amostra sem `usingSql` usar um banco de dados, defina o valor no arquivo de configuração do aplicativo do serviço para`false`  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Para a configuração entre máquinas, habilite o Coordenador de Transações Distribuídas usando as instruções abaixo e use a ferramenta WsatConfig.exe do Windows SDK para permitir o suporte à rede de transações WCF. Para obter informações sobre a configuração do WsatConfig.exe, consulte [Configurando o suporte à transação WS-Atomic](../feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Se você executar a amostra no mesmo computador ou em computadores diferentes, você deve configurar o Microsoft Distributed Transaction Coordinator (MSDTC) para permitir o fluxo de transações de rede e usar a ferramenta WsatConfig.exe para habilitar o suporte à rede de transações WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Para configurar o Microsoft Distributed Transaction Coordinator (MSDTC) para suportar a execução da amostra  
  
1. Em uma máquina de serviço executando o Windows Server 2003 ou o Windows XP, configure o MSDTC para permitir transações de rede recebidas seguindo estas instruções.  
  
    1. Do menu **Iniciar,** navegue até o **Painel de Controle,** depois **Ferramentas Administrativas**e, em seguida, **Serviços de Componentes**.  
  
    2. Expandir **serviços de componentes**. Abra a pasta **Computadores.**  
  
    3. Clique com o botão direito do mouse **em Meu computador** e selecione **Propriedades**.  
  
    4. Na guia **MSDTC,** clique **em Configuração de segurança**.  
  
    5. Verifique **o acesso ao DTC da rede** e permita a **entrada**.  
  
    6. Clique **em OK**e clique em **Sim** para reiniciar o serviço MSDTC.  
  
    7. Clique em **OK** para fechar a caixa de diálogo.  
  
2. Em uma máquina de serviço executando o Windows Server 2008 ou o Windows Vista, configure o MSDTC para permitir transações de rede recebidas seguindo estas instruções.  
  
    1. Do menu **Iniciar,** navegue até o **Painel de Controle,** depois **Ferramentas Administrativas**e, em seguida, **Serviços de Componentes**.  
  
    2. Expandir **serviços de componentes**. Abra a pasta **Computadores.** Selecione **coordenador de transações distribuídas**.  
  
    3. Clique com o botão direito do mouse **no coordenador do DTC** e selecione **Propriedades**.  
  
    4. Na guia **Segurança,** verifique o **acesso dtc da rede** e permita a **entrada**.  
  
    5. Clique **em OK**e clique em **Sim** para reiniciar o serviço MSDTC.  
  
    6. Clique em **OK** para fechar a caixa de diálogo.  
  
3. Na máquina cliente, configure o MSDTC para permitir transações de rede de saída:  
  
    1. A partir do menu `Control Panel` **Iniciar,** navegue até, em seguida, Ferramentas **Administrativas**e, em seguida, **Serviços de Componentes**.  
  
    2. Clique com o botão direito do mouse **em Meu computador** e selecione **Propriedades**.  
  
    3. Na guia **MSDTC,** clique **em Configuração de segurança**.  
  
    4. Verifique **o acesso ao DTC da rede** e permita a **saída**.  
  
    5. Clique **em OK**e clique em **Sim** para reiniciar o serviço MSDTC.  
  
    6. Clique em **OK** para fechar a caixa de diálogo.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
