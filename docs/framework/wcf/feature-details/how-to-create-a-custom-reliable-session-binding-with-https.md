---
title: "Como criar uma associação de sessão confiável personalizada com HTTPS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87a27bb3e33b0dd78fdb2dfa206bbde098c8b769
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="cdb79-102">Como criar uma associação de sessão confiável personalizada com HTTPS</span><span class="sxs-lookup"><span data-stu-id="cdb79-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="cdb79-103">Este tópico demonstra o uso da segurança de transporte do Secure Sockets Layer (SSL) com sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="cdb79-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="cdb79-104">Para usar uma sessão confiável via HTTPS, você deve criar uma associação personalizada que usa uma sessão confiável e o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cdb79-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="cdb79-105">Você ativar a sessão confiável imperativa por meio de código ou declarativamente no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cdb79-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="cdb79-106">Este procedimento usa os arquivos de configuração do cliente e de serviço para habilitar a sessão confiável e o [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="cdb79-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="cdb79-107">A parte fundamental desse procedimento é que o  **\<ponto de extremidade >** elemento de configuração contêm uma `bindingConfiguration` atributo que faz referência a uma configuração de associação personalizada nomeada `reliableSessionOverHttps`.</span><span class="sxs-lookup"><span data-stu-id="cdb79-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="cdb79-108">O [  **\<associação >** ](../../../../docs/framework/misc/binding.md) elemento de configuração faz referência a esse nome para especificar que uma sessão confiável e o transporte HTTPS são usados, incluindo  **\< reliableSession >** e  **\<httpsTransport >** elementos.</span><span class="sxs-lookup"><span data-stu-id="cdb79-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="cdb79-109">Para a cópia de origem deste exemplo, consulte [personalizado associação de sessão confiável via HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="cdb79-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="cdb79-110">Configure o serviço com CustomBinding para usar uma sessão confiável com HTTPS</span><span class="sxs-lookup"><span data-stu-id="cdb79-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="cdb79-111">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="cdb79-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="cdb79-112">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="cdb79-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="cdb79-113">Observe que as informações de associação ou o endereço não estão especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="cdb79-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="cdb79-114">Não é necessário escrever código para recuperar as informações de associação ou o endereço do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cdb79-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="cdb79-115">Criar um *Web. config* arquivo para configurar um ponto de extremidade para o `CalculatorService` com uma associação personalizada denominada `reliableSessionOverHttps` que usa uma sessão confiável e o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cdb79-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="cdb79-116">Criar um *svc* arquivo que contém a linha:</span><span class="sxs-lookup"><span data-stu-id="cdb79-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="cdb79-117">Coloque o *svc* arquivo no seu diretório virtual dos serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="cdb79-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="cdb79-118">Configurar o cliente com CustomBinding para usar uma sessão confiável com HTTPS</span><span class="sxs-lookup"><span data-stu-id="cdb79-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="cdb79-119">Use o [Ferramenta Utilitária de metadados ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar o código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="cdb79-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="cdb79-120">O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.</span><span class="sxs-lookup"><span data-stu-id="cdb79-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="cdb79-121">O aplicativo cliente gerado também contém a implementação de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="cdb79-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="cdb79-122">Observe que as informações de endereço e associação não são especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="cdb79-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="cdb79-123">Não é necessário escrever código para recuperar as informações de endereço e a associação do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cdb79-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="cdb79-124">Configurar uma associação personalizada denominada `reliableSessionOverHttps` para usar o transporte HTTPS e sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="cdb79-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="cdb79-125">Criar uma instância do `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="cdb79-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="cdb79-126">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="cdb79-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="cdb79-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cdb79-127">.NET Framework security</span></span>

<span data-ttu-id="cdb79-128">Porque o certificado usado neste exemplo é um certificado de teste criado com *Makecert.exe*, um alerta de segurança é exibida quando você tentar acessar um endereço HTTPS, tais como `https://localhost/servicemodelsamples/service.svc`, no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="cdb79-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdb79-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdb79-129">See also</span></span>

[<span data-ttu-id="cdb79-130">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="cdb79-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
