---
title: "Expedição por elemento Body"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ab8ddccafa8dbf1ecde8afbb07f0a61faa62be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dispatch-by-body-element"></a>Expedição por elemento Body
Este exemplo demonstra como implementar um algoritmo alternativo para a atribuição de mensagens de entrada para as operações.  
  
 Por padrão, o dispatcher do modelo de serviço seleciona o método de manipulação de apropriado para uma mensagem de entrada com base no WS-Addressing da mensagem "Ação" informação de cabeçalho ou a equivalente na solicitação HTTP SOAP.  
  
 Alguns Web SOAP 1.1 serviços pilhas que não seguem o WS-I Basic Profile 1.1 diretrizes não enviar mensagens com base no URI de ação, mas em vez disso, com base no nome qualificado XML do primeiro elemento dentro do corpo SOAP. Da mesma forma, o lado do cliente dessas pilhas pode enviar mensagens com um cabeçalho de HTTP SoapAction arbitrário ou vazio, que era permitido pela especificação do SOAP 1.1.  
  
 Para alterar a maneira como as mensagens são enviadas para métodos, o exemplo implementa o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface extensibilidade a `DispatchByBodyElementOperationSelector`. Essa classe seleciona operações de acordo com o primeiro elemento do corpo da mensagem.  
  
 O construtor da classe espera um dicionário preenchido com pares de `XmlQualifiedName` e cadeias de caracteres, na qual os nomes qualificados indicam o nome do primeiro filho do corpo SOAP e as cadeias de caracteres indicam o nome da operação correspondente. O `defaultOperationName` é o nome da operação que recebe todas as mensagens que não podem ser comparadas com este dicionário:  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementações são muito simples de compilação porque há apenas um método na interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. O trabalho deste método é para inspecionar uma mensagem de entrada e retornar uma cadeia de caracteres que é igual ao nome de um método no contrato de serviço para o ponto de extremidade atual.  
  
 Neste exemplo, o seletor de operação adquire um <xref:System.Xml.XmlDictionaryReader> para a mensagem de entrada do corpo usando <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Este método já posiciona o leitor no primeiro filho do corpo da mensagem, para que seja suficiente para obter o nome do elemento atual e o URI de namespace e combiná-los em um `XmlQualifiedName` que é usado para pesquisar a operação correspondente a dicionário mantido pelo seletor de operação.  
  
