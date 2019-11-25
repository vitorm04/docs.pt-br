---
title: Como proteger mensagens em sessões confiáveis
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: edff27fe9649387c1922c34e72ef59d615e52b90
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141669"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Como proteger mensagens em sessões confiáveis

Este tópico descreve as etapas necessárias para habilitar a segurança em nível de mensagem para mensagens trocadas em uma sessão confiável usando uma das associações fornecidas pelo sistema que dão suporte a essa sessão, mas não por padrão. Habilite uma sessão segura e confiável de forma imperativa usando código ou declarativamente no arquivo de configuração. Este procedimento usa os arquivos de configuração de cliente e serviço para habilitar a sessão segura e confiável.

Esse procedimento consiste nas seguintes três tarefas principais:

1. Especifique que o cliente e o serviço trocam mensagens em uma sessão confiável.

1. Exigir segurança em nível de mensagem na sessão confiável.

1. Especifique o tipo de credencial do cliente que o cliente deve usar para ser autenticado com o serviço.

É importante na primeira tarefa que o elemento de configuração do ponto de extremidade contém um atributo `bindingConfiguration` que faz referência a uma configuração de associação chamada (neste exemplo) `MessageSecurity`. O [ **\<associação >** ](../../configure-apps/file-schema/wcf/bindings.md) elemento de configuração, em seguida, faz referência a esse nome para habilitar sessões confiáveis, definindo o atributo `enabled` do elemento [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) como `true`. Você pode exigir que as garantias de entrega ordenadas estejam disponíveis em uma sessão confiável definindo o atributo `ordered` como `true`.

Para a cópia de origem do exemplo no qual esse procedimento de configuração se baseia, consulte a [sessão confiável do WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Os itens essenciais da segunda tarefa são realizados com a definição do atributo `mode` do elemento **\<security >** contido no elemento **> de associação\<** do cliente e do serviço como `Message`.

Os itens essenciais da terceira tarefa são realizados com a definição do atributo `clientCredentialType` do elemento **\<message >** contido no elemento **\<Security >** do cliente e do serviço como `Certificate`.

> [!NOTE]
> Ao usar a segurança de mensagem com sessões confiáveis, o sistema de mensagens confiável tenta autenticar um cliente não autenticado até que ocorra um tempo limite em vez de lançar uma exceção na primeira falha.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurar o serviço com uma WSHttpBinding para usar uma sessão confiável

Este procedimento é descrito em [como trocar mensagens em uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurar o cliente com um WSHttpBinding para usar uma sessão confiável

Este procedimento é descrito em [como trocar mensagens em uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Definir o modo e ClientCredentialtype na configuração

1. Adicione um elemento Binding apropriado ao elemento [ **\<bindings >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração. O exemplo a seguir adiciona um elemento [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .

1. Adicione um elemento de **> de associação de\<** e defina seu atributo `name` como um valor apropriado. O exemplo usa o nome `MessageSecurity`.

1. Adicione um elemento de **> de segurança\<** e defina o atributo `mode` como `Message`.

1. No elemento **\<security >** , adicione um elemento **\<Message >** e defina o atributo `clientCredentialType` como `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
