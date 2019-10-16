---
title: Visão geral de criação de ponto de extremidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: bf6bfb10123223bf689945ef93ff09219a68092c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319921"
---
# <a name="endpoint-creation-overview"></a>Visão geral de criação de ponto de extremidade

Toda a comunicação com um serviço Windows Communication Foundation (WCF) ocorre por meio dos *pontos de extremidade* do serviço. Os pontos de extremidade fornecem aos clientes acesso à funcionalidade oferecida por um serviço WCF. Esta seção descreve a estrutura de um ponto de extremidade e destaca como definir um ponto de extremidade na configuração e no código.

## <a name="the-structure-of-an-endpoint"></a>A estrutura de um ponto de extremidade

Cada ponto de extremidade contém um endereço que indica onde encontrar o ponto de extremidade, uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade e um contrato que identifica os métodos disponíveis.

- **Endereço**. O endereço identifica exclusivamente o ponto de extremidade e informa aos possíveis consumidores onde o serviço está localizado. Ele é representado no modelo de objeto do WCF pelo endereço <xref:System.ServiceModel.EndpointAddress>, que contém um URI (Uniform Resource Identifier) e propriedades de endereço que incluem uma identidade, alguns elementos WSDL (linguagem de descrição de serviços Web) e uma coleção de cabeçalhos opcionais. Os cabeçalhos opcionais fornecem informações adicionais de endereçamento detalhadas para identificar ou interagir com o ponto de extremidade. Para obter mais informações, consulte [especificando um endereço de ponto de extremidade](specifying-an-endpoint-address.md).

- **Associação**. A associação especifica como se comunicar com o ponto de extremidade. A associação especifica como o ponto de extremidade se comunica com o mundo, incluindo qual protocolo de transporte deve ser usado (por exemplo, TCP ou HTTP), que codificação usar para as mensagens (por exemplo, texto ou binário) e quais requisitos de segurança são necessários (para exemplo, protocolo SSL [SSL] ou segurança de mensagem SOAP). Para obter mais informações, consulte [usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md).

- **Contrato de serviço**. O contrato de serviço descreve qual funcionalidade o ponto de extremidade expõe para o cliente. Um contrato especifica as operações que um cliente pode chamar, a forma da mensagem e o tipo de parâmetros de entrada ou dados necessários para chamar a operação e o tipo de mensagem de processamento ou resposta que o cliente pode esperar. Três tipos básicos de contratos correspondem aos padrões de troca de mensagens básicos (MEPs): datagrama (unidirecional), solicitação/resposta e duplex (bidirecional). O contrato de serviço também pode empregar dados e contratos de mensagem para exigir tipos de dados e formatos de mensagem específicos ao serem acessados. Para obter mais informações sobre como definir um contrato de serviço, consulte [projetando contratos de serviço](designing-service-contracts.md). Observe que um cliente também pode ser solicitado a implementar um contrato definido pelo serviço, chamado de contrato de retorno de chamada, para receber mensagens do serviço em um MEP duplex. Para obter mais informações, consulte [duplex Services](./feature-details/duplex-services.md).

O ponto de extremidade de um serviço pode ser especificado de forma imperativa usando código ou declarativamente por meio de configuração. Se nenhum ponto de extremidade for especificado, o tempo de execução fornecerá pontos de extremidade padrão adicionando um ponto de extremidades padrão para cada endereço base para cada contrato de serviço implementado pelo serviço. A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Em geral, é mais prático definir pontos de extremidade de serviço usando a configuração em vez de código. Manter a ligação e as informações de endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar e reimplantar o aplicativo.

> [!NOTE]
> Ao adicionar um ponto de extremidade de serviço que executa a representação, você deve usar um dos métodos <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> ou o método <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> para carregar corretamente o contrato em um novo objeto <xref:System.ServiceModel.Description.ServiceDescription>.

## <a name="defining-endpoints-in-code"></a>Definindo pontos de extremidade no código

O exemplo a seguir ilustra como especificar um ponto de extremidade no código com o seguinte:

