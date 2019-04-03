---
title: Comportamento de transação de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: dafc75c9db0dfe9b51c7425a269c166182bbcc87
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843026"
---
# <a name="service-transaction-behavior"></a>Comportamento de transação de serviço
Este exemplo demonstra o uso de uma transação de coordenadas de cliente e as configurações de ServiceBehaviorAttribute e OperationBehaviorAttribute para controlar o comportamento de transação de serviço. Este exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de Calculadora, mas é estendido para manter um log das operações realizadas em uma tabela de banco de dados e uma soma acumulada para as operações de calculadora com monitoração de estado do servidor. Gravações persistentes para a tabela de log do servidor são dependentes após o resultado de uma transação de coordenadas de cliente - se a transação do cliente não for concluída, a transação de serviço Web garante que as atualizações para o banco de dados não são confirmadas.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O contrato para o serviço define que todas as operações requerem uma transação para fluir com solicitações:  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 Para habilitar o fluxo de transações de entrada, o serviço está configurado com o wsHttpBinding fornecido pelo sistema com o atributo transactionFlow definido como `true`. Esta associação usa o protocolo WSAtomicTransactionOctober2004 interoperável:  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 Após iniciar ambos os uma conexão para o serviço e uma transação, o cliente acessa várias operações de serviço dentro do escopo da transação e, em seguida, conclui a transação e fecha a conexão:  
  
```csharp
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 No serviço, há três atributos que afetam o comportamento de transação de serviço e eles fazem isso das seguintes maneiras:  
  
-   Sobre o `ServiceBehaviorAttribute`:  
  
    -   O `TransactionTimeout` propriedade especifica o período de tempo dentro do qual uma transação deve ser concluída. Neste exemplo, ele é definido como 30 segundos.  
  
    -   O `TransactionIsolationLevel` propriedade especifica o nível de isolamento com suporte do serviço. Isso é necessário para corresponder ao nível de isolamento do cliente.  
  
    -   O `ReleaseServiceInstanceOnTransactionComplete` propriedade especifica se a instância do serviço é reciclada quando uma transação é concluída. Definindo-a para `false`, o serviço mantém a mesma instância de serviço entre as solicitações de operação. Isso é necessário para manter a execução total. Se definido como `true`, uma nova instância é gerada após a conclusão de cada ação.  
  
    -   O `TransactionAutoCompleteOnSessionClose` propriedade especifica se as transações pendentes são concluídas quando a sessão é fechada. Definindo-a para `false`, as operações individuais são necessárias para configurar o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> propriedade a ser `true` ou para solicitar explicitamente que uma chamada para o <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> método para concluir transações. Este exemplo demonstra as duas abordagens.  
  
-   Sobre o `ServiceContractAttribute`:  
  
    -   O `SessionMode` propriedade especifica se o serviço correlaciona as solicitações adequadas em uma sessão lógica. Porque esse serviço inclui operações em que a propriedade de OperationBehaviorAttribute TransactionAutoComplete é definida como `false` (multiplicar e dividir), `SessionMode.Required` deve ser especificado. Por exemplo, a multiplicar a operação não concluir sua transação e em vez disso, depende de uma chamada posterior a divisão para ser concluída usando o `SetTransactionComplete` método; o serviço deve ser capaz de determinar que essas operações estão ocorrendo na mesma sessão.  
  
-   Sobre o `OperationBehaviorAttribute`:  
  
    -   O `TransactionScopeRequired` propriedade especifica se as ações da operação devem ser executadas em um escopo de transação. Isso é definido como `true` para todas as operações nesse exemplo e, porque o cliente flui sua transação para todas as operações, ocorrem as ações dentro do escopo de transação do cliente.  
  
    -   O `TransactionAutoComplete` propriedade especifica se a transação na qual o método é executado é preenchida automaticamente se não ocorrer nenhuma exceção sem tratamento. Conforme descrito anteriormente, isso é definido como `true` para as operações de adicionar e subtrair, mas `false` para as operações de divisão e multiplicação. As operações de adicionar e subtrair concluir suas ações automaticamente, a divisão conclua suas ações por meio de uma chamada explícita para o `SetTransactionComplete` método e a multiplicação não concluir suas ações, mas em vez disso, baseia-se em e requer uma chamada posterior, como a Divida, para concluir as ações.  
  
 A implementação de serviço atribuída é da seguinte maneira:  
  
```csharp
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 O registro em log as solicitações de operação de serviço são exibidos na janela do console do serviço. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 Observe que, além de manter os em funcionamento total dos cálculos, o serviço reporta a criação de instâncias (uma instância para este exemplo) e registra as solicitações de operação em um banco de dados. Porque todas as solicitações de fluem de transação do cliente, qualquer falha ao concluir a transação resulta em todas as operações de banco de dados que estão sendo revertidas. Isso pode ser demonstrado de várias maneiras:  
  
