---
title: Como fazer intercâmbio de mensagens dentro de uma sessão confiável
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 53e5661bf140540cd0fc7a9fcb739b67488b8491
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374498"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="f43ec-102">Como fazer intercâmbio de mensagens dentro de uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="f43ec-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="f43ec-103">Este tópico descreve as etapas necessárias para habilitar uma sessão confiável usando uma das associações fornecidas pelo sistema que dão suporte a essa sessão, mas não por padrão.</span><span class="sxs-lookup"><span data-stu-id="f43ec-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="f43ec-104">Habilitar uma sessão confiável imperativamente usando código ou de forma declarativa em seu arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f43ec-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="f43ec-105">Este procedimento usa os arquivos de configuração do cliente e o serviço para habilitar a sessão confiável e estipulam que as mensagens chegam na mesma ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="f43ec-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="f43ec-106">A parte fundamental desse procedimento é que o elemento de configuração do ponto de extremidade contêm uma `bindingConfiguration` atributo que faz referência a uma configuração de ligação nomeada `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="f43ec-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="f43ec-107">O [  **\<associação >** ](../../../../docs/framework/misc/binding.md) elemento de configuração faz referência a esse nome para habilitar sessões confiáveis, definindo o `enabled` atributo do [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elemento `true`.</span><span class="sxs-lookup"><span data-stu-id="f43ec-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="f43ec-108">Especifique as garantias de entrega ordenada para a sessão confiável, definindo o `ordered` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="f43ec-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="f43ec-109">Para a cópia de origem deste exemplo, consulte [sessão confiável de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="f43ec-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f43ec-110">Configurar o serviço com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="f43ec-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="f43ec-111">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="f43ec-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="f43ec-112">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="f43ec-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="f43ec-113">Observe que as informações de associação ou o endereço não estão especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="f43ec-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="f43ec-114">Não é necessário escrever código para recuperar as informações de associação ou o endereço do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f43ec-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="f43ec-115">Criar uma *Web. config* arquivo para configurar um ponto de extremidade para o `CalculatorService` que usa o <xref:System.ServiceModel.WSHttpBinding> com uma sessão confiável habilitada e a entrega de mensagens necessária ordenada.</span><span class="sxs-lookup"><span data-stu-id="f43ec-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="f43ec-116">Criar uma *svc* arquivo que contém a linha:</span><span class="sxs-lookup"><span data-stu-id="f43ec-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="f43ec-117">Coloque o *svc* arquivo no seu diretório virtual de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="f43ec-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f43ec-118">Configurar o cliente com um WSHttpBinding para usar uma sessão confiável</span><span class="sxs-lookup"><span data-stu-id="f43ec-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="f43ec-119">Use o [ferramenta de utilitário de metadados ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar o código de metadados de serviço:</span><span class="sxs-lookup"><span data-stu-id="f43ec-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="f43ec-120">O cliente gerado contém o `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="f43ec-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="f43ec-121">O aplicativo de cliente gerado também contém a implementação do `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="f43ec-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="f43ec-122">Observe que as informações de endereço e a associação não são especificadas em qualquer lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="f43ec-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="f43ec-123">Não é necessário escrever código para recuperar as informações de associação ou o endereço do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f43ec-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="f43ec-124">*Svcutil.exe* também gera a configuração do cliente que usa o <xref:System.ServiceModel.WSHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="f43ec-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="f43ec-125">Nomeie o arquivo de configuração *App. config* ao usar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f43ec-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="f43ec-126">Criar uma instância das `ClientCalculator` em um aplicativo e chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="f43ec-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="f43ec-127">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="f43ec-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="f43ec-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f43ec-128">Example</span></span>

<span data-ttu-id="f43ec-129">Várias das associações fornecidas pelo sistema dá suporte a sessões confiáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="f43ec-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="f43ec-130">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="f43ec-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="f43ec-131">Para obter um exemplo de como criar uma associação personalizada que dá suporte a sessões confiáveis, consulte [como: criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="f43ec-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f43ec-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f43ec-132">See also</span></span>

[<span data-ttu-id="f43ec-133">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="f43ec-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
