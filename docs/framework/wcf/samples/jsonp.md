---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183569"
---
# <a name="jsonp"></a><span data-ttu-id="d35c5-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="d35c5-102">JSONP</span></span>
<span data-ttu-id="d35c5-103">Esta amostra demonstra como apoiar json com preenchimento (JSONP) em serviços WCF REST.</span><span class="sxs-lookup"><span data-stu-id="d35c5-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="d35c5-104">JSONP é uma convenção usada para invocar scripts de domínio cruzado gerando tags de script no documento atual.</span><span class="sxs-lookup"><span data-stu-id="d35c5-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="d35c5-105">O resultado é retornado em uma função de retorno de chamada especificada.</span><span class="sxs-lookup"><span data-stu-id="d35c5-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="d35c5-106">O JSONP baseia-se na `<script src="http://..." >` ideia de que tags como podem avaliar scripts de qualquer domínio e o script recuperado por essas tags é avaliado dentro de um escopo no qual outras funções podem já ser definidas.</span><span class="sxs-lookup"><span data-stu-id="d35c5-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d35c5-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="d35c5-107">Demonstrates</span></span>
 <span data-ttu-id="d35c5-108">Scripting de domínio cruzado com JSONP.</span><span class="sxs-lookup"><span data-stu-id="d35c5-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="d35c5-109">Discussão</span><span class="sxs-lookup"><span data-stu-id="d35c5-109">Discussion</span></span>
 <span data-ttu-id="d35c5-110">A amostra inclui uma página da Web que adiciona dinamicamente um bloco de script após a página ter sido renderizada no navegador.</span><span class="sxs-lookup"><span data-stu-id="d35c5-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="d35c5-111">Este bloco de script soca um serviço `GetCustomer`WCF REST que tem uma única operação, .</span><span class="sxs-lookup"><span data-stu-id="d35c5-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="d35c5-112">O serviço WCF REST retorna o nome e endereço de um cliente embrulhado em um nome de função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d35c5-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="d35c5-113">Quando o serviço WCF REST responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web.</span><span class="sxs-lookup"><span data-stu-id="d35c5-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="d35c5-114">A injeção da tag de script e a execução da função de retorno de chamada são automaticamente manuseadas pelo ASP.NET controle AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="d35c5-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="d35c5-115">O padrão de uso é o mesmo que todos os proxies ajax ASP.NET, com a adição de uma linha para habilitar JSONP, como mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d35c5-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="d35c5-116">A página da Web pode chamar o serviço <xref:System.ServiceModel.Description.WebScriptEndpoint> WCF REST porque o serviço está usando o conjunto com `crossDomainScriptAccessEnabled` `true`.</span><span class="sxs-lookup"><span data-stu-id="d35c5-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="d35c5-117">Ambas as configurações são feitas no arquivo Web.config o \<elemento system.serviceModel>.</span><span class="sxs-lookup"><span data-stu-id="d35c5-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="d35c5-118">O ScriptManager gerencia a interação com o serviço e oculta a complexidade de implementar manualmente o acesso JSONP.</span><span class="sxs-lookup"><span data-stu-id="d35c5-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="d35c5-119">Quando `crossDomainScriptAccessEnabled` é `true` definido e o formato de resposta para uma operação é JSON, a infra-estrutura WCF inspeciona o URI da solicitação de um parâmetro de seqüência de consulta de chamada e envolve a resposta JSON com o valor do parâmetro de string de consulta de chamada.</span><span class="sxs-lookup"><span data-stu-id="d35c5-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="d35c5-120">Na amostra, a página da Web chama o serviço WCF REST com o seguinte URI.</span><span class="sxs-lookup"><span data-stu-id="d35c5-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="d35c5-121">Como o parâmetro de seqüência de `JsonPCallback`seqüeique de chamada de chamada tem um valor de , o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d35c5-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="d35c5-122">Esta resposta JSONP inclui os dados do cliente formatados como JSON, embrulhados com o nome da função de retorno de chamada que a página da Web solicitou.</span><span class="sxs-lookup"><span data-stu-id="d35c5-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="d35c5-123">O ScriptManager executará esse retorno de chamada usando uma tag de script para realizar a solicitação de domínio cruzado e, em seguida, passará o resultado para o manipulador onSuccess que foi passado para a operação GetCustomer do proxy ASP.NET a AJAX.</span><span class="sxs-lookup"><span data-stu-id="d35c5-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="d35c5-124">A amostra consiste em dois ASP.NET aplicações web: uma contém apenas um serviço WCF e outra contém a página web .aspx, que chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="d35c5-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="d35c5-125">Ao executar a solução, o Visual Studio 2012 hospedará os dois sites em diferentes portas, o que cria um ambiente onde o serviço e o cliente vivem em diferentes domínios.</span><span class="sxs-lookup"><span data-stu-id="d35c5-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d35c5-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d35c5-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d35c5-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d35c5-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d35c5-128">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="d35c5-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d35c5-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d35c5-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="d35c5-130">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="d35c5-130">To run the sample</span></span>  
  
1. <span data-ttu-id="d35c5-131">Abra a solução para a amostra JSONP.</span><span class="sxs-lookup"><span data-stu-id="d35c5-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="d35c5-132">Pressione F5 `http://localhost:26648/JSONPClientPage.aspx` para iniciar no navegador.</span><span class="sxs-lookup"><span data-stu-id="d35c5-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="d35c5-133">Observe que após as cargas da página, as entradas de texto para "Nome" e "Endereço" são preenchidas por valores.</span><span class="sxs-lookup"><span data-stu-id="d35c5-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="d35c5-134">Esses valores foram fornecidos a partir de uma chamada para o serviço WCF depois que o navegador terminou de renderizar a página.</span><span class="sxs-lookup"><span data-stu-id="d35c5-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
