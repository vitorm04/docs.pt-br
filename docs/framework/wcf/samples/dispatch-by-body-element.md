---
title: Expedição por elemento Body
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183718"
---
# <a name="dispatch-by-body-element"></a>Expedição por elemento Body
Esta amostra demonstra como implementar um algoritmo alternativo para atribuir mensagens recebidas às operações.  
  
 Por padrão, o despachante do modelo de serviço seleciona o método de manuseio apropriado para uma mensagem recebida com base no cabeçalho "Action" da mensagem ou nas informações equivalentes na solicitação HTTP SOAP.  
  
 Algumas pilhas de serviços DA SOAP 1.1 que não seguem as diretrizes do Perfil Básico WS-I 1.1 não despacham mensagens baseadas no URI de ação, mas sim com base no nome qualificado XML do primeiro elemento dentro do corpo SOAP. Da mesma forma, o lado cliente dessas pilhas pode enviar mensagens com um cabeçalho HTTP SoapAction vazio ou arbitrário, o que foi permitido pela especificação SOAP 1.1.  
  
 Para alterar a forma como as mensagens são enviadas <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> para métodos, `DispatchByBodyElementOperationSelector`a amostra implementa a interface de extensibilidade no . Esta classe seleciona operações com base no primeiro elemento do corpo da mensagem.  
  
 O construtor de classe espera um dicionário `XmlQualifiedName` preenchido com pares de e cordas, pelo qual os nomes qualificados indicam o nome do primeiro filho do corpo SOAP e as cordas indicam o nome da operação correspondente. O `defaultOperationName` é o nome da operação que recebe todas as mensagens que não podem ser comparadas com este dicionário:  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementações são muito simples de construir, pois há <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>apenas um método na interface: . O trabalho deste método é inspecionar uma mensagem recebida e devolver uma seqüência que seja igual ao nome de um método no contrato de serviço para o ponto final atual.  
  
 Nesta amostra, o seletor <xref:System.Xml.XmlDictionaryReader> de operação adquire um <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>para o corpo da mensagem recebida usando . Este método já posiciona o leitor sobre o primeiro filho do corpo da mensagem de modo que seja suficiente `XmlQualifiedName` para obter o nome do elemento atual e o espaço de nome URI e combiná-lo em um que é então usado para procurar a operação correspondente do dicionário mantido pelo seletor de operação.  
  
```csharp
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
  
 Acessar o corpo <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> da mensagem com ou qualquer outro método que forneça acesso ao conteúdo do corpo da mensagem faz com que a mensagem seja marcada como "leitura", o que significa que a mensagem é inválida para qualquer processamento adicional. Portanto, o seletor de operação cria uma cópia da mensagem recebida com o método mostrado no código a seguir. Como a posição do leitor não foi alterada durante a inspeção, ela pode ser referenciada pela mensagem recém-criada à qual as propriedades da mensagem e os cabeçalhos de mensagem também são copiados, o que resulta em um clone exato da mensagem original:  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Adicionando um Seletor de Operação a um Serviço  
 Os seletores de operação de despacho de serviço são extensões para o despachante da Windows Communication Foundation (WCF). Para selecionar métodos no canal de retorno de contratos duplex, há também seletores de operação do cliente, que funcionam muito parecidos com os seletores de operação de despacho descritos aqui, mas que não estão explicitamente cobertos nesta amostra.  
  
 Como a maioria das extensões do modelo de serviço, os seletores de operação de despacho são adicionados ao despachante usando comportamentos. Um *comportamento* é um objeto de configuração, que adiciona uma ou mais extensões ao tempo de execução do despacho (ou ao tempo de execução do cliente) ou altera suas configurações.  
  
 Como os seletores de operação têm escopo de <xref:System.ServiceModel.Description.IContractBehavior>contrato, o comportamento apropriado para implementar aqui é o . Como a interface é <xref:System.Attribute> implementada em uma classe derivada, como mostrado no código a seguir, o comportamento pode ser declarativamente adicionado a qualquer contrato de serviço. Sempre <xref:System.ServiceModel.ServiceHost> que um é aberto e o tempo de execução de despacho é construído, todos os comportamentos encontrados como atributos em contratos, operações e implementações de serviço ou como elemento na configuração do serviço são automaticamente adicionados e posteriormente solicitados a contribuir com extensões ou modificar a configuração padrão.  
  
 Para a brevidade, o trecho de código <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>a seguir mostra apenas a implementação do método , o que afeta as alterações de configuração para o despachante nesta amostra. Os outros métodos não são mostrados porque retornam ao chamador sem fazer qualquer trabalho.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Primeiro, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> a implementação configura o dicionário de busca para o <xref:System.ServiceModel.Description.OperationDescription> seletor de <xref:System.ServiceModel.Description.ContractDescription>operação, iterando sobre os elementos no ponto final do serviço . Em seguida, cada descrição da `DispatchBodyElementAttribute` <xref:System.ServiceModel.Description.IOperationBehavior> operação é inspecionada para a presença do comportamento, uma implementação que também é definida nesta amostra. Embora essa classe também seja um comportamento, ela é passiva e não contribui ativamente com nenhuma alteração de configuração no tempo de execução do despacho. Todos os seus métodos retornam ao chamador sem tomar nenhuma ação. O comportamento de operação só existe para que os metadados necessários para o novo mecanismo de expedição, ou seja, o nome qualificado do elemento do corpo em cuja ocorrência uma operação é selecionada, possam ser associados às respectivas operações.  
  
 Se tal comportamento for encontrado, um par de valores`QName` criado a partir`Name` do nome qualificado XML (propriedade) e o nome da operação (propriedade) será adicionado ao dicionário.  
  
 Uma vez preenchido o dicionário, um novo `DispatchByBodyElementOperationSelector` é construído com essas informações e definido como o seletor de operação do tempo de execução do despacho:  
  
```csharp
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
  
