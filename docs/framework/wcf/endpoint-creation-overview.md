---
title: Visão geral de criação de ponto de extremidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: fa6486db483c004430e0e8ed75c75a6b25c05d6b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613578"
---
# <a name="endpoint-creation-overview"></a>Visão geral de criação de ponto de extremidade
Toda a comunicação com um serviço do Windows Communication Foundation (WCF) ocorre por meio de *pontos de extremidade* do serviço. Pontos de extremidade fornecem os clientes acessem a funcionalidade que oferece um serviço WCF. Esta seção descreve a estrutura de um ponto de extremidade e descreve como definir um ponto de extremidade na configuração e no código.  
  
## <a name="the-structure-of-an-endpoint"></a>A estrutura de um ponto de extremidade  
 Cada ponto de extremidade contém um endereço que indica onde encontrar o ponto de extremidade, uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade e um contrato que identifica os métodos disponíveis.  
  
- **Endereço**. O endereço identifica o ponto de extremidade exclusivamente e informa à consumidores em potencial em que o serviço está localizado. Ele é representado no modelo de objeto WCF pelo <xref:System.ServiceModel.EndpointAddress> endereço, que contém um identificador de recurso uniforme (URI) e as propriedades de endereço que incluem uma identidade, alguns elementos de descrição linguagem WSDL (Web Services) e uma coleção de opcional cabeçalhos. Os cabeçalhos opcionais fornecem informações adicionais de endereçamento detalhadas para identificar ou interagir com o ponto de extremidade. Para obter mais informações, consulte [especificação de um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
- **Associação**. A associação especifica como se comunicar com o ponto de extremidade. A associação especifica como o ponto de extremidade se comunica com o mundo, incluindo qual protocolo de transporte usar (por exemplo, TCP ou HTTP), codificação a ser usada para as mensagens (por exemplo, texto ou binário), e quais requisitos de segurança são necessários (para exemplo, Secure Sockets Layer [SSL] ou segurança de mensagem SOAP). Para obter mais informações, consulte [usando associações para configurar os serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
- **Contrato de serviço**. O contrato de serviço descreve qual funcionalidade que o ponto de extremidade expõe para o cliente. Um contrato especifica as operações que um cliente pode chamar, o formulário da mensagem e o tipo de dados necessários para chamar a operação e o tipo de processamento ou o cliente pode esperar de mensagem de resposta ou parâmetros de entrada. Três tipos básicos de contratos correspondem aos padrões de troca de mensagens básicas (MEPs): datagrama (unidirecional), solicitação/resposta e duplex (bidirecional). O contrato de serviço também pode empregar os contratos de dados e a mensagem em exigem tipos de dados específicos e formatos de mensagem quando acessados. Para obter mais informações sobre como definir um contrato de serviço, consulte [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md). Observe que um cliente também pode ser necessário para implementar um contrato de serviço definido, chamado de um contrato de retorno de chamada, receber mensagens do serviço em um MEP duplex. Para obter mais informações, consulte [serviços Duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 O ponto de extremidade para um serviço pode ser especificado imperativamente por meio de código ou declarativamente por meio da configuração. Se nenhum ponto de extremidade forem especificados, em seguida, o tempo de execução fornece pontos de extremidade padrão com a adição de um ponto de extremidade padrão para cada endereço base para cada contrato de serviço implementado pelo serviço. Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Em geral, é mais prático definir pontos de extremidade de serviço usando a configuração em vez de código. Informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar e reimplantar o aplicativo.  
  
> [!NOTE]
>  Ao adicionar um ponto de extremidade de serviço que executa representação, você deve usar um dos <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> métodos ou o <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> método para carregar corretamente o contrato em um novo <xref:System.ServiceModel.Description.ServiceDescription> objeto.  
  
## <a name="defining-endpoints-in-code"></a>Definir pontos de extremidade no código  
 O exemplo a seguir ilustra como especificar um ponto de extremidade no código com o seguinte:  
  
- Definir um contrato para um `IEcho` tipo de serviço que aceita o nome e o eco com a resposta de alguém "Hello \<nome >!".  
  
- Implementar uma `Echo` serviço do tipo definido pelo `IEcho` contrato.  
  
- Especifique um endereço de ponto de extremidade de `http://localhost:8000/Echo` para o serviço.  
  
- Configurar o `Echo` usando um <xref:System.ServiceModel.WSHttpBinding> associação.  
  
```csharp  
Namespace Echo  
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
>  O host de serviço é criado com um endereço básico e, em seguida, o restante do endereço, relativo ao endereço base, é especificado como parte de um ponto de extremidade. Esse particionamento do endereço permite que vários pontos de extremidade seja definido de forma mais conveniente para os serviços em um host.  
  
> [!NOTE]
>  Propriedades de <xref:System.ServiceModel.Description.ServiceDescription> no serviço de aplicativo não deve ser modificado subsequente para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método em <xref:System.ServiceModel.ServiceHostBase>. Alguns membros, como o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade e o `AddServiceEndpoint` métodos <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, lançar uma exceção se modificado além daquele ponto. Outros permitem que você modificá-los, mas o resultado será indefinido.  
>   
>  Da mesma forma, no cliente a <xref:System.ServiceModel.Description.ServiceEndpoint> valores não devem ser modificados após a chamada para <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sobre o <xref:System.ServiceModel.ChannelFactory>. O <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade gera uma exceção se modificado após esse ponto. Os outros valores de descrição de cliente podem ser modificados sem erro, mas o resultado será indefinido.  
>   
>  Se para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Definir pontos de extremidade na configuração  
 Ao criar um aplicativo, você geralmente deseja adiar as decisões para o administrador que está implantando o aplicativo. Por exemplo, há muitas vezes não há como saber antecipadamente que um serviço (um URI) de endereços será. Em vez de embutir um endereço, é preferível para permitir que um administrador para fazer isso depois de criar um serviço. Essa flexibilidade é realizada por meio da configuração. Para obter detalhes, consulte [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Use o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com o `/config:` *filename*`[,`*filename* `]` alternar para Crie rapidamente arquivos de configuração.  
  
## <a name="using-default-endpoints"></a>Usando pontos de extremidade padrão  
 Se nenhum ponto de extremidade forem especificados no código ou na configuração, em seguida, o tempo de execução fornece pontos de extremidade padrão com a adição de um ponto de extremidade padrão para cada endereço base para cada contrato de serviço implementado pelo serviço. O endereço base pode ser especificado no código ou na configuração e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.ICommunicationObject.Open> é chamado de <xref:System.ServiceModel.ServiceHost>. Este exemplo é o mesmo exemplo da seção anterior, mas uma vez que nenhum ponto de extremidade forem especificados, os pontos de extremidade padrão são adicionados.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
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
  
 Se os pontos de extremidade forem fornecidos explicitamente, os pontos de extremidade padrão ainda podem ser adicionados chamando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> sobre o <xref:System.ServiceModel.ServiceHost> antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificado](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
