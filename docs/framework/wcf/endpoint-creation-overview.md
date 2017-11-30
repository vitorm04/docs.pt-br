---
title: "Visão geral de criação de ponto de extremidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b507f47c7dd4371d297b9ada1cb4610214aecb7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-creation-overview"></a>Visão geral de criação de ponto de extremidade
Toda a comunicação com um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço ocorre por meio de *pontos de extremidade* do serviço. Pontos de extremidade fornecem o acesso de clientes para a funcionalidade que um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ofertas de serviço. Esta seção descreve a estrutura de um ponto de extremidade e descreve como definir um ponto de extremidade na configuração e no código.  
  
## <a name="the-structure-of-an-endpoint"></a>A estrutura de um ponto de extremidade  
 Cada ponto de extremidade contém um endereço que indica onde encontrar o ponto de extremidade, uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade e um contrato que identifica os métodos disponíveis.  
  
-   **Endereço**. O endereço identifica o ponto de extremidade exclusivamente e informa potenciais consumidores onde se encontra o serviço. Ele é representado no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de objeto, o <xref:System.ServiceModel.EndpointAddress> endereço, que contém um identificador de recurso uniforme (URI) e as propriedades de endereço que incluem uma identidade, alguns elementos de WSDL Web Services Description Language () e uma coleção de cabeçalhos opcionais. Os cabeçalhos opcionais fornecem informações adicionais de endereçamento detalhadas para identificar ou interagir com o ponto de extremidade. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Especificando um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Associação**. A associação especifica como se comunicar com o ponto de extremidade. A associação especifica como o ponto de extremidade se comunica com o mundo, inclusive qual protocolo de transporte a ser usado (por exemplo, TCP ou HTTP), qual codificação a ser usada para as mensagens (por exemplo, texto ou binário), e os requisitos de segurança são necessários (para exemplo, Secure Sockets Layer [SSL] ou segurança de mensagens SOAP). [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Contrato de serviço**. O contrato de serviço descreve qual funcionalidade expõe o ponto de extremidade para o cliente. Um contrato especifica as operações que um cliente pode chamar, o formato da mensagem e o tipo de dados necessários para chamar a operação e o tipo de processamento ou o cliente pode esperar de mensagem de resposta ou parâmetros de entrada. Três tipos básicos de contratos correspondem aos padrões de troca de mensagem básica (MEPs): datagrama (unidirecional), solicitação/resposta e duplex (bidirecional). O contrato de serviço também pode empregar os contratos de dados e a mensagem em exigem tipos de dados específicos e formatos de mensagem quando acessados. [!INCLUDE[crabout](../../../includes/crabout-md.md)]como definir um contrato de serviço, consulte [criar contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md). Observe que um cliente também pode ser necessário para implementar um contrato de serviço definido, chamado de um contrato de retorno de chamada, para receber mensagens do serviço em um MEPS duplex. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Serviços duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 O ponto de extremidade para um serviço pode ser especificado imperativa por meio de código ou declarativamente por meio da configuração. Se nenhum ponto de extremidade forem especificados, em seguida, o tempo de execução fornece pontos de extremidade padrão adicionando um ponto de extremidade padrão para cada endereço base para cada contrato de serviço implementado pelo serviço. Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Geralmente, é mais prático definir pontos de extremidade de serviço usando a configuração em vez do código. Informações sem o código de endereçamento e manter a associação permite que a alteração sem ter que recompilar e reimplantar o aplicativo.  
  
> [!NOTE]
>  Ao adicionar um ponto de extremidade de serviço que executa representação, você deve usar uma da <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> métodos ou <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> método a carregar adequadamente o contrato para uma nova <xref:System.ServiceModel.Description.ServiceDescription> objeto.  
  
## <a name="defining-endpoints-in-code"></a>Definir pontos de extremidade no código  
 O exemplo a seguir ilustra como especificar um ponto de extremidade no código com o seguinte:  
  
-   Definir um contrato para um `IEcho` tipo de serviço que aceita o nome e o eco com a resposta de alguém "Hello \<nome >!".  
  
-   Implementar um `Echo` serviço do tipo definido pelo `IEcho` contrato.  
  
-   Especifique um endereço de ponto de extremidade de http://localhost:8000/eco para o serviço.  
  
-   Configurar o `Echo` de serviço usando um <xref:System.ServiceModel.WSHttpBinding> associação.  
  
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
>  O host de serviço é criado com um endereço base e, em seguida, o restante do endereço relativo ao endereço base, é especificado como parte de um ponto de extremidade. Esse particionamento do endereço permite que vários pontos de extremidade a ser definido de modo mais conveniente para serviços em um host.  
  
> [!NOTE]
>  Propriedades de <xref:System.ServiceModel.Description.ServiceDescription> no serviço de aplicativo não deve ser modificado após o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método <xref:System.ServiceModel.ServiceHostBase>. Alguns membros, como o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade e o `AddServiceEndpoint` métodos em <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, lançar uma exceção se modificados após esse ponto. Outros permitem que você modificá-las, mas o resultado é indefinido.  
>   
>  Da mesma forma, no cliente de <xref:System.ServiceModel.Description.ServiceEndpoint> valores não devem ser modificados após a chamada a <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> no <xref:System.ServiceModel.ChannelFactory>. O <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade gera uma exceção se modificado após esse ponto. Os outros valores de descrição do cliente podem ser modificados sem erro, mas o resultado é indefinido.  
>   
>  Se para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Definir pontos de extremidade na configuração  
 Ao criar um aplicativo, você geralmente deseja adiar decisões para o administrador que está implantando o aplicativo. Por exemplo, há geralmente não será nenhuma maneira de saber antecipadamente que um serviço resolver (um URI). Em vez de codificar um endereço, é preferível para permitir que um administrador fazer isso depois de criar um serviço. Essa flexibilidade é feita por meio da configuração. Para obter detalhes, consulte [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com o `/config:` *filename*`[,`*filename* `]` alternar para Crie rapidamente os arquivos de configuração.  
  
## <a name="using-default-endpoints"></a>Usando pontos de extremidade padrão  
 Se nenhum ponto de extremidade está especificados no código ou na configuração de tempo de execução fornece pontos de extremidade padrão com a adição de um ponto de extremidade padrão para cada endereço base para cada contrato de serviço implementado pelo serviço. O endereço base pode ser especificado no código ou na configuração e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.ICommunicationObject.Open> é chamado de <xref:System.ServiceModel.ServiceHost>. Este exemplo é o mesmo exemplo da seção anterior, mas como não há pontos de extremidade são especificados, os pontos de extremidade padrão são adicionados.  
  
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
  
 Se os pontos de extremidade são explicitamente fornecidos, os pontos de extremidade padrão ainda podem ser adicionados ao chamar <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> no <xref:System.ServiceModel.ServiceHost> antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. [!INCLUDE[crabout](../../../includes/crabout-md.md)]pontos de extremidade padrão, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md) (Implementando contratos de serviço)
