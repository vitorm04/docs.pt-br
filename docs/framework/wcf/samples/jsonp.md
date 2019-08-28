---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9f24ccb5ba14e0b43f0e3f911a1672db5821d228
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039550"
---
# <a name="jsonp"></a><span data-ttu-id="8d3dc-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="8d3dc-102">JSONP</span></span>
<span data-ttu-id="8d3dc-103">Este exemplo demonstra como dar suporte a JSON com preenchimento (JSONP) nos serviços REST do WCF.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="8d3dc-104">JSONP é uma convenção usada para invocar scripts entre domínios, gerando marcas de script no documento atual.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="8d3dc-105">O resultado é retornado em uma função de retorno de chamada especificada.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="8d3dc-106">O JSONP é baseado na ideia de que marcas como `<script src="http://..." >` o podem avaliar scripts de qualquer domínio e o script recuperado por essas marcas é avaliado em um escopo no qual outras funções já podem estar definidas.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8d3dc-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="8d3dc-107">Demonstrates</span></span>
 <span data-ttu-id="8d3dc-108">Script entre domínios com o JSONP.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="8d3dc-109">Discussão</span><span class="sxs-lookup"><span data-stu-id="8d3dc-109">Discussion</span></span>
 <span data-ttu-id="8d3dc-110">O exemplo inclui uma página da Web que adiciona dinamicamente um bloco de script depois que a página é processada no navegador.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="8d3dc-111">Esse bloco de script chama um serviço REST do WCF que tem uma única `GetCustomer`operação,.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="8d3dc-112">O serviço REST do WCF retorna o nome e o endereço do cliente encapsulados em um nome de função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="8d3dc-113">Quando o serviço REST do WCF responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="8d3dc-114">A injeção da marca de script e a execução da função de retorno de chamada é manipulada automaticamente pelo controle ScriptManager do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="8d3dc-115">O padrão de uso é o mesmo que todos os proxies AJAX do ASP.NET, com a adição de uma linha para habilitar o JSONP, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8d3dc-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="8d3dc-116">A página da Web pode chamar o serviço REST do WCF porque o serviço está <xref:System.ServiceModel.Description.WebScriptEndpoint> usando `crossDomainScriptAccessEnabled` o com `true`definido como.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="8d3dc-117">Essas duas configurações são feitas no arquivo \<Web. config no elemento System. ServiceModel >.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 <span data-ttu-id="8d3dc-118">O ScriptManager gerencia a interação com o serviço e oculta a complexidade de implementar manualmente o acesso JSONP.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="8d3dc-119">Quando `crossDomainScriptAccessEnabled` é definido como `true` e o formato de resposta para uma operação é JSON, a infraestrutura do WCF inspeciona o URI da solicitação de um parâmetro de cadeia de caracteres de consulta de retorno de chamada e encapsula a resposta JSON com o valor da cadeia de caracteres de consulta de retorno de chamada meter.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="8d3dc-120">No exemplo, a página da Web chama o serviço REST do WCF com o URI a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="8d3dc-121">Como o parâmetro de cadeia de caracteres de consulta de `JsonPCallback`retorno de chamada tem um valor de, o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="8d3dc-122">Essa resposta JSONP inclui os dados do cliente formatados como JSON, encapsulados com o nome da função de retorno de chamada que a página da Web solicitou.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="8d3dc-123">O ScriptManager executará esse retorno de chamada usando uma marca de script para realizar a solicitação entre domínios e, em seguida, passará o resultado para o manipulador OnSuccess que foi passado para a operação GetCustomer do proxy AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="8d3dc-124">O exemplo consiste em dois aplicativos Web ASP.NET: um contém apenas um serviço WCF, e outro contém a página do Web. aspx, que chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="8d3dc-125">Ao executar a solução, o Visual Studio 2012 hospedará os dois sites em portas diferentes, o que cria um ambiente em que o serviço e o cliente residem em domínios diferentes.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d3dc-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d3dc-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8d3dc-128">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d3dc-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="8d3dc-130">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="8d3dc-130">To run the sample</span></span>  
  
1. <span data-ttu-id="8d3dc-131">Abra a solução para o exemplo JSONP.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="8d3dc-132">Pressione F5 para iniciar `http://localhost:26648/JSONPClientPage.aspx` no navegador.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="8d3dc-133">Observe que, depois que a página é carregada, as entradas de texto para "nome" e "endereço" são preenchidas por valores.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="8d3dc-134">Esses valores foram fornecidos de uma chamada para o serviço WCF depois que o navegador terminar de renderizar a página.</span><span class="sxs-lookup"><span data-stu-id="8d3dc-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
