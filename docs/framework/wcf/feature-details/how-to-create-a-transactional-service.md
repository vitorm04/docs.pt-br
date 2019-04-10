---
title: 'Como: criar um serviço transacional'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 7f7f060db5a4ffd66524e220e3e3291debd8a3fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329486"
---
# <a name="how-to-create-a-transactional-service"></a>Como: criar um serviço transacional
Este exemplo demonstra vários aspectos da criação de um serviço transacional e o uso de uma transação iniciada pelo cliente para coordenar operações de serviço.  
  
### <a name="creating-a-transactional-service"></a>Criando um serviço transacional  
  
1. Criar um contrato de serviço e anotar as operações com a configuração desejada do <xref:System.ServiceModel.TransactionFlowOption> enumeração para especificar os requisitos de transação de entrada. Observe que você também pode colocar o <xref:System.ServiceModel.TransactionFlowAttribute> na classe de serviço que está sendo implementado. Isso permite uma única implementação de uma interface para usar essas configurações de transação, em vez de todas as implementações.  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. Criar uma classe de implementação e usar o <xref:System.ServiceModel.ServiceBehaviorAttribute> especificar opcionalmente um <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> e um <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Você deve observar que em muitos casos, o padrão <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> de 60 segundos e o padrão <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> de `Unspecified` são apropriadas. Para cada operação, você pode usar o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo para especificar se o trabalho realizado dentro do método deve ocorrer dentro do escopo de acordo com o valor de um escopo de transação a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atributo. Nesse caso, a transação usada para o `Add` método é o mesmo que a transação de entrada obrigatória que flui do cliente e a transação usada para o `Subtract` método é o mesmo que a transação de entrada se uma foi colocada em fluxo no cliente, ou uma nova transação criada localmente e implicitamente.  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. Configure as ligações no arquivo de configuração, especificando que o contexto de transação deve ser colocada em fluxo e os protocolos a serem usados para fazer isso. Para obter mais informações, consulte [configuração de transação de ServiceModel](servicemodel-transaction-configuration.md). Especificamente, o tipo de associação é especificado no elemento de ponto de extremidade `binding` atributo. O [ \<ponto de extremidade >](../../configure-apps/file-schema/wcf/endpoint-element.md) elemento contém um `bindingConfiguration` atributo que faz referência a uma configuração de ligação nomeada `transactionalOleTransactionsTcpBinding`, conforme mostrado no seguinte exemplo de configuração.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Fluxo de transações é habilitado no nível de configuração usando o `transactionFlow` atributo e o protocolo de transação é especificado usando o `transactionProtocol` de atributo, conforme mostrado na seguinte configuração.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Suporte a vários protocolos de transação  
  
1. Para otimizar o desempenho, você deve usar o protocolo de OleTransactions para cenários que envolvem um cliente e serviço escritos usando o Windows Communication Foundation (WCF). No entanto, o protocolo WS-AtomicTransaction (WS-AT) é útil para cenários quando a interoperabilidade com pilhas de protocolo de terceiros é necessária. Você pode configurar os serviços WCF para aceitar os dois protocolos, fornecendo vários pontos de extremidade com associações específicas de protocolo apropriadas, conforme mostrado no seguinte exemplo de configuração.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     O protocolo de transação é especificado usando o `transactionProtocol` atributo. No entanto, esse atributo estiver ausente do sistema forneceu `wsHttpBinding`, porque essa associação só pode usar o protocolo WS-AT.  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a>Controlando a conclusão de uma transação  
  
1. Por padrão, as operações do WCF concluir transações automaticamente se nenhuma exceção sem tratamento é geradas. Você pode modificar esse comportamento usando o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade e o <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> método. Quando uma operação é necessária para ocorrer dentro da mesma transação como outra operação (por exemplo, uma operação de débito e crédito), você pode desabilitar o comportamento de preenchimento automático definindo a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade para `false` conforme mostrado na seguinte `Debit` exemplo de operação. A transação a `Debit` usos de operação não será concluída até que um método com o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade definida como `true` é chamado, conforme mostrado na operação `Credit1`, ou quando o <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> método é chamado para marcar explicitamente o transação completa, como mostrado na operação `Credit2`. Observe que as operações de duas crédito são mostradas para fins de ilustração, e que uma única operação de crédito seria mais comum.  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. Para fins de correlação de transações, definindo o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade `false` requer o uso de uma associação de sessão. Esse requisito é especificado com o `SessionMode` propriedade no <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Controlando o tempo de vida de uma instância de serviço transacional  
  
1. O WCF usa o <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> propriedade para especificar se a instância do serviço subjacente é liberada quando uma transação é concluída. Uma vez que o padrão será `true`, a menos que configurado de outra forma, comportamento de ativação do WCF exibe um eficiente e previsível "just-in-time". Chamadas para um serviço em uma transação subsequente terá certeza de uma nova instância de serviço com nenhum resíduos de estado da transação anterior. Embora isso geralmente é útil, às vezes, convém manter o estado na instância do serviço além da conclusão da transação. Exemplos disso seria quando estado obrigatório ou identificadores de recursos são caras para recuperar ou reconstituir. Você pode fazer isso definindo a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> propriedade para `false`. Com essa configuração, a instância e qualquer estado associado estará disponíveis em chamadas subsequentes. Ao usar isso, dê atenta consideração aos quando e como transações e o estado serão limpo e concluídas. O exemplo a seguir demonstra como fazer isso, mantendo a instância com o `runningTotal` variável.  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Uma vez que o tempo de vida de instância é um comportamento que é interno ao serviço e controlado por meio de <xref:System.ServiceModel.ServiceBehaviorAttribute> propriedade, nenhuma modificação para a configuração de serviço ou contrato de serviço é obrigatório para definir o comportamento de instância. Além disso, durante a transmissão não conterá nenhuma representação disso.
