---
title: Visão geral do cliente WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 5cb73dfeaac4f1c23724dc71b0f1f5d07fd28b5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791229"
---
# <a name="wcf-client-overview"></a>Visão geral do cliente WCF
Esta seção descreve o que fazem aplicativos cliente, como configurar, criar e usar um cliente do Windows Communication Foundation (WCF) e como proteger aplicativos cliente.  
  
## <a name="using-wcf-client-objects"></a>Usando objetos de cliente WCF  
 Um aplicativo cliente é um aplicativo gerenciado que usa um cliente WCF para se comunicar com outro aplicativo. Para criar um cliente de aplicativo para um serviço WCF requer as seguintes etapas:  
  
1. Obter o contrato de serviço, as associações e as informações de endereço de um ponto de extremidade de serviço.  
  
2. Crie um cliente WCF usando essas informações.  
  
3. Chamar as operações.  
  
4. Feche o objeto de cliente do WCF.  
  
 As seções a seguir abordam essas etapas e fazem breves introduções às seguintes questões:  
  
- Manipulando erros.  
  
- Configurando e protegendo clientes.  
  
- Criando objetos de retorno de chamada para serviços duplex.  
  
- Chamando serviços de modo assíncrono.  
  
- Chamando serviços por meio de canais de cliente.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Obter o contrato de serviço, as associações e os endereços  
 No WCF, serviços e clientes do modelo contratos usando atributos gerenciados, interfaces e métodos. Para se conectar a um serviço em um aplicativo cliente, é necessário obter as informações de tipo do contrato de serviço. Normalmente, você faz isso usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), que baixa metadados do serviço, converte-o em um arquivo de código fonte gerenciado na linguagem de sua escolha e cria um cliente arquivo de configuração do aplicativo que você pode usar para configurar o objeto de cliente do WCF. Por exemplo, se você pretende criar um objeto de cliente WCF para invocar um `MyCalculatorService`, e você souber que os metadados para o serviço é publicado ao `http://computerName/MyCalculatorService/Service.svc?wsdl`, em seguida, o exemplo de código a seguir mostra como usar Svcutil.exe para obter um `ClientCode.vb` de arquivos que contém o contrato de serviço em código gerenciado.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Você pode compilar esse código de contrato no aplicativo cliente ou em outro assembly que o aplicativo cliente, em seguida, pode usar para criar um objeto de cliente do WCF. Você pode usar o arquivo de configuração para configurar o objeto de cliente para se conectar corretamente ao serviço.  
  
 Para obter um exemplo desse processo, consulte [como: Criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Para obter informações mais completas sobre os contratos, consulte [contratos](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Criar um novo objeto de cliente WCF  
 Um cliente do WCF é um objeto local que representa um serviço WCF em um formulário que o cliente pode usar para se comunicar com o serviço remoto. Tipos de cliente WCF implementam o serviço de destino de contrato, portanto, quando você cria um e configurá-lo, em seguida, você pode usar o objeto de cliente diretamente para chamar as operações de serviço. O tempo de execução do WCF converte as chamadas de método em mensagens, envia-os para o serviço, escuta a resposta e retorna os valores para o objeto de cliente do WCF como valores de retorno ou `out` ou `ref` parâmetros.  
  
 Você também pode usar objetos de canal de cliente do WCF para se conectar e usar os serviços. Para obter detalhes, consulte [arquitetura de cliente WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Criando um novo objeto do WCF  
 Para ilustrar o uso de uma classe <xref:System.ServiceModel.ClientBase%601>, suponha que o seguinte contrato de serviço simples foi gerado em um aplicativo de serviço.  
  
> [!NOTE]
>  Se você estiver usando o Visual Studio para criar seu cliente do WCF, os objetos são carregados automaticamente no Pesquisador de objetos quando você adiciona uma referência de serviço ao seu projeto.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Se você não estiver usando o Visual Studio, examine o código de contrato gerado para localizar o tipo que estende <xref:System.ServiceModel.ClientBase%601> e a interface de contrato de serviço `ISampleService`. Nesse caso, esse tipo terá a seguinte aparência:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Essa classe pode ser criada como um objeto local usando um dos construtores, configurada e, em seguida, usada para se conectar a um serviço do tipo `ISampleService`.  
  
 É recomendável que você crie o objeto de cliente do WCF em primeiro lugar e, em seguida, usá-lo e fechá-lo em um bloco try/catch único. Você não deve usar o `using` instrução (`Using` no Visual Basic) porque isso pode mascarar exceções em determinados modos de falha. Para obter mais informações, consulte as seções a seguir, bem como [uso Close e Abort para liberar os recursos de cliente do WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Contratos, associações e endereços  
 Antes de criar um objeto de cliente do WCF, você deve configurar o objeto de cliente. Especificamente, ele deve ter um serviço *ponto de extremidade* usar. O ponto de extremidade é a combinação de um contrato de serviço, uma associação e um endereço. (Para obter mais informações sobre pontos de extremidade, consulte [pontos de extremidade: Endereços, associações e contratos](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Normalmente, essas informações estão localizadas na [ \<ponto de extremidade >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) elemento em um arquivo de configuração do aplicativo cliente, como a ferramenta Svcutil.exe gera e é carregada automaticamente quando você cria seu cliente objeto. Ambos os tipos de cliente WCF também têm sobrecargas que permitem que você especificar essas informações de forma programática.  
  
 Por exemplo, um arquivo de configuração gerado de um `ISampleService` usado nos exemplos anteriores contém as seguintes informações de ponto de extremidade.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Esse arquivo de configuração especifica um ponto de extremidade de destino no elemento `<client>`. Para obter mais informações sobre como usar vários pontos de extremidade de destino, consulte o <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> ou o <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> construtores.  
  
## <a name="calling-operations"></a>Chamando operações  
 Uma vez você tem um objeto de cliente criado e configurado, criar um bloco try/catch, chame as operações da mesma maneira que faria se o objeto fosse local e fechar o objeto de cliente do WCF. Quando o aplicativo cliente chama a primeira operação, WCF abre automaticamente o canal subjacente e o canal subjacente é fechado quando o objeto é reciclado. (Como alternativa, você também pode abrir e fechar explicitamente o canal antes ou após chamar outras operações.)  
  
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
  
 Você pode chamar as operações com a criação de um objeto de cliente do WCF e chamando seus métodos, como o exemplo de código a seguir demonstra. Observe que a abertura, a chamada e o fechamento do objeto de cliente WCF ocorre dentro de um bloco try/catch único. Para obter mais informações, consulte [serviços de acesso usando um cliente WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) e [uso Close e Abort para liberar os recursos de cliente do WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Manipulando erros  
 Poderão ocorrer exceções em um aplicativo cliente quando o canal de cliente subjacente for aberto (explícita ou automaticamente, durante o chamamento de uma operação), o objeto de cliente ou de canal for usado para chamar operações, ou o canal de cliente subjacente for fechado. É recomendável que os aplicativos possam, pelo menos, manipular as exceções <xref:System.TimeoutException?displayProperty=nameWithType> e <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> possíveis, além de qualquer objeto <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> lançado como resultado de falhas de SOAP retornadas pelas operações. As falhas de SOAP especificadas no contrato de operação são geradas para aplicativos cliente como <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>, em que o parâmetro de tipo é o tipo de detalhe da falha de SOAP. Para obter mais informações sobre como lidar com condições de erro em um aplicativo cliente, consulte [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md). Para um exemplo completo que mostra como tratar erros em um cliente, consulte [esperado exceções](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Configurando e protegendo clientes  
 A configuração de um cliente começa com o carregamento obrigatório das informações de ponto de extremidade de destino do objeto de cliente ou de canal, geralmente em um arquivo de configuração, embora você também pode carregar essas informações de modo programático, usando as propriedades e os construtores de cliente. No entanto, são necessárias etapas adicionais de configuração em vários cenários de segurança e para habilitar determinado comportamento de cliente.  
  
 Por exemplo, os requisitos de segurança dos contratos de serviço são declarados na interface do contrato de serviço e, se a ferramenta Svcutil.exe tiver criado um arquivo de configuração, este geralmente conterá uma associação capaz de oferecer suporte aos requisitos de segurança do serviço. Em alguns casos, no entanto, talvez seja necessário definir configurações de segurança adicional, como configurar credenciais do cliente. Para obter informações completas sobre a configuração de segurança para clientes do WCF, consulte [Protegendo clientes](../../../docs/framework/wcf/securing-clients.md).  
  
 Além disso, algumas modificações personalizadas podem ser habilitadas em aplicativos cliente, como comportamentos personalizados de tempo de execução. Para obter mais informações sobre como configurar um comportamento de cliente personalizadas, consulte [Configurando comportamentos do cliente](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Criando objetos de retorno de chamada para serviços duplex  
 Os serviços duplex especificam um contrato de retorno de chamada que o aplicativo cliente deve implementar para fornecer um objeto de retorno de chamada que o serviço chamará de acordo com os requisitos do contrato. Embora os objetos de retorno de chamada não sejam serviços completos (por exemplo, você não pode iniciar um canal com um objeto de retorno de chamada), para fins de implementação e configuração, eles podem ser considerados um tipo de serviço.  
  
 Os clientes dos serviços duplex devem:  
  
- Implementar uma classe de contrato de retorno de chamada.  
  
- Crie uma instância da classe de implementação de contrato de retorno de chamada e usá-lo para criar o <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objeto que você passa para o construtor de cliente do WCF.  
  
- Chamar operações e manipular retornos de chamada de operação.  
  
 Função duplex de objetos de cliente WCF como suas contrapartes nonduplex, com exceção de que eles expõem a funcionalidade necessária para dar suporte a retornos de chamada, incluindo a configuração do serviço de retorno de chamada.  
  
 Por exemplo, você pode controlar vários aspectos do comportamento de tempo de execução do objeto de retorno de chamada usando as propriedades do atributo <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> da classe de retorno de chamada. Outro exemplo é o uso da classe <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> para habilitar o retorno das informações de exceção para serviços que chamam o objeto de retorno de chamada. Para obter mais informações, consulte [serviços Duplex](../../../docs/framework/wcf/feature-details/duplex-services.md). Para obter um exemplo completo, consulte [Duplex](../../../docs/framework/wcf/samples/duplex.md).  
  
 Em computadores com o Windows XP que executam os Serviços de Informações da Internet (IIS) 5.1, os clientes duplex devem especificar um endereço básico de cliente usando a classe <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>; do contrário, uma exceção será lançada. O exemplo de código a seguir mostra como fazer isso no código.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 O exemplo de código a seguir mostra como fazer isso em um arquivo de configuração  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Chamando serviços de modo assíncrono  
 A maneira como as operações serão chamadas fica totalmente a cargo do desenvolvedor do cliente. Isso acontece porque as mensagens que compõem uma operação podem ser mapeadas para métodos síncronos ou assíncronos quando expressas em código gerenciado. Portanto, se você quiser compilar um cliente que chama operações de forma assíncrona, use o Svcutil.exe para gerar um código de cliente assíncrono usando a opção `/async`. Para obter mais informações, confira [Como: Chamar operações de serviço de forma assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Chamando serviços por meio de canais de cliente WCF  
 Estendem os tipos de cliente WCF <xref:System.ServiceModel.ClientBase%601>, que é derivada de <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface para expor o sistema de canal subjacente. Você pode chamar serviços usando o contrato de serviço de destino com a classe <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Para obter detalhes, consulte [arquitetura de cliente WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
