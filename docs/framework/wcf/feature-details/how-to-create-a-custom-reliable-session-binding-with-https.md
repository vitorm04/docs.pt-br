---
title: Como criar uma associação de sessão confiável personalizada com HTTPS
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 26466a97ae44e6852c189d0b72bdba1b93d86141
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141727"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="2e2bf-102">Como criar uma associação de sessão confiável personalizada com HTTPS</span><span class="sxs-lookup"><span data-stu-id="2e2bf-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="2e2bf-103">Este tópico demonstra o uso de segurança de transporte de protocolo SSL (SSL) com sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="2e2bf-104">Para usar uma sessão confiável por HTTPS, você deve criar uma associação personalizada que usa uma sessão confiável e o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="2e2bf-105">Você pode habilitar a sessão confiável de maneira imperativa usando código ou declarativamente no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="2e2bf-106">Este procedimento usa os arquivos de configuração de cliente e serviço para habilitar a sessão confiável e o elemento [ **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) .</span><span class="sxs-lookup"><span data-stu-id="2e2bf-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="2e2bf-107">A parte principal desse procedimento é que o **\<ponto de extremidade >** elemento de configuração contém um atributo `bindingConfiguration` que faz referência a uma configuração de associação personalizada chamada `reliableSessionOverHttps`.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="2e2bf-108">O elemento de configuração [ **\<binding >** ](../../configure-apps/file-schema/wcf/bindings.md) faz referência a esse nome para especificar que uma sessão confiável e o transporte HTTPS sejam usados, incluindo **\<elementos reliableSession >** e **\<httpsTransport >** .</span><span class="sxs-lookup"><span data-stu-id="2e2bf-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="2e2bf-109">Para a cópia de origem deste exemplo, consulte [sessão confiável de associação personalizada sobre HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="2e2bf-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="2e2bf-110">Configurar o serviço com uma Personalizadabinding para usar uma sessão confiável com HTTPS</span><span class="sxs-lookup"><span data-stu-id="2e2bf-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="2e2bf-111">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="2e2bf-112">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="2e2bf-113">Observe que as informações de endereço ou de associação não são especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="2e2bf-114">Não é necessário escrever código para recuperar o endereço ou as informações de associação do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="2e2bf-115">Crie um arquivo *Web. config* para configurar um ponto de extremidade para o `CalculatorService` com uma associação personalizada chamada `reliableSessionOverHttps` que usa uma sessão confiável e o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="2e2bf-116">Crie um arquivo *Service. svc* que contenha a linha:</span><span class="sxs-lookup"><span data-stu-id="2e2bf-116">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="2e2bf-117">Coloque o arquivo *Service. svc* no diretório virtual do serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="2e2bf-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="2e2bf-118">Configurar o cliente com uma Personalizadabinding para usar uma sessão confiável com HTTPS</span><span class="sxs-lookup"><span data-stu-id="2e2bf-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="2e2bf-119">Use a [ferramenta de utilitário de metadados ServiceModel (*svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="2e2bf-120">O cliente gerado contém a interface `ICalculator` que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="2e2bf-121">O aplicativo cliente gerado também contém a implementação do `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="2e2bf-122">Observe que as informações de endereço e de associação não são especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="2e2bf-123">Não é necessário escrever código para recuperar o endereço e as informações de associação do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="2e2bf-124">Configure uma associação personalizada chamada `reliableSessionOverHttps` para usar o transporte HTTPS e as sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="2e2bf-125">Crie uma instância do `ClientCalculator` em um aplicativo e, em seguida, chame as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="2e2bf-126">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="2e2bf-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e2bf-127">.NET Framework security</span></span>

<span data-ttu-id="2e2bf-128">Como o certificado usado neste exemplo é um certificado de teste criado com *MakeCert. exe*, um alerta de segurança é exibido quando você tenta acessar um endereço https, como `https://localhost/servicemodelsamples/service.svc`, no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="2e2bf-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e2bf-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e2bf-129">See also</span></span>

- [<span data-ttu-id="2e2bf-130">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="2e2bf-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
