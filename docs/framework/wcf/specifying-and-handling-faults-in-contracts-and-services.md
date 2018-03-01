---
title: "Especificando e lidando com falhas em contratos e serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57fc01b77379389ca4d86d241ec8f3d672b519b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Especificando e lidando com falhas em contratos e serviços
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]aplicativos de lidar com situações de erro, mapeando os objetos de exceção gerenciada para objetos de falhas SOAP e objetos de falhas SOAP em objetos de exceção gerenciada. Os tópicos nesta seção abordam como criar contratos para expor o erro condições como falhas de SOAP personalizadas, como retornar essas falhas como parte da implementação de serviço e como os clientes capturar essas falhas.  
  
## <a name="error-handling-overview"></a>Visão geral de manipulação de erro  
 Em todos os aplicativos gerenciados, os erros de processamento são representados por <xref:System.Exception> objetos. Em aplicativos baseados em SOAP como [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos, métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento. Falhas de SOAP são tipos de mensagem que estão incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar sua operação mais robusta ou interativo. Além disso, como falhas de SOAP são demonstradas para clientes em formato XML, é um sistema de tipo altamente interoperável que os clientes em qualquer plataforma SOAP podem usar, aumentando o alcance de sua [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo.  
  
 Como [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] os aplicativos executados em ambos os tipos de sistemas de erro, qualquer informação de exceção gerenciada que é enviada para o cliente deve ser convertida de exceções em falhas de SOAP do serviço, enviada e convertida de falhas de SOAP em exceções de falha em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] clientes. No caso de clientes duplex, contratos com o cliente também podem enviar falhas de SOAP para um serviço. Em ambos os casos, você pode usar os comportamentos de exceção de serviço padrão, ou você pode controlar explicitamente se — e como — exceções são mapeadas para mensagens de falha.  
  
 Dois tipos de falhas de SOAP podem ser enviados: *declarado* e *não declarada*. Declarado falhas de SOAP são aquelas em que uma operação tem um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atributo que especifica um tipo personalizado de falhas SOAP. *Não declarada* falhas de SOAP não são especificadas no contrato para uma operação.  
  
 É altamente recomendável que as operações de serviço declaram suas falhas usando o <xref:System.ServiceModel.FaultContractAttribute> atributo formalmente especificar todas as falhas SOAP que um cliente pode esperar receber no curso normal de uma operação. Também é recomendável que retornar de uma falha de SOAP apenas as informações que um cliente precisa saber para minimizar a divulgação de informações.  
  
 Normalmente, os serviços (e clientes duplex) siga estas etapas para integrar com êxito em seus aplicativos de tratamento de erros:  
  
-   Mapear condições de exceção para falhas de SOAP personalizadas.  
  
-   Os clientes e serviços de envio e recebem de falhas de SOAP como exceções.  
  
 Além disso, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] clientes e serviços podem usar falhas de soap não declarado para fins de depuração e pode estender o comportamento de erro padrão. As seções a seguir discutem esses conceitos e tarefas.  
  
