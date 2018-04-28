---
title: Tratamento de erros do WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b85ef2b0c077b67cc341a48c9260393e158033c5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="wcf-error-handling"></a>Tratamento de erros do WCF
Os erros encontrados por um aplicativo WCF pertencem a um dos três grupos:  
  
1.  Erros de comunicação  
  
2.  Erros de canal/proxy  
  
3.  Erros de aplicativo  
  
 Erros de comunicação ocorrem quando uma rede não estiver disponível, um cliente usa um endereço incorreto ou o host de serviço não está escutando para mensagens de entrada. Os erros desse tipo são retornados ao cliente como <xref:System.ServiceModel.CommunicationException> ou <xref:System.ServiceModel.CommunicationException>-classes derivadas.  
  
 Erros de canal/proxy são erros que ocorrem dentro do canal ou o próprio proxy. Os erros desse tipo incluem: tentativa de usar um proxy ou canal que foi fechado, existe uma incompatibilidade de contrato entre o cliente e o serviço ou as credenciais do cliente são rejeitadas pelo serviço. Há muitos tipos diferentes de erros nesta categoria, muitos para listar aqui. Os erros desse tipo são retornados ao cliente como-é (Nenhuma transformação é executada nos objetos de exceção).  
  
 Erros de aplicativo ocorrem durante a execução de uma operação de serviço. Os erros desse tipo são enviados ao cliente como <xref:System.ServiceModel.FaultException> ou <xref:System.ServiceModel.FaultException%601>.  
  
 Tratamento de erros em WCF é executado por um ou mais dos seguintes:  
  
-   Manipulando diretamente a exceção é gerada. Isso é feito apenas para comunicação e erros de canal/proxy.  
  
-   Usando contratos de falha  
  
-   Implementando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface  
  
-   Tratamento <xref:System.ServiceModel.ServiceHost> eventos  
  
## <a name="fault-contracts"></a>Contratos de falha  
 Contratos de falha permitem que você defina os erros que podem ocorrer durante a operação de serviço em uma plataforma de maneira independente. Por padrão, todas as exceções lançadas a partir de uma operação de serviço serão retornadas ao cliente como um <xref:System.ServiceModel.FaultException> objeto. O <xref:System.ServiceModel.FaultException> objeto conterá informações muito pouco. Você pode controlar as informações enviadas para o cliente definir um contrato de falha e retornando o erro como uma <xref:System.ServiceModel.FaultException%601>. Para obter mais informações, consulte [especificando e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 O <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface permite a você mais controle sobre como seu aplicativo WCF responde a erros.  Isso lhe dá controle total sobre a mensagem de falha é retornada ao cliente e permite que você execute o processamento, como o log de erro personalizada.  [!INCLUDE[crdefault](../../../includes/crabout-md.md)] <xref:System.ServiceModel.Dispatcher.IErrorHandler> e [controle estendido através de tratamento de erros e emissão de relatórios](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>Eventos do ServiceHost  
 O <xref:System.ServiceModel.ServiceHost> classe hospeda serviços e define vários eventos que podem ser necessárias para tratamento de erros. Por exemplo:  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 Para obter mais informações, consulte <xref:System.ServiceModel.ServiceHost>.
