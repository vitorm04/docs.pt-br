---
title: Especificando e lidando com falhas em contratos e serviços
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: 7c64bdb0cf60fff2dad49c3ffc48629c53abecad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210666"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Especificando e lidando com falhas em contratos e serviços
Aplicativos do Windows Communication Foundation (WCF) lidar com situações de erro, mapeando objetos de exceção gerenciada para objetos de falhas SOAP e objetos de falhas SOAP em objetos de exceção gerenciada. Os tópicos desta seção discutem como criar contratos para expor o erro condições como falhas SOAP personalizadas, como retornar essas falhas como parte da implementação de serviço e como os clientes capturar essas falhas.  
  
## <a name="error-handling-overview"></a>Visão geral de manipulação de erro  
 Em todos os aplicativos gerenciados, os erros de processamento são representados por <xref:System.Exception> objetos. Aplicativos baseados em SOAP, como aplicativos do WCF, métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento. Falhas de SOAP são tipos de mensagem que são incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar sua operação mais robusta ou interativo. Além disso, como falhas de SOAP são demonstradas para clientes no formato XML, ele é um sistema de tipo altamente interoperável que podem usar os clientes em qualquer plataforma SOAP, aumentar o alcance do seu aplicativo do WCF.  
  
 Como os aplicativos do WCF executado em ambos os tipos de sistemas de erro, quaisquer informações de exceção gerenciada que são enviadas ao cliente devem ser convertidas de exceções em falhas de SOAP no serviço, enviadas e convertidas de falhas de SOAP para exceções de falha em clientes do WCF. No caso de clientes duplex, contratos com o cliente também podem enviar falhas de SOAP para um serviço. Em ambos os casos, você pode usar os comportamentos de exceção de serviço padrão, ou você pode controlar explicitamente se — e como — as exceções são mapeadas para mensagens de falha.  
  
 Dois tipos de falhas SOAP podem ser enviados: *declarado* e *não declarada*. Declarado falhas de SOAP são aquelas em que uma operação tem um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atributo que especifica um tipo personalizado de falhas SOAP. *Não declarado* falhas de SOAP não são especificadas no contrato para uma operação.  
  
 É altamente recomendável que as operações do serviço declaram suas falhas usando o <xref:System.ServiceModel.FaultContractAttribute> atributo formalmente especificar todas as falhas de SOAP que um cliente pode esperar receber no curso normal de uma operação. Também é recomendável que você retorna de uma falha de SOAP apenas as informações que um cliente precisa saber para minimizar a divulgação de informações.  
  
 Normalmente, os serviços (e os clientes duplex) execute as seguintes etapas para se integrar com êxito em seus aplicativos de tratamento de erros:  
  
-   Condições de exceção são mapeados para as falhas SOAP personalizadas.  
  
-   Os clientes e serviços enviar e recebem falhas SOAP como exceções.  
  
 Além disso, serviços e clientes do WCF podem usar as falhas de soap não declarado para fins de depuração e podem estender o comportamento de erro padrão. As seções a seguir discutem esses conceitos e tarefas.  
  
