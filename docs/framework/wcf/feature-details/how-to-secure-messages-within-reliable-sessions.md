---
title: Como proteger mensagens em sessões confiáveis
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1592c9429e6cd425b86fa2b72bfebe977e18b048
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406202"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Como proteger mensagens em sessões confiáveis

Este tópico descreve as etapas necessárias para habilitar a segurança de nível de mensagem para mensagens trocadas dentro de uma sessão confiável usando uma das associações fornecidas pelo sistema que dão suporte a essa sessão, mas não por padrão. Habilite uma sessão segura e confiável, imperativamente por meio de código ou declarativamente no arquivo de configuração. Este procedimento usa os arquivos de configuração do cliente e o serviço para habilitar a sessão segura e confiável.

Este procedimento consiste em três tarefas principais a seguir:

1. Especifique que o cliente e o serviço de trocam mensagens dentro de uma sessão confiável.

1. Exigir segurança em nível de mensagem dentro da sessão confiável.

1. Especifique o tipo de credencial de cliente que o cliente deve usar para ser autenticado com o serviço.

É importante na primeira tarefa que o elemento de configuração do ponto de extremidade contêm uma `bindingConfiguration` atributo que faz referência a uma configuração de associação chamada (neste exemplo) `MessageSecurity`. O [  **\<associação >** ](../../../../docs/framework/misc/binding.md) elemento de configuração, em seguida, faz referência a esse nome para habilitar sessões confiáveis, definindo o `enabled` atributo do [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elemento `true`. Você pode exigir que as garantias de entrega ordenada estão disponíveis dentro de uma sessão confiável, definindo o `ordered` atributo `true`.

Para a cópia do código-fonte do exemplo no qual este procedimento de configuração se baseia, consulte o [sessão confiável de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Os itens essenciais da segunda tarefa são realizados, definindo o `mode` atributo do  **\<segurança >** elemento contido no  **\<associação >** elemento do cliente e do serviço para `Message`.

Os itens essenciais da terceira tarefa são realizados, definindo o `clientCredentialType` atributo do  **\<mensagem >** elemento contido no  **\<segurança >** elemento do cliente e do serviço para `Certificate`.

> [!NOTE]
> Ao usar a segurança de mensagem com sessões confiáveis, sistema de mensagens confiável tenta autenticar um cliente não autenticado até que um tempo limite ocorre em vez de gerar uma exceção após a primeira falha.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurar o serviço com um WSHttpBinding para usar uma sessão confiável

Esse procedimento é descrito na [como: troca mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurar o cliente com um WSHttpBinding para usar uma sessão confiável

Esse procedimento é descrito na [como: troca mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Definir o modo e ClientCredentialType na configuração

1. Adicionar um elemento de associação apropriado para o [  **\<associações >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento do arquivo de configuração. O exemplo a seguir adiciona uma [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.

1. Adicionar um  **\<associação >** elemento e defina seu `name` de atributo para um valor apropriado. O exemplo usa o nome `MessageSecurity`.

1. Adicionar um  **\<segurança >** elemento e defina o `mode` atributo `Message`.

1. Dentro de  **\<segurança >** elemento, adicionar um  **\<mensagem >** elemento e o conjunto do `clientCredentialType` de atributo para `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
