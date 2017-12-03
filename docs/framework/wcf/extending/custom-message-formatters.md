---
title: Custom Message Formatters
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 413adbc25e2f92ae2e989290685db6dfeaf58368
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-message-formatters"></a>Custom Message Formatters
O conteúdo em uma mensagem é geralmente na forma de XML, geralmente que não é um formato conveniente para um aplicativo. Aplicativos manipulam objetos, obtendo e definindo suas propriedades. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usa o *contrato de dados* para converter um <xref:System.ServiceModel.Channels.Message> objeto em um objeto facilmente manipulado por um aplicativo. Esses processos são chamados de serialização e desserialização. Observe que esses mesmos termos são usados para descrever a serialização e desserialização feito pela camada de transporte de e para o formato de transmissão de mensagem, que é um processo relacionado.  
  
 Você pode usar um formatador de mensagem personalizada se você precisa implementar uma conversão especializada entre as mensagens e os objetos que não podem ser realizadas por meio de um contrato de dados. Fazer isso, modificar ou estender o comportamento de execução de uma operação em um cliente ou um serviço.  
  
## <a name="custom-message-formatters-on-the-client"></a>Formatadores de mensagem personalizado no cliente  
 O <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface define os métodos que são usados para controlar a conversão de mensagens em objetos e em mensagens para aplicativos cliente.  
  
 Você deve implementar essa interface. Substituir pela primeira vez o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> método para desserializar uma mensagem. Este método é chamado após uma mensagem de entrada é recebida, mas antes que ele é enviado para a operação de cliente.  
  
 Em seguida, substituir o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> método para serializar um objeto. Este método é chamado antes de enviar uma mensagem de saída.  
  
 Para inserir o formatador personalizado para o aplicativo de serviço, atribuir o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> o objeto para o <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> propriedade usando o comportamento de uma operação. Para obter informações sobre comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Mensagem personalizada de formatadores do serviço  
 O <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface define métodos que convertem um <xref:System.ServiceModel.Channels.Message> objeto nos parâmetros de uma operação e de parâmetros em um <xref:System.ServiceModel.Channels.Message> objeto em um aplicativo de serviço.  
  
 Você deve implementar essa interface. Substituir pela primeira vez o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> método para desserializar uma mensagem. Este método é chamado após uma mensagem de entrada é recebida, mas antes que ele é enviado para a operação de cliente.  
  
 Em seguida, substituir o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> método para serializar um objeto. Este método é chamado antes de enviar uma mensagem de saída.  
  
 Para inserir o formatador personalizado para o aplicativo de serviço, atribuir o <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> o objeto para o <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> propriedade usando o comportamento de uma operação. Para obter informações sobre comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