-   Comente a chamada do cliente para `tx.Complete`() e execute novamente – isso resulta no cliente de sair do escopo da transação sem concluir sua transação.  
  
-   Comente a chamada para a operação de serviço de divisão de k-out - este resultados impedir a ação iniciada pela conclusão da operação de multiplicação e, portanto, a transação do cliente, por fim, também não for concluída.  
  
-   Lançar uma exceção sem tratamento em qualquer lugar no escopo de transação do cliente - isso da mesma forma impede que o cliente concluir sua transação.  
  
 O resultado de qualquer um desses é que nenhuma das operações executadas dentro do escopo são confirmadas e a contagem de linhas são mantidas no banco de dados não incrementam.  
  
> [!NOTE]
>  Como parte do processo de compilação, o arquivo de banco de dados é copiado para a pasta bin. Você deve examinar essa cópia do arquivo de banco de dados para observar as linhas que são mantidas no log, em vez do arquivo que está incluído no projeto do Visual Studio.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha instalado o SQL Server 2005 Express Edition ou SQL Server 2005. No arquivo de App. config do serviço, o banco de dados `connectionString` pode ser o conjunto ou o banco de dados interações podem ser desabilitadas definindo o appSettings `usingSql` valor `false`.  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Se você executar o exemplo entre máquinas, você deve configurar o Microsoft Distributed Transaction coordenador (MSDTC) para habilitar o fluxo de transações de rede e usar a ferramenta de WsatConfig.exe para habilitar transações de rede do Windows Communication Foundation (WCF) suporte.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a>Para configurar o Microsoft Distributed Transaction coordenador (MSDTC) para dar suporte à execução do exemplo entre máquinas  
  
1.  No computador do serviço, configure o MSDTC para permitir transações de rede de entrada.  
  
    1.  Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.  
  
    2.  Clique com botão direito **meu computador** e selecione **propriedades**.  
  
    3.  Sobre o **MSDTC** , clique em **configuração de segurança**.  
  
    4.  Verifique **acesso DTC de rede** e **permitir entrada**.  
  
    5.  Clique em **Yes** para reiniciar o serviço MS DTC e, em seguida, clique em **Okey**.  
  
    6.  Clique em **OK** para fechar a caixa de diálogo.  
  
2.  No computador do serviço e no computador cliente, configure o Firewall do Windows para incluir o Microsoft Distributed Transaction coordenador (MSDTC) à lista de aplicativos de exceção:  
  
    1.  Execute o aplicativo de Firewall do Windows no painel de controle.  
  
    2.  Dos **exceções** , clique em **adicionar programa**.  
  
    3.  Navegue até a pasta C:\WINDOWS\System32.  
  
    4.  Selecione Msdtc.exe e clique em **aberto**.  
  
    5.  Clique em **Okey** para fechar o **adicionar programa** caixa de diálogo e clique em **Okey** novamente para fechar o miniaplicativo de Firewall do Windows.  
  
3.  O computador cliente, configure o MSDTC para permitir transações de rede de saída:  
  
    1.  Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.  
  
    2.  Clique com botão direito **meu computador** e selecione **propriedades**.  
  
    3.  Sobre o **MSDTC** , clique em **configuração de segurança**.  
  
    4.  Verifique **acesso DTC de rede** e **permitir saída**.  
  
    5.  Clique em **Yes** para reiniciar o serviço MS DTC e, em seguida, clique em **Okey**.  
  
    6.  Clique em **OK** para fechar a caixa de diálogo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
