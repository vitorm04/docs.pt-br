---
title: Visão geral de associações do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: 38661c2ca0e3329f508e2740dfcdf69c0d5e4105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communication-foundation-bindings-overview"></a>Visão geral de associações do Windows Communication Foundation
Associações são objetos que são usados para especificar os detalhes de comunicação que são necessárias para se conectar ao ponto de extremidade de um serviço do Windows Communication Foundation (WCF). Cada ponto de extremidade em um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço requer uma associação a ser bem especificado. Este tópico descreve os tipos dos detalhes de comunicação que definem as associações, elementos de uma associação que associações são incluídas no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], e como uma associação pode ser especificada para um ponto de extremidade.  
  
## <a name="what-a-binding-defines"></a>O que define uma associação  
 As informações em uma associação podem ser muito complexa ou muito básica. A associação mais básica especifica somente o protocolo de transporte (como HTTP) que deve ser usado para se conectar ao ponto de extremidade. Geralmente, as informações que contém uma associação sobre como se conectar a um ponto de extremidade se enquadra em uma das categorias a seguir.  
  
 Protocolos  
 Determina o mecanismo de segurança que está sendo usado: o recurso de mensagens confiável ou configurações de fluxo do contexto de transação.  
  
 Codificando  
 Determina a codificação de mensagens (por exemplo, texto ou binário).  
  
 Transporte  
 Determina o protocolo de transporte subjacente para usar (por exemplo, TCP ou HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Os elementos de uma associação  
 Uma associação basicamente consiste em uma pilha ordenada de elementos de associação de cada um deles especifica parte das informações de comunicação necessárias para conectar a um ponto de extremidade de serviço. As duas camadas mais baixas na pilha são necessários. Na base da pilha é o elemento de associação de transporte e acima isso é o elemento que contém as especificações de codificação de mensagem. Os elementos de associação opcional que especifica os outros protocolos de comunicação são colocadas em camadas acima desses dois elementos necessários. Para obter mais informações sobre esses elementos de associação e a ordem correta, consulte [personalizado associações](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 As informações em uma associação podem ser complexas, e algumas configurações podem não ser compatíveis com outras pessoas. Por esse motivo, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclui um conjunto de associações fornecidas pelo sistema. Essas associações são projetadas para cobrir a maioria dos requisitos do aplicativo. As classes a seguir representam alguns exemplos de associações fornecidas pelo sistema:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Um protocolo HTTP adequado para se conectar a serviços Web de associação que é compatível com o WS-I especificação de perfil básico (por exemplo, a serviços baseados em serviços da Web do ASP.NET).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Uma associação interoperável adequada para se conectar a pontos de extremidade que estão em conformidade com o WS-* protocolos.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Usa o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] para se conectar a outros [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pontos de extremidade no mesmo computador.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Usa o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] criar conexões de mensagem na fila com outros [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pontos de extremidade.  
  
 Para obter uma lista completa, com descrições de todas as [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-fornecido associações, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Usando seus próprio associações  
 Se nenhuma das associações fornecidas pelo sistema incluídas tiver a combinação certa de recursos que requer um aplicativo de serviço, você pode criar sua própria associação. Há duas formas de fazer isso. Você pode criar uma nova associação de pré-existente em elementos de associação usando um <xref:System.ServiceModel.Channels.CustomBinding> objeto ou você pode criar uma associação completamente definido pelo usuário derivando de <xref:System.ServiceModel.Channels.Binding> associação. Para obter mais informações sobre como criar sua própria associação usando estas duas abordagens, consulte [personalizado associações](../../../docs/framework/wcf/extending/custom-bindings.md) e [Criando associações](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Usando associações  
 Usando associações envolve duas etapas básicas:  
  
1.  Selecione ou definir uma associação. O método mais fácil é escolher uma das associações fornecidas pelo sistema incluídas com [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e usá-lo com as configurações padrão. Você também pode escolher uma associação fornecida pelo sistema e redefinir seus valores de propriedade para atender às suas necessidades. Como alternativa, você pode criar uma associação personalizada ou uma associação definida pelo usuário para que os níveis mais altos de controle e personalização.  
  
2.  Crie um ponto de extremidade que usa a associação selecionada ou definido.  
  
## <a name="code-and-configuration"></a>Código e configuração  
 Você pode definir associações de duas maneiras: por meio de código ou por meio da configuração. Essas duas abordagens não dependem de se você estiver usando uma associação fornecida pelo sistema ou uma associação personalizada. Em geral, usando o código oferece total controle sobre a definição de uma associação em tempo de design. Usando a configuração, por outro lado, permite que um administrador do sistema ou o usuário de um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço ou cliente para alterar os parâmetros de ligação sem ter que recompilar o aplicativo de serviço. Essa flexibilidade geralmente é desejável, porque não há nenhuma maneira de prever os requisitos específicos do computador no qual um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo é implantado. Informações de manter a associação (e o endereçamento) sem o código permite que a alteração sem a necessidade de recompilação ou reimplantação do aplicativo. Observe que associações definidas em código são criadas após associações especificadas na configuração, permitindo que as associações de código definido substituir a configuração definida associações.  
  
## <a name="see-also"></a>Consulte também  
 [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
