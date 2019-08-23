---
title: Exemplo de serviço de AJAX utilizando tipos complexos
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 98d33c250be31ac43eef6d76ade997a30af87090
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923686"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="203e7-102">Exemplo de serviço de AJAX utilizando tipos complexos</span><span class="sxs-lookup"><span data-stu-id="203e7-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="203e7-103">Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço de JavaScript e XML (AJAX) assíncrono do ASP.NET que cria instâncias de tipos complexos e os envia entre o serviço e o cliente como JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="203e7-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="203e7-104">Você pode acessar um serviço AJAX usando o código JavaScript de um cliente de navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="203e7-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="203e7-105">Este exemplo baseia-se no exemplo de [serviço básico Ajax](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="203e7-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="203e7-106">O suporte ao AJAX no WCF é otimizado para uso com o <xref:System.Web.UI.ScriptManager> ASP.NET AJAX por meio do controle.</span><span class="sxs-lookup"><span data-stu-id="203e7-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="203e7-107">Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="203e7-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="203e7-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="203e7-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="203e7-109">O serviço no exemplo a seguir é um serviço WCF sem código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="203e7-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="203e7-110">Como o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não é aplicado, o verbo HTTP padrão ("post") é usado.</span><span class="sxs-lookup"><span data-stu-id="203e7-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="203e7-111">O serviço tem uma operação, `DoMath`, que retorna um tipo complexo chamado `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="203e7-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="203e7-112">O tipo complexo é um tipo de contrato de dados padrão, que também não contém nenhum código específico do AJAX.</span><span class="sxs-lookup"><span data-stu-id="203e7-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

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

 <span data-ttu-id="203e7-113">Crie um ponto de extremidade AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como no exemplo de serviço básico Ajax.</span><span class="sxs-lookup"><span data-stu-id="203e7-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="203e7-114">A página da Web do cliente ComplexTypeClientPage. aspx contém o código ASP.NET e JavaScript para invocar o serviço quando o usuário clica no botão **executar cálculo** na página.</span><span class="sxs-lookup"><span data-stu-id="203e7-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="203e7-115">O código para invocar o serviço constrói um corpo JSON e o envia usando HTTP POST, semelhante ao [serviço AJAX usando o exemplo http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .</span><span class="sxs-lookup"><span data-stu-id="203e7-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="203e7-116">Depois que a chamada de serviço for realizada com sucesso, você poderá acessar os`sum`membros de `product` dados `quotient`individuais (, `difference`e) no objeto JavaScript resultante.</span><span class="sxs-lookup"><span data-stu-id="203e7-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="203e7-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="203e7-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="203e7-118">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="203e7-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="203e7-119">Crie a solução ComplexTypeAjaxService. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="203e7-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="203e7-120">Navegue até `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (não abra ComplexTypeClientPage. aspx no navegador do diretório do projeto).</span><span class="sxs-lookup"><span data-stu-id="203e7-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="203e7-121">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="203e7-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="203e7-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="203e7-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="203e7-123">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="203e7-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="203e7-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="203e7-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="203e7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="203e7-125">See also</span></span>

- [<span data-ttu-id="203e7-126">Serviço AJAX básico</span><span class="sxs-lookup"><span data-stu-id="203e7-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
