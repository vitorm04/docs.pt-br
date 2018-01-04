---
title: "Visão geral do cliente WCF"
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
helpviewer_keywords: clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d6dd9e34561f397c581e148a549ad85762c81e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-client-overview"></a>Visão geral do cliente WCF
Esta seção descreve o que os aplicativos cliente fazem, como configurar, criar e usar um cliente [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], e como proteger aplicativos cliente.  
  
## <a name="using-wcf-client-objects"></a>Usando objetos de cliente WCF  
 Um aplicativo cliente é um aplicativo gerenciado que usa um cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para se comunicar com outro aplicativo. Para criar um aplicativo cliente para um serviço do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], são necessárias as seguintes etapas:  
  
1.  Obter o contrato de serviço, as associações e as informações de endereço de um ponto de extremidade de serviço.  
  
2.  Criar um cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] que use essas informações.  
  
3.  Chamar as operações.  
  
4.  Fechar o objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 As seções a seguir abordam essas etapas e fazem breves introduções às seguintes questões:  
  
-   Manipulando erros.  
  
-   Configurando e protegendo clientes.  
  
-   Criando objetos de retorno de chamada para serviços duplex.  
  
-   Chamando serviços de modo assíncrono.  
  
-   Chamando serviços por meio de canais de cliente.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Obter o contrato de serviço, as associações e os endereços  
 No [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], os serviços e clientes modelam contratos usando atributos gerenciados, interfaces e métodos. Para se conectar a um serviço em um aplicativo cliente, é necessário obter as informações de tipo do contrato de serviço. Normalmente, você faz isso usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), que baixa os metadados do serviço, converte-o em um arquivo de código fonte gerenciado no idioma de sua escolha e cria um cliente arquivo de configuração de aplicativo que você pode usar para configurar seu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto cliente. Por exemplo, se você pretende criar um objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para chamar um `MyCalculatorService` e sabe que os metadados desse serviço serão publicados em `http://computerName/MyCalculatorService/Service.svc?wsdl`, o exemplo de código a seguir mostra como usar o Svcutil.exe para obter um arquivo `ClientCode.vb` que contenha o contrato de serviço em código gerenciado.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Você pode compilar esse código de contrato no aplicativo cliente ou em outro assembly que o aplicativo cliente poderá usar para criar um objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Você pode usar o arquivo de configuração para configurar o objeto de cliente para se conectar corretamente ao serviço.  
  
 Para obter um exemplo desse processo, consulte [como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Para obter mais informações sobre contratos, consulte [contratos](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Criar um novo objeto de cliente WCF  
 Um cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é um objeto local que representa um serviço do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] em um formato que o cliente pode usar para se comunicar com o serviço remoto. Os tipos de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] implementam o contrato de serviço de destino, para que, ao criar um e configurá-lo, você possa usar o objeto de cliente diretamente para chamar as operações de serviço. O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] executar converte de tempo, o método chama em mensagens, envia para o serviço, aguarda a resposta e retorna os valores para o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto de cliente como valores de retorno ou `out` ou `ref` parâmetros.  
  
 Você também pode usar objetos de canal de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para se conectar aos serviços e utilizá-los. Para obter detalhes, consulte [arquitetura do cliente WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Criando um novo objeto do WCF  
 Para ilustrar o uso de uma classe <xref:System.ServiceModel.ClientBase%601>, suponha que o seguinte contrato de serviço simples foi gerado em um aplicativo de serviço.  
  
> [!NOTE]
>  Se você estiver usando o [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] para criar o cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], os objetos serão automaticamente carregados no pesquisador de objetos quando você adicionar uma referência de serviço ao projeto.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Se você não estiver usando o [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], examine o código de contrato gerado para localizar o tipo que estende o <xref:System.ServiceModel.ClientBase%601> e a interface de contrato de serviço `ISampleService`. Nesse caso, esse tipo terá a seguinte aparência:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Essa classe pode ser criada como um objeto local usando um dos construtores, configurada e, em seguida, usada para se conectar a um serviço do tipo `ISampleService`.  
  
 É recomendável criar o objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] primeiro e, depois, usá-lo e fechá-lo em um único bloco try/catch. Você não deve usar a instrução `using` (`Using` no [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) porque isso pode mascarar exceções em determinados modos de falha. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]as seções a seguir, bem como [evitando problemas com a instrução Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Contratos, associações e endereços  
 Para que você possa criar um objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], configure-o. Especificamente, ele deve ter um serviço *ponto de extremidade* usar. O ponto de extremidade é a combinação de um contrato de serviço, uma associação e um endereço. ([!INCLUDE[crabout](../../../includes/crabout-md.md)] pontos de extremidade, consulte [pontos de extremidade: endereços, associações e contratos](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Normalmente, essas informações estão localizadas no [ \<ponto de extremidade >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) elemento em um arquivo de configuração do aplicativo cliente, como o a ferramenta Svcutil.exe gera e é carregada automaticamente quando você cria seu cliente objeto. Os dois tipos de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] também têm sobrecargas que permitem que você especifique essas informações de modo programático.  
  
 Por exemplo, um arquivo de configuração gerado de um `ISampleService` usado nos exemplos anteriores contém as seguintes informações de ponto de extremidade.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Esse arquivo de configuração especifica um ponto de extremidade de destino no elemento `<client>`. [!INCLUDE[crabout](../../../includes/crabout-md.md)] como usar vários pontos de extremidade de destino, consulte <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> ou os construtores <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType>.  
  
## <a name="calling-operations"></a>Chamando operações  
 Depois que você tiver um objeto de cliente criado e configurado, crie um bloco try/catch, chame as operações da mesma maneira que faria se o objeto fosse local e feche o objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Quando o aplicativo cliente chama a primeira operação, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] abre automaticamente o canal subjacente, e este é fechado quando o objeto é reciclado. (Como alternativa, você também pode abrir e fechar explicitamente o canal antes ou após chamar outras operações.)  
  
 Por exemplo, se você tiver o seguinte contrato de serviço:  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 Poderá chamar as operações criando um objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e chamando seus métodos, conforme demonstrado pelo seguinte exemplo de código. Observe que a abertura, a chamada e o fechamento do objeto de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ocorre em um único bloco try/catch. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Acessar serviços usando um cliente WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) e [evitando problemas com a instrução Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Manipulando erros  
 Poderão ocorrer exceções em um aplicativo cliente quando o canal de cliente subjacente for aberto (explícita ou automaticamente, durante o chamamento de uma operação), o objeto de cliente ou de canal for usado para chamar operações, ou o canal de cliente subjacente for fechado. É recomendável que os aplicativos possam, pelo menos, manipular as exceções <xref:System.TimeoutException?displayProperty=nameWithType> e <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> possíveis, além de qualquer objeto <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> lançado como resultado de falhas de SOAP retornadas pelas operações. As falhas de SOAP especificadas no contrato de operação são geradas para aplicativos cliente como <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>, em que o parâmetro de tipo é o tipo de detalhe da falha de SOAP. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Tratando condições de erro em um aplicativo cliente, consulte [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md). Para um conjunto completo de exemplo o mostra como tratar erros em um cliente, consulte [esperado exceções](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Configurando e protegendo clientes  
 A configuração de um cliente começa com o carregamento obrigatório das informações de ponto de extremidade de destino do objeto de cliente ou de canal, geralmente em um arquivo de configuração, embora você também pode carregar essas informações de modo programático, usando as propriedades e os construtores de cliente. No entanto, são necessárias etapas adicionais de configuração em vários cenários de segurança e para habilitar determinado comportamento de cliente.  
  
 Por exemplo, os requisitos de segurança dos contratos de serviço são declarados na interface do contrato de serviço e, se a ferramenta Svcutil.exe tiver criado um arquivo de configuração, este geralmente conterá uma associação capaz de oferecer suporte aos requisitos de segurança do serviço. Em alguns casos, no entanto, talvez seja necessário definir configurações de segurança adicional, como configurar credenciais do cliente. Para obter informações completas sobre a configuração de segurança para [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] clientes, consulte [Protegendo clientes](../../../docs/framework/wcf/securing-clients.md).  
  
 Além disso, algumas modificações personalizadas podem ser habilitadas em aplicativos cliente, como comportamentos personalizados de tempo de execução. [!INCLUDE[crabout](../../../includes/crabout-md.md)]como configurar um comportamento de cliente personalizadas, consulte [Configurando comportamentos do cliente](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Criando objetos de retorno de chamada para serviços duplex  
 Os serviços duplex especificam um contrato de retorno de chamada que o aplicativo cliente deve implementar para fornecer um objeto de retorno de chamada que o serviço chamará de acordo com os requisitos do contrato. Embora os objetos de retorno de chamada não sejam serviços completos (por exemplo, você não pode iniciar um canal com um objeto de retorno de chamada), para fins de implementação e configuração, eles podem ser considerados um tipo de serviço.  
  
 Os clientes dos serviços duplex devem:  
  
-   Implementar uma classe de contrato de retorno de chamada.  
  
-   Criar uma instância da classe de implementação de contrato de retorno de chamada e utilizá-la para criar o objeto <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> que você passa para o construtor do cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
-   Chamar operações e manipular retornos de chamada de operação.  
  
 Os objetos de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] duplex funcionam como seus equivalentes não duplex; a única diferença é que eles expõem a funcionalidade necessária para oferecer suporte aos retornos de chamada, incluindo a configuração do serviço de retorno de chamada.  
  
 Por exemplo, você pode controlar vários aspectos do comportamento de tempo de execução do objeto de retorno de chamada usando as propriedades do atributo <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> da classe de retorno de chamada. Outro exemplo é o uso da classe <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> para habilitar o retorno das informações de exceção para serviços que chamam o objeto de retorno de chamada. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Serviços duplex](../../../docs/framework/wcf/feature-details/duplex-services.md). Para obter um exemplo completo, consulte [Duplex](../../../docs/framework/wcf/samples/duplex.md).  
  
 Em computadores com o Windows XP que executam os Serviços de Informações da Internet (IIS) 5.1, os clientes duplex devem especificar um endereço básico de cliente usando a classe <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>; do contrário, uma exceção será lançada. O exemplo de código a seguir mostra como fazer isso no código.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 O exemplo de código a seguir mostra como fazer isso em um arquivo de configuração  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Chamando serviços de modo assíncrono  
 A maneira como as operações serão chamadas fica totalmente a cargo do desenvolvedor do cliente. Isso acontece porque as mensagens que compõem uma operação podem ser mapeadas para métodos síncronos ou assíncronos quando expressas em código gerenciado. Portanto, se você quiser compilar um cliente que chama operações de forma assíncrona, use o Svcutil.exe para gerar um código de cliente assíncrono usando a opção `/async`. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Como: chamar operações de serviço de forma assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Chamando serviços por meio de canais de cliente WCF  
 Os tipos de cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] estendem o <xref:System.ServiceModel.ClientBase%601>, que é derivado da interface <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> para expor o sistema de canal subjacente. Você pode chamar serviços usando o contrato de serviço de destino com a classe <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Para obter detalhes, consulte [arquitetura do cliente WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
