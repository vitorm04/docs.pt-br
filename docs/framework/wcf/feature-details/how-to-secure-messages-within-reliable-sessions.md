---
title: "Como proteger mensagens em sessões confiáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3f27b1a4de2019660e0facb081300a79eae65b99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="9381c-102">Como proteger mensagens em sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="9381c-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="9381c-103">Este tópico descreve as etapas necessárias para habilitar a segurança de nível de mensagem para mensagens trocadas dentro de uma sessão confiável usando uma das associações fornecidas pelo sistema que oferecem suporte a uma sessão, mas não por padrão.</span><span class="sxs-lookup"><span data-stu-id="9381c-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="9381c-104">Habilite uma sessão segura e confiável imperativa por meio de código ou declarativamente no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9381c-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="9381c-105">Este procedimento usa os arquivos de configuração do cliente e de serviço para habilitar a sessão segura e confiável.</span><span class="sxs-lookup"><span data-stu-id="9381c-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="9381c-106">Esse procedimento consiste em três tarefas principais a seguir:</span><span class="sxs-lookup"><span data-stu-id="9381c-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="9381c-107">Especifique que o cliente e o serviço trocam mensagens dentro de uma sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="9381c-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="9381c-108">Exigir segurança de nível de mensagem na sessão confiável.</span><span class="sxs-lookup"><span data-stu-id="9381c-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="9381c-109">Especifique o tipo de credencial de cliente que o cliente deve usar para ser autenticado com o serviço.</span><span class="sxs-lookup"><span data-stu-id="9381c-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="9381c-110">É importante na primeira tarefa que o elemento de configuração de ponto de extremidade contêm um `bindingConfiguration` atributo que faz referência a uma configuração de associação chamada (neste exemplo) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="9381c-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="9381c-111">O [  **\<associação >** ](../../../../docs/framework/misc/binding.md) elemento de configuração, em seguida, faz referência a esse nome para permitir sessões confiáveis, definindo o `enabled` atributo o [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elemento `true`.</span><span class="sxs-lookup"><span data-stu-id="9381c-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="9381c-112">Você pode exigir que as garantias de entrega ordenada estão disponíveis em uma sessão confiável, definindo o `ordered` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="9381c-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="9381c-113">Para a cópia de origem do exemplo no qual se baseia neste procedimento de configuração, consulte o [sessão confiável de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="9381c-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="9381c-114">Os itens essenciais da segunda tarefa são realizados, definindo o `mode` atributo do  **\<segurança >** elemento contido no  **\<associação >** elemento do cliente e do serviço para `Message`.</span><span class="sxs-lookup"><span data-stu-id="9381c-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="9381c-115">Os itens essenciais da terceira tarefa são realizados, definindo o `clientCredentialType` atributo do  **\<mensagem >** elemento contido no  **\<segurança >** elemento do cliente e do serviço para `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="9381c-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="9381c-116">Ao usar a segurança de mensagem com sessões confiáveis, sistema de mensagens confiável tenta autenticar um cliente não autenticado até que ocorra um tempo limite, em vez de gerar uma exceção após a primeira falha.</span><span class="sxs-lookup"><span data-stu-id="9381c-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="9381c-117">Configure o serviço com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="9381c-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="9381c-118">Este procedimento é descrito em [como: Exchange mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="9381c-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="9381c-119">Configurar o cliente com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="9381c-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="9381c-120">Este procedimento é descrito em [como: Exchange mensagens dentro de uma sessão confiável](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="9381c-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="9381c-121">Definir o modo e ClientCredentialType na configuração</span><span class="sxs-lookup"><span data-stu-id="9381c-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="9381c-122">Adicionar um elemento de associação apropriado para o [  **\<associações >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9381c-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="9381c-123">O exemplo a seguir adiciona uma [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9381c-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="9381c-124">Adicionar um  **\<associação >** elemento e defina seu `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="9381c-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="9381c-125">O exemplo usa o nome `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="9381c-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="9381c-126">Adicionar um  **\<segurança >** elemento e defina o `mode` atributo `Message`.</span><span class="sxs-lookup"><span data-stu-id="9381c-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="9381c-127">Dentro de  **\<segurança >** elemento, adicionar um  **\<mensagem >** elemento e o conjunto a `clientCredentialType` atributo `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="9381c-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