## <a name="implementing-the-service"></a>Implementação do Serviço  
 O comportamento implementado nesta amostra afeta diretamente a forma como as mensagens do fio são interpretadas e despachadas, o que é uma função do contrato de serviço. Consequentemente, o comportamento deve ser declarado no nível do contrato de serviço em qualquer implementação de serviço que optar por usá-lo.  
  
 O serviço de projeto `DispatchByBodyElementBehaviorAttribute` amostral `IDispatchedByBody` aplica o comportamento contratual ao `OperationForBodyA()` contrato `OperationForBodyB()` de `DispatchBodyElementAttribute` serviço e rotula cada uma das duas operações e com um comportamento operacional. Quando um host de serviço para um serviço que implementa este contrato é aberto, esses metadados são captados pelo construtor de spaceiros como descrito anteriormente.  
  
 Como o seletor de operação despacha exclusivamente com base no elemento do corpo da mensagem e ignora a "Ação", é necessário dizer ao `ReplyAction` tempo <xref:System.ServiceModel.OperationContractAttribute>de execução para não verificar o cabeçalho "Ação" nas respostas devolvidas atribuindo o curinga "*" à propriedade de . Além disso, é necessário ter uma operação padrão que tenha a propriedade\*"Action" definida como curinga " ". A operação padrão recebe todas as mensagens que `DispatchBodyElementAttribute`não podem ser despachadas e não têm:  
  
```csharp
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
  
 A implementação do serviço de amostra é simples. Cada método envolve a mensagem recebida em uma mensagem de resposta e a ecoa de volta para o cliente.  
  
## <a name="running-and-building-the-sample"></a>Executando e construindo a amostra  
 Quando você executa a amostra, o conteúdo do corpo das respostas de operação é exibido na janela do console cliente semelhante à seguinte saída (formatada).  
  
 O cliente envia três mensagens para o `bodyA`serviço `bodyB`cujo `bodyX`elemento de conteúdo corporal é nomeado , e , respectivamente. Como pode ser diferido a partir da descrição anterior e `bodyA` do contrato de `OperationForBodyA()` serviço mostrado, a mensagem recebida com o elemento é enviada para o método. Como não há um alvo de `bodyX` despacho explícito para a mensagem `DefaultOperation()`com o elemento do corpo, a mensagem é enviada para o . Cada uma das operações de serviço envolve o corpo de mensagem recebida em um elemento específico do método e o devolve, o que é feito para correlacionar mensagens de entrada e saída claramente para esta amostra:  
  
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
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
