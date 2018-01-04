---
title: "Como criar um serviço Web HTTP WCF básico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dc60bbb51bc573840d0d45356f0cd84fd32db2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="95d7c-102">Como criar um serviço Web HTTP WCF básico</span><span class="sxs-lookup"><span data-stu-id="95d7c-102">How to: Create a Basic WCF Web HTTP Service</span></span>
<span data-ttu-id="95d7c-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permite criar um serviço que expõe um ponto de extremidade Web.</span><span class="sxs-lookup"><span data-stu-id="95d7c-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="95d7c-104">Os pontos de extremidade Web enviam dados por XML ou JSON; não há envelope SOAP.</span><span class="sxs-lookup"><span data-stu-id="95d7c-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="95d7c-105">Este tópico demonstra como expor um ponto de extremidade desse tipo.</span><span class="sxs-lookup"><span data-stu-id="95d7c-105">This topic demonstrates how to expose such an endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95d7c-106">A única maneira de proteger um ponto de extremidade Web é exibi-lo via HTTPS, usando segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="95d7c-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="95d7c-107">Quando a segurança baseada em mensagem é usada, as informações de segurança são geralmente colocadas em cabeçalhos SOAP e, como as mensagens enviadas a pontos de extremidade não SOAP não contêm envelopes SOAP, não há lugar para colocar informações de segurança. Assim, é necessário confiar na segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="95d7c-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>  
  
### <a name="to-create-a-web-endpoint"></a><span data-ttu-id="95d7c-108">Para criar um ponto de extremidade Web</span><span class="sxs-lookup"><span data-stu-id="95d7c-108">To create a Web endpoint</span></span>  
  
1.  <span data-ttu-id="95d7c-109">Defina um contrato de serviço usando uma interface marcada com os atributos <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> e <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="95d7c-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="95d7c-110">Por padrão, <xref:System.ServiceModel.Web.WebInvokeAttribute> mapeia chamadas POST para a operação.</span><span class="sxs-lookup"><span data-stu-id="95d7c-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="95d7c-111">É possível, entretanto, especificar o método HTTP (por exemplo, HEAD, PUT ou DELETE) para mapear a operação especificando um parâmetro "method=".</span><span class="sxs-lookup"><span data-stu-id="95d7c-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="95d7c-112"><xref:System.ServiceModel.Web.WebGetAttribute> não tem um parâmetro "method=" e só mapeia chamadas GET para a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="95d7c-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="95d7c-113">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="95d7c-113">Implement the service contract.</span></span>  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="95d7c-114">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="95d7c-114">To host the service</span></span>  
  
1.  <span data-ttu-id="95d7c-115">Crie um objeto <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="95d7c-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  <span data-ttu-id="95d7c-116">Adicione uma classe <xref:System.ServiceModel.Description.ServiceEndpoint> com <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="95d7c-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="95d7c-117">Se você não adicionar um ponto de extremidade, <xref:System.ServiceModel.Web.WebServiceHost> criará automaticamente um ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="95d7c-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="95d7c-118"><xref:System.ServiceModel.Web.WebServiceHost> também adiciona <xref:System.ServiceModel.Description.WebHttpBehavior> e desabilita a página da ajuda HTTP e a funcionalidade GET da linguagem WSDL para que o ponto de extremidade de metadados não interfira no ponto de extremidade HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="95d7c-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>  
    >   
    >  <span data-ttu-id="95d7c-119">A adição de um ponto de extremidade não SOAP com uma URL de "" gera um comportamento inesperado quando há uma tentativa de chamar uma operação no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="95d7c-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="95d7c-120">Isso decorre porque o URI de escuta do ponto de extremidade é igual ao URI da página de ajuda (a página que é exibida quando você navega até o endereço básico de um serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="95d7c-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service).</span></span>  
  
     <span data-ttu-id="95d7c-121">Você pode executar uma das seguintes ações para evitar que isso ocorra:</span><span class="sxs-lookup"><span data-stu-id="95d7c-121">You can do one of the following actions to prevent this from happening:</span></span>  
  
    -   <span data-ttu-id="95d7c-122">Especifique sempre um URI que não esteja em branco para um ponto de extremidade não SOAP.</span><span class="sxs-lookup"><span data-stu-id="95d7c-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>  
  
    -   <span data-ttu-id="95d7c-123">Desative a página de ajuda.</span><span class="sxs-lookup"><span data-stu-id="95d7c-123">Turn off the help page.</span></span> <span data-ttu-id="95d7c-124">Isso pode ser feito com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="95d7c-124">This can be done with the following code.</span></span>  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  <span data-ttu-id="95d7c-125">Abra o host do serviço e aguarde até que o usuário pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="95d7c-125">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     <span data-ttu-id="95d7c-126">Este exemplo demonstra como hospedar um serviço estilo Web com um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="95d7c-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="95d7c-127">Também é possível hospedar esse tipo de serviço no IIS.</span><span class="sxs-lookup"><span data-stu-id="95d7c-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="95d7c-128">Para fazer isso, especifique a classe <xref:System.ServiceModel.Activation.WebServiceHostFactory> em um arquivo .svc como demonstra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="95d7c-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="95d7c-129">Para chamar operações de serviço mapeadas para GET no Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="95d7c-129">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="95d7c-130">Abra o Internet Explorer e digite "`http://localhost:8000/EchoWithGet?s=Hello, world!`" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="95d7c-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="95d7c-131">A URL contém o endereço básico do serviço ("http://localhost:8000/"), o endereço relativo do ponto de extremidade (""), a operação de serviço a ser chamada ("EchoWithGet") e um ponto de interrogação seguido por uma lista de parâmetros nomeados separados por um E comercial (&).</span><span class="sxs-lookup"><span data-stu-id="95d7c-131">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-in-code"></a><span data-ttu-id="95d7c-132">Para chamar operações de serviço no código</span><span class="sxs-lookup"><span data-stu-id="95d7c-132">To call service operations in code</span></span>  
  
1.  <span data-ttu-id="95d7c-133">Criar uma instância de <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` dentro de um `using` bloco.</span><span class="sxs-lookup"><span data-stu-id="95d7c-133">Create an instance of <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` within a `using` block.</span></span>  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  <span data-ttu-id="95d7c-134">Adicione <xref:System.ServiceModel.Description.WebHttpBehavior> ao ponto de extremidade que <xref:System.ServiceModel.ChannelFactory> chama.</span><span class="sxs-lookup"><span data-stu-id="95d7c-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory> calls.</span></span>  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  <span data-ttu-id="95d7c-135">Crie o canal e chame o serviço.</span><span class="sxs-lookup"><span data-stu-id="95d7c-135">Create the channel and call the service.</span></span>  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  <span data-ttu-id="95d7c-136">Feche a classe <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="95d7c-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="95d7c-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95d7c-137">Example</span></span>  
 <span data-ttu-id="95d7c-138">A seguir está a listagem completa de códigos deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="95d7c-138">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95d7c-139">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="95d7c-139">Compiling the Code</span></span>  
 <span data-ttu-id="95d7c-140">Ao compilar Service.cs, faça referência à System.ServiceModel.dll e à System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="95d7c-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d7c-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95d7c-141">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="95d7c-142">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="95d7c-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
