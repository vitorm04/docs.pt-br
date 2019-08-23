---
title: 'Como: criar um serviço transacional'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: be364e7638394a30c199b05dd15ef4c44e18e688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964012"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="39f7e-102">Como: criar um serviço transacional</span><span class="sxs-lookup"><span data-stu-id="39f7e-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="39f7e-103">Este exemplo demonstra vários aspectos da criação de um serviço transacional e o uso de uma transação iniciada pelo cliente para coordenar operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="39f7e-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="39f7e-104">Criando um serviço transacional</span><span class="sxs-lookup"><span data-stu-id="39f7e-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="39f7e-105">Crie um contrato de serviço e anote as operações com a configuração desejada da <xref:System.ServiceModel.TransactionFlowOption> enumeração para especificar os requisitos de transação de entrada.</span><span class="sxs-lookup"><span data-stu-id="39f7e-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="39f7e-106">Observe que você também pode inserir o <xref:System.ServiceModel.TransactionFlowAttribute> na classe de serviço que está sendo implementada.</span><span class="sxs-lookup"><span data-stu-id="39f7e-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="39f7e-107">Isso permite que uma única implementação de uma interface Use essas configurações de transação, em vez de cada implementação.</span><span class="sxs-lookup"><span data-stu-id="39f7e-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="39f7e-108">Crie uma classe de implementação e use o <xref:System.ServiceModel.ServiceBehaviorAttribute> para especificar opcionalmente um <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> e um <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="39f7e-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="39f7e-109">Você deve observar que, em muitos casos, o <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> padrão de 60 segundos e o <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> `Unspecified` padrão são apropriados.</span><span class="sxs-lookup"><span data-stu-id="39f7e-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="39f7e-110">Para cada operação, você pode usar o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo para especificar se o trabalho executado dentro do método deve ocorrer dentro do escopo de um escopo de transação de acordo com o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="39f7e-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="39f7e-111">Nesse caso, a transação usada para o `Add` método é a mesma que a transação de entrada obrigatória que está fluindo do cliente e a transação usada para o `Subtract` método é a mesma que a transação de entrada, caso um tenha sido transmitido do cliente ou uma nova transação criada implicitamente e localmente.</span><span class="sxs-lookup"><span data-stu-id="39f7e-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="39f7e-112">Configure as associações no arquivo de configuração, especificando que o contexto de transação deve ser fluído e os protocolos a serem usados para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="39f7e-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="39f7e-113">Para obter mais informações, consulte [configuração de transação de ServiceModel](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="39f7e-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="39f7e-114">Especificamente, o tipo de associação é especificado no atributo do elemento `binding` do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="39f7e-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="39f7e-115">`bindingConfiguration` O [ \<elemento Endpoint >](../../configure-apps/file-schema/wcf/endpoint-element.md) contém um atributo que faz referência a uma configuração `transactionalOleTransactionsTcpBinding`de associação denominada, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="39f7e-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="39f7e-116">O fluxo de transações é habilitado no nível de configuração usando `transactionFlow` o atributo, e o protocolo de transação é especificado `transactionProtocol` usando o atributo, conforme mostrado na configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="39f7e-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="39f7e-117">Oferecendo suporte a vários protocolos de transação</span><span class="sxs-lookup"><span data-stu-id="39f7e-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="39f7e-118">Para obter um desempenho ideal, você deve usar o protocolo OleTransactions para cenários que envolvem um cliente e um serviço gravados usando Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="39f7e-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="39f7e-119">No entanto, o protocolo WS-AtomicTransaction (WS-AT) é útil para cenários em que a interoperabilidade com pilhas de protocolos de terceiros é necessária.</span><span class="sxs-lookup"><span data-stu-id="39f7e-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="39f7e-120">Você pode configurar os serviços WCF para aceitar os dois protocolos fornecendo vários pontos de extremidade com associações específicas de protocolo apropriadas, conforme mostrado na configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="39f7e-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="39f7e-121">O protocolo de transação é especificado usando `transactionProtocol` o atributo.</span><span class="sxs-lookup"><span data-stu-id="39f7e-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="39f7e-122">No entanto, esse atributo está ausente do fornecido `wsHttpBinding`pelo sistema, pois essa associação só pode usar o protocolo WS-AT.</span><span class="sxs-lookup"><span data-stu-id="39f7e-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="39f7e-123">Controlando a conclusão de uma transação</span><span class="sxs-lookup"><span data-stu-id="39f7e-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="39f7e-124">Por padrão, as operações do WCF automaticamente concluem transações se nenhuma exceção sem tratamento for lançada.</span><span class="sxs-lookup"><span data-stu-id="39f7e-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="39f7e-125">Você pode modificar esse comportamento usando a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Propriedade e o <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> método.</span><span class="sxs-lookup"><span data-stu-id="39f7e-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="39f7e-126">Quando uma operação é necessária para ocorrer na mesma transação que outra operação (por exemplo, uma operação de débito e crédito), você pode desabilitar o comportamento de preenchimento automático definindo a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `false` Propriedade como, conforme mostrado no seguinte `Debit` exemplo de operação.</span><span class="sxs-lookup"><span data-stu-id="39f7e-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="39f7e-127">A transação usada `Debit` pela operação não é concluída até que um método com <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> a propriedade definida `true` seja chamado, como mostrado na operação `Credit1`, ou quando o <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> método é chamado para marcar explicitamente o transação como concluída, conforme mostrado na operação `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="39f7e-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="39f7e-128">Observe que as duas operações de crédito são mostradas para fins de ilustração e que uma única operação de crédito seria mais típica.</span><span class="sxs-lookup"><span data-stu-id="39f7e-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="39f7e-129">Para fins de correlação de transações, definir a <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Propriedade como `false` requer o uso de uma associação de sessão.</span><span class="sxs-lookup"><span data-stu-id="39f7e-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="39f7e-130">Esse requisito é especificado com a `SessionMode` propriedade <xref:System.ServiceModel.ServiceContractAttribute>no.</span><span class="sxs-lookup"><span data-stu-id="39f7e-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="39f7e-131">Controlando o tempo de vida de uma instância de serviço transacional</span><span class="sxs-lookup"><span data-stu-id="39f7e-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="39f7e-132">O WCF usa <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> a propriedade para especificar se a instância de serviço subjacente é liberada quando uma transação é concluída.</span><span class="sxs-lookup"><span data-stu-id="39f7e-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="39f7e-133">Como esse padrão é `true`, a menos que configurado de outra forma, o WCF exibe um comportamento de ativação "Just-in-time" eficiente e previsível.</span><span class="sxs-lookup"><span data-stu-id="39f7e-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="39f7e-134">As chamadas para um serviço em uma transação subsequente são garantidas como uma nova instância de serviço sem vestígios do estado da transação anterior.</span><span class="sxs-lookup"><span data-stu-id="39f7e-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="39f7e-135">Embora isso seja geralmente útil, às vezes você pode desejar manter o estado dentro da instância do serviço além da conclusão da transação.</span><span class="sxs-lookup"><span data-stu-id="39f7e-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="39f7e-136">Exemplos disso seriam quando o estado ou os identificadores necessários para os recursos forem caros de recuperar ou reconstituir.</span><span class="sxs-lookup"><span data-stu-id="39f7e-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="39f7e-137">Você pode fazer isso definindo a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> Propriedade como. `false`</span><span class="sxs-lookup"><span data-stu-id="39f7e-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="39f7e-138">Com essa configuração, a instância e qualquer estado associado estarão disponíveis em chamadas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="39f7e-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="39f7e-139">Ao usar isso, dê uma consideração cuidadosa sobre quando e como o estado e as transações serão limpos e concluídos.</span><span class="sxs-lookup"><span data-stu-id="39f7e-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="39f7e-140">O exemplo a seguir demonstra como fazer isso mantendo a instância com a `runningTotal` variável.</span><span class="sxs-lookup"><span data-stu-id="39f7e-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    > <span data-ttu-id="39f7e-141">Como o tempo de vida da instância é um comportamento que é interno ao serviço e controlado por <xref:System.ServiceModel.ServiceBehaviorAttribute> meio da propriedade, nenhuma modificação na configuração do serviço ou no contrato de serviço é necessária para definir o comportamento da instância.</span><span class="sxs-lookup"><span data-stu-id="39f7e-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="39f7e-142">Além disso, a transmissão não conterá nenhuma representação.</span><span class="sxs-lookup"><span data-stu-id="39f7e-142">In addition, the wire will contain no representation of this.</span></span>
