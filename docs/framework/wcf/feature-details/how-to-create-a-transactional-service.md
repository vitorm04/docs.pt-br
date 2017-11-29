---
title: "Como criar um serviço transacional"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7ef8d4778b21d33501e3f3d4478b722bf1e1cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-transactional-service"></a>Como criar um serviço transacional
Este exemplo demonstra vários aspectos da criação de um serviço transacional e o uso de uma transação iniciada pelo cliente para coordenar operações de serviço.  
  
### <a name="creating-a-transactional-service"></a>Criando um serviço transacional  
  
1.  Criar um contrato de serviço e anotar as operações com a configuração desejada do <xref:System.ServiceModel.TransactionFlowOption> enumeração para especificar os requisitos de transação de entrada. Observe que você também pode colocar o <xref:System.ServiceModel.TransactionFlowAttribute> na classe de serviço que está sendo implementada. Isso permite que uma única implementação de uma interface para usar essas configurações de transação, em vez de cada implementação.  
  
    ```  
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
  
2.  Criar uma classe de implementação e use o <xref:System.ServiceModel.ServiceBehaviorAttribute> especificar opcionalmente um <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> e um <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Você deve observar que, em muitos casos, o padrão <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> de 60 segundos e o padrão <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> de `Unspecified` apropriados. Para cada operação, você pode usar o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo para especificar se o trabalho executado dentro do método deve ocorrer dentro do escopo de acordo com o valor de um escopo de transação de <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atributo. Nesse caso, a transação é usada para o `Add` método é o mesmo que a transação de entrada obrigatória que flui do cliente e a transação usada para o `Subtract` método é o mesmo que a transação de entrada, se um fluiu do cliente, ou uma nova transação criada implicitamente e localmente.  
  
    ```  
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n1, n2));  
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n2, n1));  
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
  
3.  Configure as ligações no arquivo de configuração, especificando que o contexto da transação deve fluir e os protocolos a ser usado para fazer isso. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Configuração de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md). Especificamente, o tipo de associação é especificado no elemento de ponto de extremidade `binding` atributo. O [ \<ponto de extremidade >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento contém um `bindingConfiguration` atributo que faz referência a uma configuração de associação denominada `transactionalOleTransactionsTcpBinding`, conforme mostrado no exemplo de configuração.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Fluxo de transações está habilitado no nível de configuração usando o `transactionFlow` atributo e o protocolo de transação é especificado usando o `transactionProtocol` de atributo, conforme mostrado na configuração a seguir.  
  
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
  
1.  Para otimizar o desempenho, você deve usar o protocolo OleTransactions para cenários que envolvem um cliente e o serviço escritos usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. No entanto, o protocolo WS-AtomicTransaction (WS-AT) é útil para cenários quando a interoperabilidade com pilhas de protocolo de terceiros é necessária. Você pode configurar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços para aceitar os dois protocolos, fornecendo vários pontos de extremidade com associações de protocolo específico apropriadas, conforme mostrado no exemplo de configuração.  
  
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
  
     O protocolo de transação é especificado usando o `transactionProtocol` atributo. No entanto, esse atributo está ausente do fornecida pelo sistema `wsHttpBinding`, porque essa associação pode usar apenas o protocolo WS-AT.  
  
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
  
1.  Por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operações concluídas automaticamente transações se nenhuma exceção sem tratamento é geradas. Você pode modificar esse comportamento usando o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade e o <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> método. Quando uma operação deve ocorrer na mesma transação como outra operação (por exemplo, uma operação de crédito e débito), você pode desabilitar o comportamento de preenchimento automático definindo a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade `false` conforme mostrado no seguinte `Debit` exemplo de operação. A transação de `Debit` operação não será concluída até que um método com o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade definida como `true` é chamado, conforme mostrado na operação de `Credit1`, ou quando o <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> método é chamado para marcar explicitamente o transação completa, como mostrado na operação `Credit2`. Observe que as operações de dois crédito são mostradas para fins de ilustração, e que uma única operação de crédito seria mais comum.  
  
    ```  
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
  
2.  Para fins de correlação de transações, definindo o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> propriedade `false` requer o uso de uma associação de sessão. Esse requisito é especificado com o `SessionMode` propriedade o <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```  
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
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> propriedade para especificar se a instância de serviço subjacente é lançada quando uma transação é concluída. Desde que o padrão é `true`, a menos que configurado de outra forma, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exibe um comportamento de ativação de "just-in-time" eficiente e previsível. Chamadas para um serviço em uma transação subsequente terá certeza de uma nova instância de serviço com nenhuma resíduos do estado da transação anterior. Enquanto isso geralmente é útil, às vezes, convém manter o estado dentro da instância de serviço além da conclusão da transação. Exemplos disso seria quando o estado exigido ou os recursos são caros recuperar ou reconstituir. Você pode fazer isso definindo o <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> propriedade `false`. Com essa configuração, a instância e qualquer estado associado estará disponíveis em chamadas subsequentes. Ao usar esta, dê atenção para quando e como estado e as transações serão limpos e concluídas. O exemplo a seguir demonstra como fazer isso, mantendo a instância com o `runningTotal` variável.  
  
    ```  
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n, runningTotal));  
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n, runningTotal));  
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
    >  Como o tempo de vida da instância é um comportamento interno para o serviço e controlado por meio de <xref:System.ServiceModel.ServiceBehaviorAttribute> propriedade, nenhuma modificação para a configuração de serviço ou o contrato de serviço é necessária para definir o comportamento da instância. Além disso, a transmissão não conterá nenhuma representação disso.