## <a name="map-exceptions-to-soap-faults"></a>Mapear exceções para falhas de SOAP  
 A primeira etapa na criação de uma operação que manipula condições de erro é decidir em quais condições, um aplicativo cliente deve ser informado sobre erros. Algumas operações tem condições de erro específicas para sua funcionalidade. Por exemplo, um `PurchaseOrder` operação pode retornar informações específicas para clientes que não têm permissão para iniciar uma ordem de compra. Em outros casos, como um `Calculator` de serviço mais geral `MathFault` falha de SOAP pode ser capaz de descrever todas as condições de erro em todo o serviço. Depois que as condições de erro de clientes do serviço são identificadas, uma falha SOAP personalizada pode ser criada e a operação pode ser marcada como retornando essa falha SOAP quando surge sua condição de erro correspondente.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Esta etapa do desenvolvimento de seu serviço ou cliente, consulte [definindo e especificando falhas](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Os clientes e serviços de lidar com falhas de SOAP como exceções  
 Identificação de condições de erro de operação, definindo as falhas de SOAP personalizadas e marcando essas operações como retornando as falhas são as primeiras etapas no bem-sucedida tratamento de erros em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos. A próxima etapa é implementar corretamente o envio e recebimento dessas falhas. Normalmente serviços enviar falhas para informar os aplicativos cliente sobre condições de erro, mas duplex clientes também podem enviar a falhas de SOAP para serviços.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Falhas de SOAP não declarado e depuração  
 Falhas de SOAP declaradas são extremamente úteis para a criação de aplicativos distribuídos, interoperáveis robustos. No entanto, em alguns casos é útil para um serviço (ou cliente duplex) enviar uma falha de SOAP não declarada, que não é mencionado no WSDL Web Services Description Language () para essa operação. Por exemplo, ao desenvolver um serviço, situações inesperadas podem ocorrer nos quais é útil para depuração para enviar informações de volta ao cliente. Além disso, você pode definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade ou o <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> propriedade `true` para permitir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] clientes para obter informações sobre exceções de operação de serviço interno. As falhas individuais de envio e definir propriedades de comportamento de depuração são descritas na [enviando e recebendo falhas](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
>  Definir como exceções gerenciadas podem expor informações do aplicativo interno, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` pode permitir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] clientes para obter informações sobre exceções de operação de serviço interno, incluindo informações confidenciais ou de identificação pessoal.  
>   
>  Portanto, definir <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> para `true` é recomendada apenas como uma maneira de temporariamente depurar um aplicativo de serviço. Além disso, o WSDL para um método que retorna sem tratamento gerenciados exceções dessa maneira não contém o contrato para o <xref:System.ServiceModel.FaultException%601> do tipo <xref:System.ServiceModel.ExceptionDetail>. Os clientes devem esperar a possibilidade de uma falha de SOAP desconhecida (retornado para [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] clientes como <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objetos) para obter as informações de depuração corretamente.  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Personalizando o tratamento de erros com IErrorHandler  
 Se você tiver requisitos especiais para personalizar a mensagem de resposta ao cliente quando ocorre uma exceção de nível de aplicativo ou executar algum processamento personalizado depois que a mensagem de resposta é retornada, implemente o <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> interface.  
  
## <a name="fault-serialization-issues"></a>Problemas de serialização de falhas  
 Durante a desserialização de um contrato de falha, o WCF primeiro tenta corresponder ao nome de contrato de falha na mensagem SOAP com o tipo de contrato de falha. Se ele não encontrar uma correspondência exata, em seguida, ele irá procurar a lista de contratos de falha disponível em ordem alfabética por um tipo compatível. Se duas falhas contratos são tipos compatíveis (um é uma subclasse de outro, por exemplo) do tipo incorreto pode ser usado para desserializar a falha. Isso ocorre apenas se o contrato de falha não especificar um nome, um namespace e uma ação. Para evitar que esse problema ocorra, sempre totalmente qualificados contratos de falha, especificando o nome, namespace e atributos de ação. Além disso, se você tiver definido um número de contratos de falha relacionadas derivadas de uma classe base compartilhada, certifique-se de marcar quaisquer novos membros com `[DataMember(IsRequired=true)]`. Para obter mais informações sobre esse `IsRequired` atributo, consulte <xref:System.Runtime.Serialization.DataMemberAttribute>. Isso impedirá uma classe base de ser um tipo compatível e forçar a falha ser desserializado no tipo derivado correto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.CommunicationException>  
 <xref:System.ServiceModel.FaultContractAttribute.Action%2A>  
 <xref:System.ServiceModel.FaultException.Code%2A>  
 <xref:System.ServiceModel.FaultException.Reason%2A>  
 <xref:System.ServiceModel.FaultCode.SubCode%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 [Definindo e especificando falhas](../../../docs/framework/wcf/defining-and-specifying-faults.md)
