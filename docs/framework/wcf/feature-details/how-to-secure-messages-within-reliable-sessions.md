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
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="e0047-102">Como proteger mensagens em sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="e0047-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="e0047-103">Este tópico descreve as etapas necessárias para habilitar a segurança em nível de mensagem para mensagens trocadas em uma sessão confiável usando uma das associações fornecidas pelo sistema que dão suporte a essa sessão, mas não por padrão.</span><span class="sxs-lookup"><span data-stu-id="e0047-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="e0047-104">Habilite uma sessão segura e confiável de forma imperativa usando código ou declarativamente no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e0047-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="e0047-105">Este procedimento usa os arquivos de configuração de cliente e serviço para habilitar a sessão segura e confiável.</span><span class="sxs-lookup"><span data-stu-id="e0047-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="e0047-106">Esse procedimento consiste nas seguintes três tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="e0047-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="e0047-107">Especifique que o cliente e o serviço trocam mensagens em uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="e0047-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="e0047-108">Exigir segurança em nível de mensagem na sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="e0047-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="e0047-109">Especifique o tipo de credencial do cliente que o cliente deve usar para ser autenticado com o serviço.</span><span class="sxs-lookup"><span data-stu-id="e0047-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="e0047-110">É importante na primeira tarefa que o elemento de configuração do ponto de extremidade contém um atributo `bindingConfiguration` que faz referência a uma configuração de associação chamada (neste exemplo) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="e0047-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="e0047-111">O [ **\<associação >** ](../../configure-apps/file-schema/wcf/bindings.md) elemento de configuração, em seguida, faz referência a esse nome para habilitar sessões confiáveis, definindo o atributo `enabled` do elemento [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) como `true`.</span><span class="sxs-lookup"><span data-stu-id="e0047-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="e0047-112">Você pode exigir que as garantias de entrega ordenadas estejam disponíveis em uma sessão confiável definindo o atributo `ordered` como `true`.</span><span class="sxs-lookup"><span data-stu-id="e0047-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="e0047-113">Para a cópia de origem do exemplo no qual esse procedimento de configuração se baseia, consulte a [sessão confiável do WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="e0047-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="e0047-114">Os itens essenciais da segunda tarefa são realizados com a definição do atributo `mode` do elemento **\<security >** contido no elemento **> de associação\<** do cliente e do serviço como `Message`.</span><span class="sxs-lookup"><span data-stu-id="e0047-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="e0047-115">Os itens essenciais da terceira tarefa são realizados com a definição do atributo `clientCredentialType` do elemento **\<message >** contido no elemento **\<Security >** do cliente e do serviço como `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="e0047-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="e0047-116">Ao usar a segurança de mensagem com sessões confiáveis, o sistema de mensagens confiável tenta autenticar um cliente não autenticado até que ocorra um tempo limite em vez de lançar uma exceção na primeira falha.</span><span class="sxs-lookup"><span data-stu-id="e0047-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="e0047-117">Configurar o serviço com uma WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="e0047-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="e0047-118">Este procedimento é descrito em [como trocar mensagens em uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="e0047-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="e0047-119">Configurar o cliente com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="e0047-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="e0047-120">Este procedimento é descrito em [como trocar mensagens em uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="e0047-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="e0047-121">Definir o modo e ClientCredentialtype na configuração</span><span class="sxs-lookup"><span data-stu-id="e0047-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="e0047-122">Adicione um elemento Binding apropriado ao elemento [ **\<bindings >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e0047-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="e0047-123">O exemplo a seguir adiciona um elemento [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e0047-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="e0047-124">Adicione um elemento de **> de associação de\<** e defina seu atributo `name` como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e0047-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="e0047-125">O exemplo usa o nome `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="e0047-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="e0047-126">Adicione um elemento de **> de segurança\<** e defina o atributo `mode` como `Message`.</span><span class="sxs-lookup"><span data-stu-id="e0047-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="e0047-127">No elemento **\<security >** , adicione um elemento **\<Message >** e defina o atributo `clientCredentialType` como `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="e0047-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