- Defina um contrato para um tipo de serviço `IEcho` que aceite o nome de uma pessoa e o eco com a resposta "Olá \<Name >!".

- Implemente um serviço `Echo` do tipo definido pelo contrato `IEcho`.

- Especifique um endereço de ponto de extremidade de `http://localhost:8000/Echo` para o serviço.

- Configure o serviço `Echo` usando uma associação de <xref:System.ServiceModel.WSHttpBinding>.

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Use a predefined WSHttpBinding to configure the service.
          WSHttpBinding binding = new WSHttpBinding();

          // Add the endpoint for this service to the service host.
          serviceHost.AddServiceEndpoint(
             typeof(IEcho),
             binding,
             echoUri
           );

          // Open the service host to run it.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Create a ServiceHost for the Echo service.
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)

' Use a predefined WSHttpBinding to configure the service.
Dim binding As New WSHttpBinding()

' Add the endpoint for this service to the service host.
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)

' Open the service host to run it.
serviceHost.Open()
```

> [!NOTE]
> O host de serviço é criado com um endereço base e, em seguida, o restante do endereço, relativo ao endereço base, é especificado como parte de um ponto de extremidade. Esse particionamento do endereço permite que vários pontos de extremidade sejam definidos mais convenientemente para os serviços em um host.

> [!NOTE]
> As propriedades de <xref:System.ServiceModel.Description.ServiceDescription> no aplicativo de serviço não devem ser modificadas subsequentemente para o método <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> em <xref:System.ServiceModel.ServiceHostBase>. Alguns membros, como a propriedade <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> e os métodos `AddServiceEndpoint` em <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, lançam uma exceção, caso sejam modificados após esse ponto. Outros permitem que você os modifique, mas o resultado é indefinido.
>
> Da mesma forma, no cliente os valores <xref:System.ServiceModel.Description.ServiceEndpoint> não devem ser modificados após a chamada para <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> no <xref:System.ServiceModel.ChannelFactory>. A propriedade <xref:System.ServiceModel.ChannelFactory.Credentials%2A> gera uma exceção, se modificada após esse ponto. Os outros valores de descrição do cliente podem ser modificados sem erros, mas o resultado é indefinido.
>
> Seja para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.

## <a name="defining-endpoints-in-configuration"></a>Definindo pontos de extremidade na configuração

Ao criar um aplicativo, muitas vezes você desejará adiar decisões para o administrador que está implantando o aplicativo. Por exemplo, geralmente não há como saber com antecedência o que será um endereço de serviço (URI). Em vez de embutir em código um endereço, é preferível permitir que um administrador faça isso depois de criar um serviço. Essa flexibilidade é realizada por meio da configuração. Para obter detalhes, consulte [Configurando serviços](configuring-services.md).

> [!NOTE]
> Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) com a opção `/config:`*filename*`[,`*filename*`]` para criar rapidamente os arquivos de configuração.

## <a name="using-default-endpoints"></a>Usando pontos de extremidade padrão

Se nenhum ponto de extremidade for especificado no código ou na configuração, o tempo de execução fornecerá os pontos de extremidade padrão adicionando um ponto de extremidades padrão para cada endereço base para cada contrato de serviço implementado pelo serviço. O endereço base pode ser especificado no código ou na configuração, e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.ICommunicationObject.Open> é chamado no <xref:System.ServiceModel.ServiceHost>. Este exemplo é o mesmo exemplo da seção anterior, mas como nenhum ponto de extremidade é especificado, os pontos de extremidade padrão são adicionados.

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Open the service host to run it. Default endpoints
          // are added when the service is opened.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Open the service host to run it. Default endpoints
' are added when the service is opened.
serviceHost.Open()
```

 Se os pontos de extremidade forem fornecidos explicitamente, os pontos de extremidade padrão ainda poderão ser adicionados chamando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> no <xref:System.ServiceModel.ServiceHost> antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificada](simplified-configuration.md) e [configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).

## <a name="see-also"></a>Consulte também

- [Implementando contratos de serviço](implementing-service-contracts.md)
