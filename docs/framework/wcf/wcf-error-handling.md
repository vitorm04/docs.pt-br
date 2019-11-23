---
title: Tratamento de erros do WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 7e5c65da3fa13a3640c7a6948f1284d0c6ffdfc4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319943"
---
# <a name="wcf-error-handling"></a>Tratamento de erros do WCF
Os erros encontrados por um aplicativo WCF pertencem a um dos três grupos:  
  
1. Erros de comunicação  
  
2. Erros de proxy/canal  
  
3. Erros de aplicativo  
  
 Os erros de comunicação ocorrem quando uma rede não está disponível, um cliente usa um endereço incorreto ou o host de serviço não está escutando mensagens de entrada. Erros desse tipo são retornados ao cliente como <xref:System.ServiceModel.CommunicationException> ou classes derivadas de <xref:System.ServiceModel.CommunicationException>.  
  
 Erros de proxy/canal são erros que ocorrem dentro do canal ou proxy em si. Os erros desse tipo incluem: tentativa de usar um proxy ou canal que foi fechado, uma incompatibilidade de contrato existe entre o cliente e o serviço ou as credenciais do cliente são rejeitadas pelo serviço. Há muitos tipos diferentes de erros nessa categoria, muitas para listar aqui. Erros desse tipo são retornados ao cliente como estão (nenhuma transformação é executada nos objetos de exceção).  
  
 Erros de aplicativo ocorrem durante a execução de uma operação de serviço. Os erros desse tipo são enviados ao cliente como <xref:System.ServiceModel.FaultException> ou <xref:System.ServiceModel.FaultException%601>.  
  
 O tratamento de erros no WCF é executado por um ou mais dos seguintes:  
  
- Manipulando diretamente a exceção gerada. Isso só é feito para erros de comunicação e de proxy/canal.  
  
- Usando contratos de falha  
  
- Implementando a interface <xref:System.ServiceModel.Dispatcher.IErrorHandler>  
  
- Manipulando eventos de <xref:System.ServiceModel.ServiceHost>  
  
## <a name="fault-contracts"></a>Contratos de falha  
 Os contratos de falha permitem que você defina os erros que podem ocorrer durante a operação de serviço de forma independente de plataforma. Por padrão, todas as exceções geradas de dentro de uma operação de serviço serão retornadas ao cliente como um objeto <xref:System.ServiceModel.FaultException>. O objeto <xref:System.ServiceModel.FaultException> conterá muito pouca informação. Você pode controlar as informações enviadas ao cliente definindo um contrato de falha e retornando o erro como um <xref:System.ServiceModel.FaultException%601>. Para obter mais informações, consulte [especificando e manipulando falhas em contratos e serviços](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 A interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> permite mais controle sobre como seu aplicativo WCF responde a erros.  Ele oferece controle total sobre a mensagem de falha que é retornada ao cliente e permite que você execute o processamento de erro personalizado, como registro em log.  Para obter mais informações sobre <xref:System.ServiceModel.Dispatcher.IErrorHandler> e [estender o controle sobre tratamento de erros e relatórios](./samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>Eventos ServiceHost  
 A classe <xref:System.ServiceModel.ServiceHost> hospeda serviços e define vários eventos que podem ser necessários para lidar com erros. Por exemplo:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Para obter mais informações, consulte <xref:System.ServiceModel.ServiceHost>.
