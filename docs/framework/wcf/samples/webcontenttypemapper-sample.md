---
title: WebContentTypeMapper Sample
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143558"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="81ed6-102">WebContentTypeMapper Sample</span><span class="sxs-lookup"><span data-stu-id="81ed6-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="81ed6-103">Esta amostra demonstra como mapear novos tipos de conteúdo para os formatos de corpo de mensagem da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="81ed6-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="81ed6-104">O <xref:System.ServiceModel.Description.WebHttpEndpoint> elemento conecta-se ao codificador de mensagens da Web, que permite que o WCF receba mensagens binárias JSON, XML ou raw no mesmo ponto final.</span><span class="sxs-lookup"><span data-stu-id="81ed6-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="81ed6-105">O codificador determina o formato do corpo da mensagem olhando para o tipo de conteúdo HTTP da solicitação.</span><span class="sxs-lookup"><span data-stu-id="81ed6-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="81ed6-106">Esta amostra introduz <xref:System.ServiceModel.Channels.WebContentTypeMapper> a classe, que permite ao usuário controlar o mapeamento entre o tipo de conteúdo e o formato do corpo.</span><span class="sxs-lookup"><span data-stu-id="81ed6-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="81ed6-107">O WCF fornece um conjunto de mapeamentos padrão para tipos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="81ed6-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="81ed6-108">Por exemplo, `application/json` mapas para `text/xml` JSON e mapas para XML.</span><span class="sxs-lookup"><span data-stu-id="81ed6-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="81ed6-109">Qualquer tipo de conteúdo que não seja mapeado para JSON ou XML é mapeado para o formato binário bruto.</span><span class="sxs-lookup"><span data-stu-id="81ed6-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="81ed6-110">Em alguns cenários (por exemplo, APIs estilo push), o desenvolvedor de serviços não controla o tipo de conteúdo retornado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="81ed6-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="81ed6-111">Por exemplo, os clientes `text/javascript` podem `application/json`retornar JSON como em vez de .</span><span class="sxs-lookup"><span data-stu-id="81ed6-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="81ed6-112">Neste caso, o desenvolvedor do serviço deve <xref:System.ServiceModel.Channels.WebContentTypeMapper> fornecer um tipo que deriva para lidar com o determinado tipo de conteúdo corretamente, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="81ed6-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="81ed6-113">O tipo deve <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> substituir o método.</span><span class="sxs-lookup"><span data-stu-id="81ed6-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="81ed6-114">O método deve `contentType` avaliar o argumento e <xref:System.ServiceModel.Channels.WebContentFormat.Json>retornar <xref:System.ServiceModel.Channels.WebContentFormat.Xml> <xref:System.ServiceModel.Channels.WebContentFormat.Raw>um <xref:System.ServiceModel.Channels.WebContentFormat.Default>dos seguintes valores: , , ou .</span><span class="sxs-lookup"><span data-stu-id="81ed6-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="81ed6-115">O <xref:System.ServiceModel.Channels.WebContentFormat.Default> retorno adia os mapeamentos padrão do codificador de mensagens da Web.</span><span class="sxs-lookup"><span data-stu-id="81ed6-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="81ed6-116">No código de amostra `text/javascript` anterior, o tipo de conteúdo é mapeado para JSON, e todos os outros mapeamentos permanecem inalterados.</span><span class="sxs-lookup"><span data-stu-id="81ed6-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="81ed6-117">Para usar `JsonContentTypeMapper` a classe, use o seguinte em sua Web.config:</span><span class="sxs-lookup"><span data-stu-id="81ed6-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="81ed6-118">Para verificar a necessidade de usar o JsonContentTypeMapper, remova o atributo contentTypeMapper do arquivo de configuração acima.</span><span class="sxs-lookup"><span data-stu-id="81ed6-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="81ed6-119">A página do cliente falha ao `text/javascript` ser carregada ao tentar usar para enviar conteúdo JSON.</span><span class="sxs-lookup"><span data-stu-id="81ed6-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="81ed6-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="81ed6-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="81ed6-121">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81ed6-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="81ed6-122">Construa a solução WebContentTypeMapperSample.sln conforme descrito na [construção do Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81ed6-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="81ed6-123">Navegue `http://localhost/ServiceModelSamples/JCTMClientPage.htm` para (não abra JCTMClientPage.htm no navegador de dentro do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="81ed6-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="81ed6-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="81ed6-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="81ed6-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="81ed6-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="81ed6-126">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="81ed6-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81ed6-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="81ed6-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
