---
title: Como fazer intercâmbio de mensagens dentro de uma sessão confiável
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 58a392fc6295e82f41e08c80a3343b4059afad7e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141683"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="dabeb-102">Como fazer intercâmbio de mensagens dentro de uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="dabeb-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="dabeb-103">Este tópico descreve as etapas necessárias para habilitar uma sessão confiável usando uma das associações fornecidas pelo sistema que dão suporte a essa sessão, mas não por padrão.</span><span class="sxs-lookup"><span data-stu-id="dabeb-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="dabeb-104">Você habilita uma sessão confiável imperativamente usando código ou declarativamente em seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dabeb-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="dabeb-105">Este procedimento usa os arquivos de configuração de cliente e serviço para habilitar a sessão confiável e estipular que as mensagens chegam na mesma ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="dabeb-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="dabeb-106">A parte principal desse procedimento é que o elemento de configuração do ponto de extremidade contém um atributo `bindingConfiguration` que faz referência a uma configuração de associação chamada `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="dabeb-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="dabeb-107">O elemento de configuração [ **\<binding >** ](../../configure-apps/file-schema/wcf/bindings.md) faz referência a esse nome para habilitar sessões confiáveis, definindo o atributo `enabled` do elemento [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) como `true`.</span><span class="sxs-lookup"><span data-stu-id="dabeb-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="dabeb-108">Você especifica as garantias de entrega ordenadas para a sessão confiável definindo o atributo `ordered` como `true`.</span><span class="sxs-lookup"><span data-stu-id="dabeb-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="dabeb-109">Para a cópia de origem deste exemplo, consulte a [sessão confiável do WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="dabeb-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="dabeb-110">Configurar o serviço com uma WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="dabeb-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="dabeb-111">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="dabeb-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="dabeb-112">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="dabeb-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="dabeb-113">Observe que as informações de endereço ou de associação não são especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="dabeb-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="dabeb-114">Não é necessário escrever código para recuperar o endereço ou as informações de associação do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dabeb-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="dabeb-115">Crie um arquivo *Web. config* para configurar um ponto de extremidade para o `CalculatorService` que usa o <xref:System.ServiceModel.WSHttpBinding> com sessão confiável habilitada e entrega ordenada de mensagens necessárias.</span><span class="sxs-lookup"><span data-stu-id="dabeb-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="dabeb-116">Crie um arquivo *Service. svc* que contenha a linha:</span><span class="sxs-lookup"><span data-stu-id="dabeb-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="dabeb-117">Coloque o arquivo *Service. svc* no diretório virtual do serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="dabeb-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="dabeb-118">Configurar o cliente com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="dabeb-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="dabeb-119">Use a [ferramenta de utilitário de metadados ServiceModel (*svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar código de metadados de serviço:</span><span class="sxs-lookup"><span data-stu-id="dabeb-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="dabeb-120">O cliente gerado contém a interface `ICalculator` que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="dabeb-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="dabeb-121">O aplicativo cliente gerado também contém a implementação do `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="dabeb-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="dabeb-122">Observe que as informações de endereço e de associação não são especificadas em nenhum lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="dabeb-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="dabeb-123">Não é necessário escrever código para recuperar o endereço ou as informações de associação do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dabeb-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="dabeb-124">*Svcutil. exe* também gera a configuração para o cliente que usa a classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="dabeb-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="dabeb-125">Nomeie o arquivo de configuração *app. config* ao usar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dabeb-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="dabeb-126">Crie uma instância do `ClientCalculator` em um aplicativo e chame as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="dabeb-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="dabeb-127">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="dabeb-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="dabeb-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dabeb-128">Example</span></span>

<span data-ttu-id="dabeb-129">Por padrão, várias das associações fornecidas pelo sistema dão suporte a sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="dabeb-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="dabeb-130">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="dabeb-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="dabeb-131">Para obter um exemplo de como criar uma associação personalizada que dê suporte a sessões confiáveis, consulte [como: criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="dabeb-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dabeb-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dabeb-132">See also</span></span>

- [<span data-ttu-id="dabeb-133">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="dabeb-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
