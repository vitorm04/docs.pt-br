---
title: 'Como: Mensagens seguras em sessões confiáveis'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: ee35f2a36ca08814423b5a3d0b1432bacd28c2e5
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333047"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="80196-102">Como: Mensagens seguras em sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="80196-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="80196-103">Este tópico descreve as etapas necessárias para habilitar a segurança de nível de mensagem para mensagens trocadas dentro de uma sessão confiável usando uma das associações fornecidas pelo sistema que dão suporte a essa sessão, mas não por padrão.</span><span class="sxs-lookup"><span data-stu-id="80196-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="80196-104">Habilite uma sessão segura e confiável, imperativamente por meio de código ou declarativamente no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="80196-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="80196-105">Este procedimento usa os arquivos de configuração do cliente e o serviço para habilitar a sessão segura e confiável.</span><span class="sxs-lookup"><span data-stu-id="80196-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="80196-106">Este procedimento consiste em três tarefas principais a seguir:</span><span class="sxs-lookup"><span data-stu-id="80196-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="80196-107">Especifique que o cliente e o serviço de trocam mensagens dentro de uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="80196-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="80196-108">Exigir segurança em nível de mensagem dentro da sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="80196-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="80196-109">Especifique o tipo de credencial de cliente que o cliente deve usar para ser autenticado com o serviço.</span><span class="sxs-lookup"><span data-stu-id="80196-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="80196-110">É importante na primeira tarefa que o elemento de configuração do ponto de extremidade contêm uma `bindingConfiguration` atributo que faz referência a uma configuração de associação chamada (neste exemplo) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="80196-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="80196-111">O [  **\<associação >** ](../../../../docs/framework/misc/binding.md) elemento de configuração, em seguida, faz referência a esse nome para habilitar sessões confiáveis, definindo o `enabled` atributo do [  **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) elemento `true`.</span><span class="sxs-lookup"><span data-stu-id="80196-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="80196-112">Você pode exigir que as garantias de entrega ordenada estão disponíveis dentro de uma sessão confiável, definindo o `ordered` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="80196-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="80196-113">Para a cópia do código-fonte do exemplo no qual este procedimento de configuração se baseia, consulte o [sessão confiável de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="80196-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="80196-114">Os itens essenciais da segunda tarefa são realizados, definindo o `mode` atributo do  **\<segurança >** elemento contido no  **\<associação >** elemento do cliente e do serviço para `Message`.</span><span class="sxs-lookup"><span data-stu-id="80196-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="80196-115">Os itens essenciais da terceira tarefa são realizados, definindo o `clientCredentialType` atributo do  **\<mensagem >** elemento contido no  **\<segurança >** elemento do cliente e do serviço para `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="80196-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="80196-116">Ao usar a segurança de mensagem com sessões confiáveis, sistema de mensagens confiável tenta autenticar um cliente não autenticado até que um tempo limite ocorre em vez de gerar uma exceção após a primeira falha.</span><span class="sxs-lookup"><span data-stu-id="80196-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="80196-117">Configurar o serviço com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="80196-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="80196-118">Esse procedimento é descrito em [como: Trocar mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="80196-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="80196-119">Configurar o cliente com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="80196-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="80196-120">Esse procedimento é descrito em [como: Trocar mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="80196-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="80196-121">Definir o modo e ClientCredentialType na configuração</span><span class="sxs-lookup"><span data-stu-id="80196-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="80196-122">Adicionar um elemento de associação apropriado para o [  **\<associações >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="80196-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="80196-123">O exemplo a seguir adiciona uma [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="80196-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="80196-124">Adicionar um  **\<associação >** elemento e defina seu `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="80196-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="80196-125">O exemplo usa o nome `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="80196-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="80196-126">Adicionar um  **\<segurança >** elemento e defina o `mode` atributo `Message`.</span><span class="sxs-lookup"><span data-stu-id="80196-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="80196-127">Dentro de  **\<segurança >** elemento, adicionar um  **\<mensagem >** elemento e o conjunto do `clientCredentialType` de atributo para `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="80196-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
