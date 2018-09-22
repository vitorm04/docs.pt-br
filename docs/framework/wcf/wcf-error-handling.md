---
title: Tratamento de erros do WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 4fad317d8cb696b29d9c8e4e4d8209abc28410f8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580480"
---
# <a name="wcf-error-handling"></a>Tratamento de erros do WCF
Os erros encontrados por um aplicativo WCF pertencem a um dos três grupos:  
  
1.  Erros de comunicação  
  
2.  Erros de canal/proxy  
  
3.  Erros de aplicativo  
  
 Erros de comunicação ocorrem quando uma rede não está disponível, um cliente usa um endereço incorreto ou o host de serviço não está escutando para mensagens de entrada. Os erros desse tipo são retornados ao cliente como <xref:System.ServiceModel.CommunicationException> ou <xref:System.ServiceModel.CommunicationException>-as classes derivadas.  
  
 Erros de canal/proxy são erros que ocorrem dentro do próprio proxy ou do canal. Os erros desse tipo incluem: tentativa de usar um proxy ou de canal que foi fechado, existe uma incompatibilidade de contrato entre o cliente e o serviço ou as credenciais do cliente são rejeitadas pelo serviço. Há muitos tipos diferentes de erros nesta categoria, muitos para listar aqui. Os erros desse tipo são retornados ao cliente como-está (Nenhuma transformação é executada em objetos de exceção).  
  
 Erros de aplicativo ocorrem durante a execução de uma operação de serviço. Erros desse tipo são enviados ao cliente tão <xref:System.ServiceModel.FaultException> ou <xref:System.ServiceModel.FaultException%601>.  
  
 Tratamento de erro no WCF é executado por um ou mais das seguintes opções:  
  
-   Tratamento de exceção gerada diretamente. Isso é feito apenas para a comunicação e erros de canal/proxy.  
  
-   Usando contratos de falha  
  
-   Implementando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface  
  
-   Tratamento <xref:System.ServiceModel.ServiceHost> eventos  
  
## <a name="fault-contracts"></a>Contratos de falha  
 Contratos de falha permitem que você defina os erros que podem ocorrer durante a operação de serviço em uma plataforma de maneira independente. Por padrão, todas as exceções geradas de dentro de uma operação de serviço serão retornadas ao cliente como um <xref:System.ServiceModel.FaultException> objeto. O <xref:System.ServiceModel.FaultException> objeto conterá informações muito pouco. Você pode controlar as informações enviadas para o cliente definir um contrato de falha e retornando o erro, pois um <xref:System.ServiceModel.FaultException%601>. Para obter mais informações, consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 O <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface permite que você mais controle sobre como o aplicativo WCF responde a erros.  Ele lhe dá controle total sobre a mensagem de falha que é retornada ao cliente e permite que você realize processamento, como registro em log de erro personalizado.  Para obter mais informações sobre <xref:System.ServiceModel.Dispatcher.IErrorHandler> e [estendendo o controle sobre o tratamento de erros e emissão de relatórios](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>Eventos de ServiceHost  
 O <xref:System.ServiceModel.ServiceHost> hospeda serviços de classe e define vários eventos que podem ser necessárias para tratamento de erros. Por exemplo:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Para obter mais informações, consulte <xref:System.ServiceModel.ServiceHost>.
