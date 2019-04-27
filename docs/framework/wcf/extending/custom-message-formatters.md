---
title: Custom Message Formatters
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: af1596c65fc87a68bc3dc2ab5ab2d82133e0fed4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857968"
---
# <a name="custom-message-formatters"></a>Custom Message Formatters
O conteúdo em uma mensagem é geralmente na forma de XML, geralmente, que não é um formato conveniente para um aplicativo. Aplicativos manipulam objetos, obter e definir suas propriedades. Windows Communication Foundation (WCF) usa o *contrato de dados* para converter um <xref:System.ServiceModel.Channels.Message> objeto em um objeto facilmente manipulado por um aplicativo. Esses processos são chamados de serialização e desserialização. Observe que esses mesmos termos são usados para descrever a serialização e desserialização feita pela camada de transporte de e para o formato de transmissão de mensagem, que é um processo não relacionado.  
  
 Você pode usar um formatador de mensagem personalizada se você precisar implementar uma conversão especializada entre as mensagens e objetos que você não pode realizar por meio de um contrato de dados. Fazer isso, modificar ou estender o comportamento de execução de uma operação em um cliente ou um serviço.  
  
## <a name="custom-message-formatters-on-the-client"></a>Formatadores de mensagem personalizada no cliente  
 O <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface define métodos que são usados para controlar a conversão de mensagens em objetos e em mensagens para aplicativos cliente.  
  
 Você deve implementar essa interface. Substituir pela primeira vez o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> método para desserializar uma mensagem. Este método é chamado depois que uma mensagem de entrada é recebida, mas antes que ela seja expedida para a operação do cliente.  
  
 Em seguida, substituir o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> método para serializar um objeto. Esse método é chamado antes de enviar uma mensagem de saída.  
  
 Para inserir o formatador personalizado no aplicativo de serviço, atribuir a <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> do objeto para o <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> propriedade usando um comportamento de operação. Para obter informações sobre comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Formatadores de mensagem personalizado no serviço  
 O <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface define métodos que convertem um <xref:System.ServiceModel.Channels.Message> objeto em parâmetros para uma operação e de parâmetros em um <xref:System.ServiceModel.Channels.Message> objeto em um aplicativo de serviço.  
  
 Você deve implementar essa interface. Substituir pela primeira vez o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> método para desserializar uma mensagem. Este método é chamado depois que uma mensagem de entrada é recebida, mas antes que ela seja expedida para a operação do cliente.  
  
 Em seguida, substituir o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> método para serializar um objeto. Esse método é chamado antes de enviar uma mensagem de saída.  
  
 Para inserir o formatador personalizado no aplicativo de serviço, atribuir a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> do objeto para o <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> propriedade usando um comportamento de operação. Para obter informações sobre comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
