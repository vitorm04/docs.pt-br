---
title: Introdução à extensibilidade
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 991c3879990fd5b6562a2270c65e1560efadc022
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="introduction-to-extensibility"></a>Introdução à extensibilidade
O [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] modelo de aplicativo é projetado para resolver a maior parte dos requisitos de comunicação de qualquer aplicativo distribuído. Mas sempre há cenários em que o modelo de aplicativo padrão e implementações de fornecido pelo sistema não têm suporte. O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de extensibilidade destina-se para dar suporte a cenários personalizados, permitindo que você modificar o comportamento do sistema em cada nível, até mesmo para o ponto de substituir o modelo de aplicativo inteiro. Este tópico descreve as várias áreas de extensão e aponta para obter mais informações sobre cada um.  
  
## <a name="areas-to-extend"></a>Áreas para estender  
 Você pode estender:  
  
-   O tempo de execução do aplicativo. Isso estende a distribuição e o processamento de mensagens para o aplicativo. Essa área também inclui estender o sistema de segurança, o sistema de metadados, o sistema de serialização e as associações e elementos que se conectam o aplicativos com o sistema de canais subjacente de associação.  
  
-   O canal e o tempo de execução do canal. Isso estende o sistema que funciona no nível da mensagem, fornecendo o protocolo de transporte e suporte a codificação.  
  
-   O tempo de execução do host. Isso estende a relação entre o domínio de aplicativo de hospedagem para o tempo de execução do aplicativo e de canal.  
  
### <a name="extending-the-application-runtime"></a>Estendendo o tempo de execução do aplicativo  
 Em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos, há uma distinção entre as mensagens destinadas a um canal correspondente e que são destinados para o aplicativo em si. Mensagens do canal de suportam a algumas funcionalidades relacionadas de canal, como estabelecer uma conversa segura ou estabelecer uma sessão confiável. Essas mensagens não estão disponíveis para o tempo de execução do aplicativo; eles são processados antes que a camada de aplicativo está envolvida.  
  
 As mensagens de aplicativo contém dados que são destinados a um cliente ou operação de serviço que você ou seu cliente tiver sido criado. Essas mensagens estão disponíveis para o sistema de extensão do nível do aplicativo no formato de mensagem ou de objeto, dependendo das suas necessidades.  
  
 Todas as mensagens passam por meio do sistema de canal. somente as mensagens de aplicativo são passadas do sistema de canal para o aplicativo. Para criar a nova funcionalidade no nível do canal, você deve estender o sistema de canal. Para criar a nova funcionalidade no nível do aplicativo, você deve estender o tempo de execução do serviço ou cliente (distribuidores e fábricas de canais, respectivamente). Para obter mais informações sobre como estender o tempo de execução do aplicativo, consulte [estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Segurança estendida  
 Para criar os mecanismos de segurança personalizada, como tokens e credenciais, você deve estender o sistema de segurança. Para obter mais informações, consulte [estendendo segurança](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Estendendo metadados  
 Para expor seus metadados em diferente do padrão, você deve estender o sistema de metadados. Para obter mais informações, consulte [estendendo o sistema de metadados](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Estendendo a serialização  
 Para construir decodificadores personalizados, fornecer substitutos de dados ou outras tarefas que envolvem a personalização de dados transferidos, você deve estender o sistema de serialização. Para obter mais informações, consulte [estendendo codificadores e serializadores](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Estendendo associações  
 Para associar os canais de transporte ou protocolo da camada de aplicativo, você deve estender o sistema de associação. Para obter mais informações, consulte [estendendo associações](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Estendendo o sistema de canal  
 Para criar canais que oferecem suporte a transportes personalizados ou funcionalidade de protocolo, consulte [estendendo a camada do canal](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Estendendo o serviço de sistema de hospedagem  
 Para modificar o modelo de aplicativo de todo o serviço, você deve estender <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> classe. Para obter mais informações, consulte [estendendo ServiceHost e a camada de modelo de serviço](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Para modificar a relação entre o domínio de aplicativo de hospedagem e o host de serviço, você deve estender o <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classe. Para obter mais informações, consulte [estendendo hospedagem usando ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o WCF](../../../docs/framework/wcf/extending/index.md)