```  
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 Acessando o corpo da mensagem com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ou qualquer um dos outros métodos que fornecem acesso ao conteúdo do corpo da mensagem faz com que a mensagem a ser marcado como "leitura", que significa que a mensagem é inválida para processamento. Portanto, o seletor de operação cria uma cópia da mensagem de entrada com o método mostrado no código a seguir. Porque a posição do leitor não foi alterada durante a inspeção, ele pode ser referenciado pela mensagem recém-criado para o qual as propriedades de mensagem e os cabeçalhos de mensagem também são copiados, que resulta em um clone exato da mensagem original:  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Adicionando um seletor de operação para um serviço  
 Seletores de operação de expedição de serviço são extensões para o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispatcher. Para selecionar os métodos no canal de retorno de chamada de contratos duplex, também há seletores de operação de cliente, que funcionam muito bem como os seletores de operação de expedição descritos aqui, mas que não é abordado neste exemplo explicitamente.  
  
 Como a maioria das extensões do modelo de serviço, expedição seletores são adicionados para o distribuidor usando comportamentos de operação. Um *comportamento* é um objeto de configuração, que adiciona uma ou mais extensões para o tempo de execução de despacho (ou no tempo de execução do cliente) ou se transforma suas configurações.  
  
 Como os seletores de operação têm escopo de contrato, o comportamento apropriado para implementar aqui é o <xref:System.ServiceModel.Description.IContractBehavior>. Porque a interface é implementada em um <xref:System.Attribute> classe derivada conforme mostrado no código a seguir, o comportamento pode ser adicionado declarativamente a qualquer contrato de serviço. Sempre que um <xref:System.ServiceModel.ServiceHost> é aberto e o tempo de execução de despacho é criado, todos os comportamentos encontrado como atributos em contratos, operações e implementações de serviço ou como um elemento na configuração de serviço são adicionados automaticamente e subsequentemente solicitado contribuir extensões ou modifique a configuração padrão.  
  
 Para resumir, o trecho de código a seguir mostra apenas a implementação do método <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, que afeta as alterações de configuração para o dispatcher neste exemplo. Os outros métodos não são mostrados porque elas retornam ao chamador sem fazer qualquer trabalho.  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Primeiro, o <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementação define o dicionário de pesquisa para o seletor de operação pela iteração no <xref:System.ServiceModel.Description.OperationDescription> elementos na extremidade do serviço <xref:System.ServiceModel.Description.ContractDescription>. Em seguida, a descrição de cada operação é inspecionada a presença do `DispatchBodyElementAttribute` comportamento, uma implementação de <xref:System.ServiceModel.Description.IOperationBehavior> que também está definido neste exemplo. Embora essa classe também é um comportamento, é passivo e não contribuem ativamente alterações de configuração para o tempo de execução de expedição. Todos os seus métodos de retornam ao chamador sem realizar nenhuma ação. O comportamento de operação só existe para que os metadados necessários para o novo expedição mecanismo, ou seja, o nome qualificado do elemento body em cuja ocorrência de uma operação for selecionada, podem ser associados com as operações do respectivas.  
  
 Se tal comportamento de um for encontrado, um par de valor criado a partir o nome qualificado XML (`QName` propriedade) e o nome da operação (`Name` propriedade) é adicionada ao dicionário.  
  
 Depois que o dicionário for preenchido, um novo `DispatchByBodyElementOperationSelector` é construído com essas informações e definido como o seletor de operação de tempo de execução de despacho:  
  
```  
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a>Implementando o serviço  
 O comportamento implementado neste exemplo diretamente afeta como mensagens de transmissão são interpretadas e distribuídas, que é uma função do contrato de serviço. Consequentemente, o comportamento deve ser declarado no nível de contrato de serviço em qualquer implementação de serviço que desejar usá-lo.  
  
 O serviço de projeto de exemplo se aplica a `DispatchByBodyElementBehaviorAttribute` contrato comportamento para o `IDispatchedByBody` contrato e rótulos as duas operações de serviço `OperationForBodyA()` e `OperationForBodyB()` com um `DispatchBodyElementAttribute` comportamento da operação. Quando um host de serviço para um serviço que implementa este contrato é aberto, esses metadados é captados pelo construtor de dispatcher conforme descrito anteriormente.  
  
 Como o seletor de operação despacha exclusivamente com base no elemento de corpo de mensagem e ignora a "ação", é necessário informar o tempo de execução para não verificar o cabeçalho "Ação" nas respostas retornadas atribuindo o caractere curinga "*" para o `ReplyAction` propriedade <xref:System.ServiceModel.OperationContractAttribute>. Além disso, é necessário ter uma operação de padrão que tem a propriedade "Ação" definida como o caractere curinga "\*". A operação padrão recebe todas as mensagens que não podem ser distribuídas e não tem um `DispatchBodyElementAttribute`:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 A implementação do serviço de exemplo é simples. Cada método envolve a mensagem recebida em uma mensagem de resposta e exibe-lo de volta ao cliente.  
  
## <a name="running-and-building-the-sample"></a>Executando e compilar o exemplo  
 Quando você executar o exemplo, o conteúdo do corpo das respostas de operação são exibidos na janela do console do cliente semelhante à seguinte saída (formatada).  
  
 O cliente envia três mensagens para o serviço cujo conteúdo de elemento é chamado de corpo `bodyA`, `bodyB`, e `bodyX`, respectivamente. Como podem ser adiadas a descrição anterior e o contrato de serviço mostrado, a mensagem de entrada com o `bodyA` elemento é enviado para o `OperationForBodyA()` método. Porque não há nenhum destino de expedição explícita para a mensagem com o `bodyX` elemento body, a mensagem é enviada para o `DefaultOperation()`. Cada uma das operações de serviço encapsula o corpo da mensagem recebida em um elemento específico para o método e retorna, que é feito para correlacionar a entrada e saída mensagens claramente para este exemplo:  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>Consulte também
