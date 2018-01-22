---
title: "Exemplo de serviço de AJAX utilizando tipos complexos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c83da8aba2e1a88665f4443d98dbebbd5b1962b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="93559-102">Exemplo de serviço de AJAX utilizando tipos complexos</span><span class="sxs-lookup"><span data-stu-id="93559-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="93559-103">Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um serviço ASP.NET Asynchronous JavaScript e XML (AJAX) que cria instâncias de tipos complexos e envia-os entre o cliente como JSON JavaScript Object Notation () e de serviço.</span><span class="sxs-lookup"><span data-stu-id="93559-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="93559-104">Você pode acessar um serviço de AJAX usando código JavaScript de um cliente de navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="93559-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="93559-105">Este exemplo se baseia o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="93559-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="93559-106">Suporte do AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é otimizado para uso com o ASP.NET AJAX por meio de <xref:System.Web.UI.ScriptManager> controle.</span><span class="sxs-lookup"><span data-stu-id="93559-106">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="93559-107">Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte o [AJAX exemplos](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="93559-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93559-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="93559-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="93559-109">O serviço no exemplo a seguir está uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço sem nenhum código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="93559-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span> <span data-ttu-id="93559-110">Porque o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não é aplicado, o verbo HTTP padrão ("POST") é usado.</span><span class="sxs-lookup"><span data-stu-id="93559-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="93559-111">O serviço tem uma operação, `DoMath`, que retorna um tipo complexo chamado `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="93559-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="93559-112">O tipo complexo é um tipo de contrato de dados padrão, que também não contém nenhum código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="93559-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  
  
```  
[DataContract]  
    public class MathResult  
    {  
        [DataMember]  
        public double sum;  
        [DataMember]  
        public double difference;  
        [DataMember]  
        public double product;  
        [DataMember]  
        public double quotient;  
    }  
```  
  
 <span data-ttu-id="93559-113">Crie um ponto de extremidade do AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como o exemplo de serviço AJAX básico.</span><span class="sxs-lookup"><span data-stu-id="93559-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="93559-114">O cliente ComplexTypeClientPage.aspx de página da Web contém código ASP.NET e JavaScript para invocar o serviço quando o usuário clica o **cálculos** botão na página.</span><span class="sxs-lookup"><span data-stu-id="93559-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="93559-115">O código para chamar o serviço constrói um corpo JSON e a envia usando HTTP POST, semelhante do [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="93559-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="93559-116">Após a chamada de serviço concluído com êxito, você pode acessar os membros de dados individuais (`sum`, `difference`, `product` e `quotient`) em JavaScript resultante do objeto.</span><span class="sxs-lookup"><span data-stu-id="93559-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="93559-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="93559-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="93559-118">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93559-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="93559-119">Compile a solução ComplexTypeAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="93559-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="93559-120">Navegue até http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (não abrir ComplexTypeClientPage.aspx no navegador do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="93559-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93559-121">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="93559-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="93559-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="93559-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="93559-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="93559-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="93559-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="93559-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="93559-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93559-125">See Also</span></span>  
 [<span data-ttu-id="93559-126">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="93559-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
