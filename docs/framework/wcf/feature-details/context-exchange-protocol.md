---
title: Protocolo de intercâmbio de contexto
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: a682b94b1ab659515e618e79230d94f57f140717
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493173"
---
# <a name="context-exchange-protocol"></a>Protocolo de intercâmbio de contexto
Esta seção descreve o protocolo de intercâmbio de contexto introduzido na versão do Windows Communication Foundation (WCF) do .NET Framework versão 3.5. Este protocolo permite que o canal do cliente aceitar um contexto fornecido por um serviço e aplicá-lo a todas as solicitações subsequentes para esse serviço enviados pela mesma instância de canal do cliente. A implementação do protocolo de troca de contexto pode usar um dos seguintes dois mecanismos para propagar contexto entre o servidor e o cliente: cookies HTTP ou um cabeçalho SOAP.  
  
 O protocolo de intercâmbio de contexto é implementado em uma camada de canal personalizado. O canal comunica-se o contexto de e para a camada de aplicativo usando um <xref:System.ServiceModel.Channels.ContextMessageProperty> propriedade. Para transmissão entre pontos de extremidade, o valor do contexto é serializado como um cabeçalho SOAP na camada do canal, tanto convertido de ou para as propriedades de mensagem que representam uma solicitação e resposta HTTP. No último caso, espera-se que uma das camadas de canal subjacente converte as propriedades de mensagem de solicitação e resposta HTTP para e de cookies HTTP, respectivamente. A escolha do mecanismo usado para trocar o contexto é feita usando o <xref:System.ServiceModel.Channels.ContextExchangeMechanism> propriedade o <xref:System.ServiceModel.Channels.ContextBindingElement>. Os valores válidos são `HttpCookie` ou `SoapHeader`.  
  
 No cliente, uma instância de um canal pode operar em dois modos com base nas configurações de propriedade do canal, <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Modo 1: Gerenciamento de contexto do canal  
 Este é o modo padrão onde <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> é definido como `true`. Nesse modo, o canal de contexto gerencia o contexto e armazena em cache o contexto durante seu ciclo de vida. Contexto pode ser recuperado do canal por meio da propriedade de canal `IContextManager` chamando o `GetContext` método. O canal também pode ser inicializado previamente com contexto específico antes de serem abertas ao chamar o `SetContext` método na propriedade de canal. Depois que o canal é inicializado com o contexto não pode ser redefinido.  
  
 A seguir está uma lista de constantes nesse modo:  
  
-   Qualquer tentativa de redefinir o contexto usando `SetContext` depois que o canal foi aberta gera uma <xref:System.InvalidOperationException>.  
  
-   Qualquer tentativa de enviar o contexto usando o <xref:System.ServiceModel.Channels.ContextMessageProperty> em uma mensagem de saída gera um <xref:System.InvalidOperationException>.  
  
-   Se uma mensagem é recebida do servidor com um contexto específico, quando o canal já foi inicializado com um contexto específico, isso resulta em um <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    >  É apropriado receber um contexto inicial do servidor somente se o canal é aberto sem qualquer contexto definido explicitamente.  
  
-   O <xref:System.ServiceModel.Channels.ContextMessageProperty> na mensagem de entrada é sempre null.  
  
## <a name="mode-2-application-context-management"></a>Modo 2: Gerenciamento de contexto de aplicativo  
 Este é o modo quando <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> é definido como `false`. Nesse modo o canal de contexto não gerencia o contexto. É responsabilidade do aplicativo para recuperar, gerenciar e aplicar o contexto usando o <xref:System.ServiceModel.Channels.ContextMessageProperty>. Qualquer tentativa de chamar `GetContext` ou `SetContext` resulta em um <xref:System.InvalidOperationException>.  
  
 Não importa qual modo é escolhida a fábrica de canais do cliente oferece suporte a <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, e <xref:System.ServiceModel.Channels.IDuplexSessionChannel> padrões de troca de mensagens.  
  
 Sobre o serviço, uma instância do canal é responsável por converter o contexto fornecido pelo cliente em mensagens de entrada para o <xref:System.ServiceModel.Channels.ContextMessageProperty>. A propriedade de mensagem, em seguida, pode ser acessada pela camada de aplicativo ou outros canais mais acima na pilha de chamadas. Os canais de serviço também permitem que a camada de aplicativo especificar um novo valor de contexto para ser propagadas de volta para o cliente, anexando um <xref:System.ServiceModel.Channels.ContextMessageProperty> à mensagem de resposta. Essa propriedade é convertida para o cabeçalho SOAP ou um cookie HTTP que contém o contexto, que depende da configuração da associação. O ouvinte de canal de serviço oferece suporte <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>, e <xref:System.ServiceModel.Channels.IReplySessionChannel> padrões de troca de mensagens.  
  
 O protocolo de intercâmbio de contexto apresenta um novo `wsc:Context` cabeçalho SOAP para representar as informações de contexto quando cookies HTTP não são usados para propagar o contexto. O esquema de cabeçalho de contexto permite que qualquer número de elementos filho, cada um com uma chave de cadeia de caracteres e conteúdo de cadeia de caracteres. Este é um exemplo de um cabeçalho de contexto.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Quando estiver no `HttpCookie` modo, os cookies são definidos usando o `SetCookie` cabeçalho. O nome do cookie é `WscContext`. O valor do cookie é Base64 codificação do `wsc:Context` cabeçalho. Esse valor está entre aspas.  
  
 O valor de contexto deve ser protegido contra modificações enquanto protegidos em trânsito pela mesma razão cabeçalhos WS-Addressing – o cabeçalho é usado para determinar onde expedir a solicitação no serviço. O `wsc:Context` cabeçalho, portanto, é necessário ser digitalmente assinados ou assinado e criptografado no nível de transporte ou SOAP quando a associação oferece o recurso de proteção de mensagem. Quando HTTP cookies são usados para propagar o contexto, eles devem ser protegidos usando a segurança de transporte.  
  
 Pontos de extremidade de serviço que requer suporte para o protocolo de intercâmbio de contexto podem tornar explícita na política publicada. Duas novas declarações de política foram introduzidas para representar o requisito para o cliente para suportar o protocolo de intercâmbio de contexto no nível de SOAP ou para habilitar o suporte de cookie HTTP. Geração dessas declarações para a diretiva do serviço é controlada pelo valor da <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> propriedade da seguinte maneira:  
  
-   Para <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, a declaração a seguir é gerada:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
-   Para <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, a declaração a seguir é gerada:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Guia de interoperabilidade de protocolos de serviços Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