## <a name="map-exceptions-to-soap-faults"></a>Mapear exceções para falhas de SOAP  
 A primeira etapa na criação de uma operação que manipula condições de erro é decidir em quais condições um aplicativo cliente deve ser informado sobre os erros. Algumas operações ter condições de erro específicas para sua funcionalidade. Por exemplo, um `PurchaseOrder` operação deverá retornar informações específicas para os clientes que não são permitidos para iniciar uma ordem de compra. Em outros casos, como um `Calculator` de serviço, um mais geral `MathFault` falha de SOAP pode ser capaz de descrever todas as condições de erro em um serviço inteiro. Depois que as condições de erro de clientes do seu serviço são identificadas, uma falha SOAP personalizada pode ser criada e a operação pode ser marcada como de retorno dessa falha SOAP quando surge da sua condição de erro correspondente.  
  
 Para obter mais informações sobre esta etapa de desenvolvimento de seu serviço ou cliente, consulte [definindo e especificando falhas](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Os clientes e serviços lidar com falhas de SOAP como exceções  
 Identificar as condições de erro de operação, definindo as falhas SOAP personalizadas e marcando essas operações como retornar as falhas são as primeiras etapas no bem-sucedida tratamento de erros em aplicativos do WCF. A próxima etapa é implementar corretamente o envio e recebimento dessas falhas. Normalmente serviços enviam falhas para informar os aplicativos cliente sobre condições de erro, mas os clientes duplex também podem enviar falhas de SOAP para serviços.  
  
 Para obter mais informações, consulte [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Falhas de SOAP não declarado e depuração  
 Falhas SOAP declaradas são extremamente úteis para a criação de aplicativos robustos, interoperáveis e distribuídos. No entanto, em alguns casos é útil para um serviço (ou cliente duplex) enviar uma falha de SOAP não declarada, que não é mencionado na descrição de linguagem WSDL (Web Services) para essa operação. Por exemplo, ao desenvolver um serviço, situações inesperadas podem ocorrer no qual ele é útil para depuração fins para enviar informações de volta ao cliente. Além disso, você pode definir as <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade ou o <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade `true` para permitir que clientes do WCF para obter informações sobre exceções de operação de serviço interno. Enviar falhas individuais e definir propriedades de comportamento de depuração são descritos em [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
>  Pois exceções gerenciadas podem expor informações de aplicativo interno, definindo <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` pode permitir que clientes do WCF para obter informações sobre exceções de operação de serviço interno, incluindo pessoal ou de identificação de informações confidenciais.  
>   
>  Portanto, definir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` é recomendada apenas como uma maneira de depurar temporariamente um aplicativo de serviço. Além disso, o WSDL para um método que retorna sem tratamento gerenciadas exceções dessa maneira não contém o contrato para o <xref:System.ServiceModel.FaultException%601> do tipo <xref:System.ServiceModel.ExceptionDetail>. Os clientes devem esperar a possibilidade de uma falha SOAP desconhecida (retornadas aos clientes do WCF como <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objetos) para obter as informações de depuração corretamente.  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Personalizando o tratamento de erros com IErrorHandler  
 Se você tiver requisitos especiais para personalizar a mensagem de resposta ao cliente quando ocorre uma exceção de nível de aplicativo ou executar algum processamento personalizado depois que a mensagem de resposta é retornada, implemente o <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> interface.  
  
## <a name="fault-serialization-issues"></a>Problemas de serialização de falha  
 Durante a desserialização de um contrato de falha, o WCF primeiro tenta corresponder o nome do contrato de falha da mensagem SOAP com o tipo de contrato de falha. Se ele não é possível localizar uma correspondência exata, em seguida, ele pesquisará a lista de contratos de falha disponíveis em ordem alfabética para um tipo compatível. Se dois falha contratos são tipos compatíveis (uma é uma subclasse de outro, por exemplo) o tipo errado pode ser usado para desserializar a falha. Isso ocorre apenas se o contrato de falha não especificar um nome, namespace e ação. Para evitar que esse problema ocorra, sempre totalmente qualifica contratos de falha, especificando o nome, namespace e atributos de ação. Além disso, se você tiver definido um número de contratos de falha relacionadas derivadas de uma classe base compartilhada, certifique-se de marcar os novos membros com `[DataMember(IsRequired=true)]`. Para obter mais informações sobre isso `IsRequired` atributo, consulte <xref:System.Runtime.Serialization.DataMemberAttribute>. Isso impedirá que uma classe base que está sendo um tipo compatível e forçar a falha a ser desserializado no tipo derivado correto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.FaultException>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.CommunicationException>
- <xref:System.ServiceModel.FaultContractAttribute.Action%2A>
- <xref:System.ServiceModel.FaultException.Code%2A>
- <xref:System.ServiceModel.FaultException.Reason%2A>
- <xref:System.ServiceModel.FaultCode.SubCode%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- [Definindo e especificando falhas](../../../docs/framework/wcf/defining-and-specifying-faults.md)
