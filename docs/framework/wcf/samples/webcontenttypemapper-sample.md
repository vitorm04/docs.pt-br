---
title: WebContentTypeMapper Sample
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27342076290ca40abefea63edcc5f5c7186c4256
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="a06fb-102">WebContentTypeMapper Sample</span><span class="sxs-lookup"><span data-stu-id="a06fb-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="a06fb-103">Este exemplo demonstra como mapear os novos tipos de conteúdo para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] formatos de corpo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a06fb-103">This sample demonstrates how to map new content types to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message body formats.</span></span>  
  
 <span data-ttu-id="a06fb-104">O <xref:System.ServiceModel.Description.WebHttpEndpoint> elemento se conecta o codificador de mensagem da Web, que permite [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para receber mensagens de binárias brutas no mesmo ponto de extremidade, XML ou JSON.</span><span class="sxs-lookup"><span data-stu-id="a06fb-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="a06fb-105">O codificador determina o formato do corpo da mensagem, observando o tipo de conteúdo HTTP da solicitação.</span><span class="sxs-lookup"><span data-stu-id="a06fb-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="a06fb-106">Este exemplo apresenta o <xref:System.ServiceModel.Channels.WebContentTypeMapper> classe, que permite ao usuário controlar o mapeamento entre o tipo de conteúdo e o formato do corpo.</span><span class="sxs-lookup"><span data-stu-id="a06fb-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a06fb-107">Fornece um conjunto de mapeamentos padrão para tipos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a06fb-107"> provides a set of default mappings for content types.</span></span> <span data-ttu-id="a06fb-108">Por exemplo, `application/json` mapeia para JSON e `text/xml` mapeia para XML.</span><span class="sxs-lookup"><span data-stu-id="a06fb-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="a06fb-109">Qualquer tipo de conteúdo que não está mapeado para JSON ou XML é mapeado para o formato binário bruto.</span><span class="sxs-lookup"><span data-stu-id="a06fb-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="a06fb-110">Em alguns cenários (por exemplo, APIs push-style), o desenvolvedor de serviço não controla o tipo de conteúdo retornado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a06fb-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="a06fb-111">Por exemplo, os clientes podem retornar JSON como `text/javascript` em vez de `application/json`.</span><span class="sxs-lookup"><span data-stu-id="a06fb-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="a06fb-112">Nesse caso, o desenvolvedor de serviço deve fornecer um tipo que deriva de <xref:System.ServiceModel.Channels.WebContentTypeMapper> para lidar com o tipo de conteúdo fornecido corretamente, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a06fb-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a06fb-113">O tipo deve substituir o <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> método.</span><span class="sxs-lookup"><span data-stu-id="a06fb-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="a06fb-114">O método deve avaliar o `contentType` argumento e retornar um dos seguintes valores: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, ou <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="a06fb-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="a06fb-115">Retornando <xref:System.ServiceModel.Channels.WebContentFormat.Default> transfere para os mapeamentos de codificador de mensagem de Web padrão.</span><span class="sxs-lookup"><span data-stu-id="a06fb-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="a06fb-116">No código de exemplo anterior, o `text/javascript` conteúdo tipo é mapeado para JSON, e todos os outros mapeamentos permanecem inalterados.</span><span class="sxs-lookup"><span data-stu-id="a06fb-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="a06fb-117">Para usar o `JsonContentTypeMapper` de classe, use o seguinte no Web. config:</span><span class="sxs-lookup"><span data-stu-id="a06fb-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a06fb-118">Para verificar se o requisito para usar o JsonContentTypeMapper, remova o atributo de contentTypeMapper do arquivo de configuração acima.</span><span class="sxs-lookup"><span data-stu-id="a06fb-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="a06fb-119">A página do cliente não for carregado durante a tentativa de usar `text/javascript` para enviar conteúdo o JSON.</span><span class="sxs-lookup"><span data-stu-id="a06fb-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a06fb-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a06fb-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a06fb-121">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a06fb-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a06fb-122">Compile a solução WebContentTypeMapperSample.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a06fb-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a06fb-123">Navegue até http://localhost/ServiceModelSamples/JCTMClientPage.htm (não abrir JCTMClientPage.htm no navegador de dentro do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="a06fb-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a06fb-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a06fb-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a06fb-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a06fb-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a06fb-126">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a06fb-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a06fb-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a06fb-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="a06fb-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a06fb-128">See Also</span></span>
