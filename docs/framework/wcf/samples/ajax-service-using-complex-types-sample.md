---
title: Exemplo de serviço de AJAX utilizando tipos complexos
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: c284fbef36ee7f6dda725ba9a3db9b98fb1549ed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="a8cc4-102">Exemplo de serviço de AJAX utilizando tipos complexos</span><span class="sxs-lookup"><span data-stu-id="a8cc4-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="a8cc4-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço ASP.NET Asynchronous JavaScript e XML (AJAX) que cria instâncias de tipos complexos e envia-los entre o cliente como JSON JavaScript Object Notation () e de serviço.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="a8cc4-104">Você pode acessar um serviço de AJAX usando código JavaScript de um cliente de navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="a8cc4-105">Este exemplo se baseia o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="a8cc4-106">Suporte do AJAX no WCF é otimizado para uso com o ASP.NET AJAX por meio de <xref:System.Web.UI.ScriptManager> controle.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="a8cc4-107">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte o [AJAX exemplos](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="a8cc4-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8cc4-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a8cc4-109">O serviço no exemplo a seguir é um serviço WCF, sem nenhum código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="a8cc4-110">Porque o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não é aplicado, o verbo HTTP padrão ("POST") é usado.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="a8cc4-111">O serviço tem uma operação, `DoMath`, que retorna um tipo complexo chamado `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="a8cc4-112">O tipo complexo é um tipo de contrato de dados padrão, que também não contém nenhum código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

```csharp
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

 <span data-ttu-id="a8cc4-113">Crie um ponto de extremidade do AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como o exemplo de serviço AJAX básico.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="a8cc4-114">O cliente ComplexTypeClientPage.aspx de página da Web contém código ASP.NET e JavaScript para invocar o serviço quando o usuário clica o **cálculos** botão na página.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="a8cc4-115">O código para chamar o serviço constrói um corpo JSON e a envia usando HTTP POST, semelhante do [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="a8cc4-116">Após a chamada de serviço concluído com êxito, você pode acessar os membros de dados individuais (`sum`, `difference`, `product` e `quotient`) em JavaScript resultante do objeto.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8cc4-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a8cc4-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a8cc4-118">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8cc4-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a8cc4-119">Compile a solução ComplexTypeAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8cc4-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a8cc4-120">Navegue até http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (não abrir ComplexTypeClientPage.aspx no navegador do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="a8cc4-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8cc4-121">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a8cc4-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a8cc4-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8cc4-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a8cc4-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="a8cc4-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8cc4-125">See Also</span></span>  
 [<span data-ttu-id="a8cc4-126">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="a8cc4-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
