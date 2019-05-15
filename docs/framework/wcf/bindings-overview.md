---
title: Visão geral de associações do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: e78616acc56e75dd06445f7a569ab94e65e20cc0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592235"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Visão geral de associações do Windows Communication Foundation
Associações são objetos que são usados para especificar os detalhes de comunicação que são necessárias para se conectar ao ponto de extremidade de um serviço do Windows Communication Foundation (WCF). Cada ponto de extremidade em um serviço WCF requer uma associação a ser bem especificado. Este tópico descreve os tipos dos detalhes de comunicação que definem as associações, os elementos de uma associação, quais associações são incluídas no WCF e como uma associação pode ser especificada para um ponto de extremidade.  
  
## <a name="what-a-binding-defines"></a>O que define uma associação  
 As informações em uma associação podem ser muito básico ou muito complexos. A associação mais básica especifica somente o protocolo de transporte (como HTTP) que deve ser usado para se conectar ao ponto de extremidade. De modo geral, as informações de que uma associação contém sobre como se conectar a um ponto de extremidade entra em uma das categorias a seguir.  
  
 Protocolos  
 Determina o mecanismo de segurança que está sendo usado: recurso de mensagens confiável ou configurações de fluxo do contexto de transação.  
  
 Codificando  
 Determina a codificação de mensagens (por exemplo, texto ou binário).  
  
 Transporte  
 Determina o protocolo de transporte subjacente usada (por exemplo, TCP ou HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Os elementos de uma associação  
 Uma associação consiste basicamente em uma pilha ordenada de elementos, de associação de cada um deles especifica parte das informações de comunicação necessárias para se conectar a um ponto de extremidade de serviço. Duas camadas mais baixas na pilha são ambos necessários. Na base da pilha é o elemento de associação de transporte e logo acima do que isso é o elemento que contém as especificações de codificação de mensagem. Os elementos de associação opcional que especifica os protocolos de comunicação são colocadas em camadas acima desses dois elementos necessários. Para obter mais informações sobre esses elementos de associação e a ordem correta, consulte [ligações personalizadas](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 As informações em uma associação podem ser complexas, e algumas configurações podem não ser compatíveis com outras pessoas. Por esse motivo, o WCF inclui um conjunto de associações fornecidas pelo sistema. Essas associações são projetadas para abranger a maioria dos requisitos do aplicativo. As classes a seguir representam alguns exemplos das associações fornecidas pelo sistema:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: Um protocolo HTTP adequado para se conectar a serviços Web de associação que está em conformidade com o WS-eu especificação do Basic Profile (por exemplo, a serviços baseados em serviços da Web do ASP.NET).  
  
- <xref:System.ServiceModel.WSHttpBinding>: Uma associação interoperável adequada para se conectar a pontos de extremidade que estão em conformidade com o WS-* protocolos.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Usa o .NET Framework para se conectar a outros pontos de extremidade do WCF no mesmo computador.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Usa o .NET Framework para criar na fila de mensagens conexões com outros pontos de extremidade do WCF.  

- <xref:System.ServiceModel.NetTcpBinding>: Esta associação oferece um desempenho mais alto que associações HTTP e é ideal para uso em uma rede local.
  
 Para obter uma lista completa, com descrições de todas as associações de fornecido com o WCF, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Usando suas próprias ligações  
 Se nenhuma das associações fornecidas pelo sistema incluídas tem a combinação certa de recursos necessários para um aplicativo de serviço, você pode criar sua própria associação. Há duas formas de fazer isso. Você pode criar uma nova associação de preexistente em elementos de associação usando um <xref:System.ServiceModel.Channels.CustomBinding> objeto ou você pode criar uma associação completamente definida pelo usuário, derivando do <xref:System.ServiceModel.Channels.Binding> associação. Para obter mais informações sobre como criar sua própria associação usando estas duas abordagens, consulte [ligações personalizadas](../../../docs/framework/wcf/extending/custom-bindings.md) e [Criando associações](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Usando associações  
 Usando associações envolve duas etapas básicas:  
  
1. Selecione ou defina uma associação. É o método mais fácil escolher uma das associações fornecidas pelo sistema incluídas com o WCF e usá-lo com suas configurações padrão. Também pode escolher uma associação fornecida pelo sistema e de redefinição de seus valores de propriedade para atender às suas necessidades. Como alternativa, você pode criar uma ligação personalizada ou uma associação definida pelo usuário ter níveis mais altos de controle e personalização.  
  
2. Crie um ponto de extremidade que usa a associação selecionada ou definido.  
  
## <a name="code-and-configuration"></a>Configuração e código  
 Você pode definir associações de duas maneiras: por meio de código ou por meio da configuração. Essas duas abordagens não dependem se você estiver usando uma associação fornecida pelo sistema ou uma associação personalizada. Em geral, usando código lhe dá controle total sobre a definição de uma associação em tempo de design. Por outro lado, usando a configuração, permite que um administrador do sistema ou o usuário de um serviço WCF ou o cliente para alterar os parâmetros de uma associação sem ter que recompilar o aplicativo de serviço. Essa flexibilidade geralmente é desejável porque não há nenhuma maneira de prever os requisitos de máquina específica em que um aplicativo WCF deve ser implantado. Manter a associação (e o endereçamento) informações fora do código permite que eles alterem os sem a necessidade de recompilação ou reimplantação do aplicativo. Observe que associações definidas em código são criadas após associações especificadas na configuração, permitindo que as associações definidas pelo código substituir todas as associações definidas por configuração.  
  
## <a name="see-also"></a>Consulte também

- [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
