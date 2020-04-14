---
title: Visão geral do cliente WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: c12579062b04cfb46e14d5c3d734a7c155f8d654
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278880"
---
# <a name="wcf-client-overview"></a>Visão geral do cliente WCF

Esta seção descreve o que os aplicativos clientes fazem, como configurar, criar e usar um cliente WCF (Windows Communication Foundation) e como proteger aplicativos clientes.  
  
## <a name="using-wcf-client-objects"></a>Usando objetos de cliente WCF  
 Um aplicativo cliente é um aplicativo gerenciado que usa um cliente WCF para se comunicar com outro aplicativo. A criação de um aplicativo cliente para um serviço WCF requer as seguintes etapas:  
  
1. Obter o contrato de serviço, as associações e as informações de endereço de um ponto de extremidade de serviço.  
  
2. Crie um cliente WCF usando essas informações.  
  
3. Chamar as operações.  
  
4. Feche o objeto cliente WCF.  
  
As seções a seguir abordam essas etapas e fazem breves introduções às seguintes questões:  
  
- Tratamento de erros.  
  
- Configurando e protegendo clientes.  
  
- Criando objetos de retorno de chamada para serviços duplex.  
  
- Chamando serviços de modo assíncrono.  
  
- Chamando serviços por meio de canais de cliente.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Obter o contrato de serviço, as associações e os endereços  
 No WCF, os contratos de modelo de serviços e clientes utilizam atributos, interfaces e métodos gerenciados. Para se conectar a um serviço em um aplicativo cliente, é necessário obter as informações de tipo do contrato de serviço. Normalmente, você faz isso usando o [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), que baixa metadados do serviço, converte-os em um arquivo de código-fonte gerenciado no idioma de sua escolha e cria um arquivo de configuração de aplicativo cliente que você pode usar para configurar seu objeto cliente WCF. Por exemplo, se você vai criar um objeto `MyCalculatorService`cliente WCF para invocar um , e `http://computerName/MyCalculatorService/Service.svc?wsdl`você sabe que os metadados para esse serviço são `ClientCode.vb` publicados em , então o exemplo de código a seguir mostra como usar Svcutil.exe para obter um arquivo que contém o contrato de serviço em código gerenciado.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Você pode compilar esse código de contrato no aplicativo do cliente ou em outro conjunto que o aplicativo cliente possa usar para criar um objeto cliente WCF. Você pode usar o arquivo de configuração para configurar o objeto de cliente para se conectar corretamente ao serviço.  
  
 Para um exemplo desse processo, consulte [Como: Criar um Cliente](how-to-create-a-wcf-client.md). Para obter informações mais completas sobre contratos, consulte [Contratos](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Criar um novo objeto de cliente WCF  
 Um cliente WCF é um objeto local que representa um serviço WCF em um formulário que o cliente pode usar para se comunicar com o serviço remoto. Os tipos de clientes WCF implementam o contrato de serviço de destino, então, quando você cria um e o configura, você pode usar o objeto cliente diretamente para invocar operações de serviço. O tempo de execução do WCF converte as chamadas do método em mensagens, envia-as para o serviço, ouve a resposta e devolve esses valores ao objeto cliente WCF como valores de retorno ou `out` parâmetros. `ref`  
  
 Você também pode usar objetos de canal cliente WCF para se conectar e usar serviços. Para obter detalhes, consulte [WCF Client Architecture](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Criando um novo objeto do WCF  
 Para ilustrar o uso de uma classe <xref:System.ServiceModel.ClientBase%601>, suponha que o seguinte contrato de serviço simples foi gerado em um aplicativo de serviço.  
  
> [!NOTE]
> Se você estiver usando o Visual Studio para criar seu cliente WCF, os objetos são carregados automaticamente no navegador de objetos quando você adiciona uma referência de serviço ao seu projeto.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Se você não estiver usando o Visual Studio, examine <xref:System.ServiceModel.ClientBase%601> o código do `ISampleService`contrato gerado para encontrar o tipo que se estende e a interface do contrato de serviço . Nesse caso, esse tipo terá a seguinte aparência:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Essa classe pode ser criada como um objeto local usando um dos construtores, configurada e, em seguida, usada para se conectar a um serviço do tipo `ISampleService`.  
  
 Recomenda-se que você crie primeiro o objeto cliente WCF e, em seguida, use-o e feche-o dentro de um único bloco de tentativa/captura. Não use a `using` declaração (no`Using` Visual Basic) porque ela pode mascarar exceções em certos modos de falha. Para obter mais informações, consulte as seguintes seções, bem como [Use Close e Abort para liberar recursos do cliente WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Contratos, associações e endereços  
 Antes de criar um objeto cliente WCF, você deve configurar o objeto cliente. Especificamente, ele deve ter um *ponto final de* serviço para usar. O ponto de extremidade é a combinação de um contrato de serviço, uma associação e um endereço. (Para obter mais informações sobre pontos finais, consulte [Pontos finais: Endereços, Vinculações e Contratos](./feature-details/endpoints-addresses-bindings-and-contracts.md).) Normalmente, essas informações estão localizadas no [ \<ponto final>](../configure-apps/file-schema/wcf/endpoint-of-client.md) elemento em um arquivo de configuração de aplicativo cliente, como a que a ferramenta Svcutil.exe gera, e é carregada automaticamente quando você cria seu objeto cliente. Ambos os tipos de clientes WCF também têm sobrecargas que permitem especificar programáticamente essas informações.  
  
 Por exemplo, um arquivo de configuração gerado de um `ISampleService` usado nos exemplos anteriores contém as seguintes informações de ponto de extremidade.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Esse arquivo de configuração especifica um ponto de extremidade de destino no elemento `<client>`. Para obter mais informações sobre o <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> uso <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> de vários pontos finais de destino, consulte os construtores ou os construtores.  
  
## <a name="calling-operations"></a>Chamando operações  
 Depois de ter um objeto cliente criado e configurado, crie um bloco de tentativa/captura, chame as operações da mesma forma que você faria se o objeto fosse local e feche o objeto cliente WCF. Quando o aplicativo cliente chama a primeira operação, o WCF abre automaticamente o canal subjacente e o canal subjacente é fechado quando o objeto é reciclado. (Como alternativa, você também pode abrir e fechar explicitamente o canal antes ou após chamar outras operações.)  
  
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
  
 Você pode chamar as operações criando um objeto cliente WCF e chamando seus métodos, como o exemplo de código a seguir demonstra. A abertura, chamada e fechamento do objeto cliente WCF ocorre dentro de um único bloco de tentativa/captura. Para obter mais informações, consulte [Acessar serviços usando um cliente WCF](./feature-details/accessing-services-using-a-client.md) e [usar close e abort para liberar recursos de cliente sw.](./samples/use-close-abort-release-wcf-client-resources.md)  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Tratando erros  
 Poderão ocorrer exceções em um aplicativo cliente quando o canal de cliente subjacente for aberto (explícita ou automaticamente, durante o chamamento de uma operação), o objeto de cliente ou de canal for usado para chamar operações, ou o canal de cliente subjacente for fechado. É recomendável que os aplicativos possam, pelo menos, manipular as exceções <xref:System.TimeoutException?displayProperty=nameWithType> e <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> possíveis, além de qualquer objeto <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> lançado como resultado de falhas de SOAP retornadas pelas operações. As falhas de SOAP especificadas no contrato de operação são geradas para aplicativos cliente como <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>, em que o parâmetro de tipo é o tipo de detalhe da falha de SOAP. Para obter mais informações sobre condições de erro de manuseio em um aplicativo cliente, consulte [Envio e Recebimento de Falhas](sending-and-receiving-faults.md). Para obter uma amostra completa, mostra como lidar com erros em um cliente, consulte [Exceções esperadas](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Configurando e protegendo clientes  
 A configuração de um cliente começa com o carregamento obrigatório das informações de ponto de extremidade de destino do objeto de cliente ou de canal, geralmente em um arquivo de configuração, embora você também pode carregar essas informações de modo programático, usando as propriedades e os construtores de cliente. No entanto, são necessárias etapas adicionais de configuração em vários cenários de segurança e para habilitar determinado comportamento de cliente.  
  
 Por exemplo, os requisitos de segurança dos contratos de serviço são declarados na interface do contrato de serviço e, se a ferramenta Svcutil.exe tiver criado um arquivo de configuração, este geralmente conterá uma associação capaz de oferecer suporte aos requisitos de segurança do serviço. Em alguns casos, no entanto, talvez seja necessário definir configurações de segurança adicional, como configurar credenciais do cliente. Para obter informações completas sobre a configuração de segurança para clientes WCF, consulte [Protegendo clientes](securing-clients.md).  
  
 Além disso, algumas modificações personalizadas podem ser habilitadas em aplicativos cliente, como comportamentos personalizados de tempo de execução. Para obter mais informações sobre como configurar um comportamento personalizado do cliente, consulte [Configurando comportamentos do cliente](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Criando objetos de retorno de chamada para serviços duplex  
 Os serviços duplex especificam um contrato de retorno de chamada que o aplicativo cliente deve implementar para fornecer um objeto de retorno de chamada que o serviço chamará de acordo com os requisitos do contrato. Embora os objetos de retorno de chamada não sejam serviços completos (por exemplo, você não pode iniciar um canal com um objeto de retorno de chamada), para fins de implementação e configuração, eles podem ser considerados um tipo de serviço.  
  
 Os clientes dos serviços duplex devem:  
  
- Implementar uma classe de contrato de retorno de chamada.  
  
- Crie uma instância da classe de implementação do <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> contrato de retorno de chamada e use-a para criar o objeto que você passar para o construtor cliente WCF.  
  
- Chamar operações e manipular retornos de chamada de operação.  
  
 Os objetos clientes Duplex WCF funcionam como suas contrapartes não duplex, com a exceção de que expõem a funcionalidade necessária para suportar retornos de chamadas, incluindo a configuração do serviço de retorno de chamada.  
  
 Por exemplo, você pode controlar vários aspectos do comportamento de runtime do objeto de retorno de chamada usando as propriedades do atributo <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> da classe de retorno de chamada. Outro exemplo é o uso da classe <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> para habilitar o retorno das informações de exceção para serviços que chamam o objeto de retorno de chamada. Para obter mais informações, consulte [Serviços Duplex](./feature-details/duplex-services.md). Para obter uma amostra completa, consulte [Duplex](./samples/duplex.md).  
  
 Em computadores com o Windows XP que executam os Serviços de Informações da Internet (IIS) 5.1, os clientes duplex devem especificar um endereço básico de cliente usando a classe <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>; do contrário, uma exceção será lançada. O exemplo de código a seguir mostra como fazer isso no código.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 O exemplo de código a seguir mostra como fazer isso em um arquivo de configuração  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Chamando serviços de modo assíncrono  
 A maneira como as operações serão chamadas fica totalmente a cargo do desenvolvedor do cliente. Isso acontece porque as mensagens que compõem uma operação podem ser mapeadas para métodos síncronos ou assíncronos quando expressas em código gerenciado. Portanto, se você quiser compilar um cliente que chama operações de forma assíncrona, use o Svcutil.exe para gerar um código de cliente assíncrono usando a opção `/async`. Para obter mais informações, consulte [Como: Chamar operações de serviço assíncronamente](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Chamando serviços por meio de canais de cliente WCF  
 Os tipos de <xref:System.ServiceModel.ClientBase%601>clientes WCF <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> se estendem, que por si só deriva da interface para expor o sistema de canal subjacente. Você pode chamar serviços usando o contrato de serviço de destino com a classe <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Para obter detalhes, consulte [WCF Client Architecture](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
