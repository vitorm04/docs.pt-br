---
title: Como expor um contrato para clientes SOAP e da Web
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
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c04da670c84aaecf3587e6620c70e94c6b7350e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="b3845-102">Como expor um contrato para clientes SOAP e da Web</span><span class="sxs-lookup"><span data-stu-id="b3845-102">How to: Expose a Contract to SOAP and Web Clients</span></span>
<span data-ttu-id="b3845-103">Por padrão, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] disponibiliza pontos de extremidade apenas para clientes SOAP.</span><span class="sxs-lookup"><span data-stu-id="b3845-103">By default, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="b3845-104">Em [como: criar um serviço básico do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), um ponto de extremidade é disponibilizado para clientes SOAP não.</span><span class="sxs-lookup"><span data-stu-id="b3845-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="b3845-105">Pode haver momentos quando você deseja disponibilizar o mesmo contrato de duas maneiras, como um ponto de extremidade da Web e como um ponto de extremidade SOAP.</span><span class="sxs-lookup"><span data-stu-id="b3845-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="b3845-106">Este tópico mostra um exemplo de como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b3845-106">This topic shows an example of how to do this.</span></span>  
  
### <a name="to-define-the-service-contract"></a><span data-ttu-id="b3845-107">Para definir o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="b3845-107">To define the service contract</span></span>  
  
1.  <span data-ttu-id="b3845-108">Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> e <xref:System.ServiceModel.Web.WebGetAttribute> atributos, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="b3845-109">Por padrão <xref:System.ServiceModel.Web.WebInvokeAttribute> mapeia chamadas POST para a operação.</span><span class="sxs-lookup"><span data-stu-id="b3845-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="b3845-110">No entanto, você pode especificar o método para mapear para a operação especificando um "método =" parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b3845-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="b3845-111"><xref:System.ServiceModel.Web.WebGetAttribute> não tem um parâmetro "method=" e só mapeia chamadas GET para a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="b3845-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="b3845-112">Implemente o contrato de serviço, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-112">Implement the service contract, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="b3845-113">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="b3845-113">To host the service</span></span>  
  
1.  <span data-ttu-id="b3845-114">Criar um <xref:System.ServiceModel.ServiceHost> do objeto, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  <span data-ttu-id="b3845-115">Adicionar um <xref:System.ServiceModel.Description.ServiceEndpoint> com <xref:System.ServiceModel.BasicHttpBinding> para o ponto de extremidade SOAP, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  <span data-ttu-id="b3845-116">Adicionar um <xref:System.ServiceModel.Description.ServiceEndpoint> com <xref:System.ServiceModel.WebHttpBinding> para o ponto de extremidade SOAP não e adicione o <xref:System.ServiceModel.Description.WebHttpBehavior> ao ponto de extremidade, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  <span data-ttu-id="b3845-117">Chamar `Open()` em um <xref:System.ServiceModel.ServiceHost> instância para abrir o host de serviço, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="b3845-118">Para chamar operações de serviço mapeadas para GET no Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="b3845-118">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="b3845-119">Abra o Internet Explorer e digite "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="b3845-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="b3845-120">A URL contém o endereço básico do serviço ("http://localhost:8000/"), o endereço relativo do ponto de extremidade (""), a operação de serviço a ser chamada ("EchoWithGet") e um ponto de interrogação seguido por uma lista de parâmetros nomeados separados por um E comercial (&).</span><span class="sxs-lookup"><span data-stu-id="b3845-120">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="b3845-121">Para chamar operações de serviço no ponto de extremidade da Web no código</span><span class="sxs-lookup"><span data-stu-id="b3845-121">To call service operations on the Web endpoint in code</span></span>  
  
1.  <span data-ttu-id="b3845-122">Criar uma instância de <xref:System.ServiceModel.Web.WebChannelFactory%601> dentro de um `using` bloquear, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="b3845-123">`Close()`é chamado automaticamente no canal no final de `using` bloco.</span><span class="sxs-lookup"><span data-stu-id="b3845-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>  
  
1.  <span data-ttu-id="b3845-124">Criar o canal e chamar o serviço, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-124">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="b3845-125">Para chamar operações de serviço no ponto de extremidade SOAP</span><span class="sxs-lookup"><span data-stu-id="b3845-125">To call service operations on the SOAP endpoint</span></span>  
  
1.  <span data-ttu-id="b3845-126">Criar uma instância de <xref:System.ServiceModel.ChannelFactory> dentro de um `using` bloquear, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  <span data-ttu-id="b3845-127">Criar o canal e chamar o serviço, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-127">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a><span data-ttu-id="b3845-128">Para fechar o host de serviço</span><span class="sxs-lookup"><span data-stu-id="b3845-128">To close the service host</span></span>  
  
1.  <span data-ttu-id="b3845-129">Feche o host de serviço, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3845-129">Close the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="b3845-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3845-130">Example</span></span>  
 <span data-ttu-id="b3845-131">Este é o código completo listando deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b3845-131">The following is the full code listing for this topic.</span></span>  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3845-132">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b3845-132">Compiling the Code</span></span>  
 <span data-ttu-id="b3845-133">Ao compilar Service.cs, fazer referência a System.ServiceModel.dll e System.</span><span class="sxs-lookup"><span data-stu-id="b3845-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3845-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3845-134">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="b3845-135">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="b3845-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
