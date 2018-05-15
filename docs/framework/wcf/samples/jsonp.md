---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9002597ef662c78b6519ab0c04700cddf7ee3714
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="jsonp"></a><span data-ttu-id="a977d-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="a977d-102">JSONP</span></span>
<span data-ttu-id="a977d-103">Este exemplo demonstra como dar suporte a JSON com preenchimento (JSONP) em serviços WCF REST.</span><span class="sxs-lookup"><span data-stu-id="a977d-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="a977d-104">JSONP é uma convenção usada para chamar scripts de domínio cruzado por gerar marcações de script no documento atual.</span><span class="sxs-lookup"><span data-stu-id="a977d-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="a977d-105">O resultado é retornado em uma função de retorno de chamada especificada.</span><span class="sxs-lookup"><span data-stu-id="a977d-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="a977d-106">JSONP baseia-se a ideia marcas como `<script src="http://..." >` pode avaliar qualquer domínio de scripts e o script recuperado por essas marcas é avaliado em um escopo no qual outras funções já podem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="a977d-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a977d-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="a977d-107">Demonstrates</span></span>  
 <span data-ttu-id="a977d-108">Entre domínios de script com JSONP.</span><span class="sxs-lookup"><span data-stu-id="a977d-108">Cross-domain scripting with JSONP.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a977d-109">Discussão</span><span class="sxs-lookup"><span data-stu-id="a977d-109">Discussion</span></span>  
 <span data-ttu-id="a977d-110">O exemplo inclui uma página da Web que adiciona dinamicamente um bloco de script após a página foi renderizada no navegador.</span><span class="sxs-lookup"><span data-stu-id="a977d-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="a977d-111">Este bloco de script chama um serviço WCF REST com uma única operação, `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="a977d-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="a977d-112">O serviço WCF REST retorna o nome e endereço encapsulado em um nome de função de retorno de chamada do cliente.</span><span class="sxs-lookup"><span data-stu-id="a977d-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="a977d-113">Quando o serviço WCF REST responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web.</span><span class="sxs-lookup"><span data-stu-id="a977d-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="a977d-114">A inclusão da marca do script e a execução da função de retorno de chamada são tratados automaticamente pelo controle ScriptManager do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="a977d-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="a977d-115">O padrão de uso é o mesmo que todos os proxies do ASP.NET AJAX, com a adição de uma linha para habilitar JSONP, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a977d-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="a977d-116">A página da Web pode chamar o serviço WCF REST porque o serviço está usando o <xref:System.ServiceModel.Description.WebScriptEndpoint> com `crossDomainScriptAccessEnabled` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="a977d-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="a977d-117">Ambas essas configurações são feitas no arquivo Web. config sob o \<System. ServiceModel > elemento.</span><span class="sxs-lookup"><span data-stu-id="a977d-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>  
  
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
  
 <span data-ttu-id="a977d-118">ScriptManager gerencia a interação com o serviço e distância oculta a complexidade da implementação manualmente acesso JSONP.</span><span class="sxs-lookup"><span data-stu-id="a977d-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="a977d-119">Quando `crossDomainScriptAccessEnabled` é definido como `true` e o formato de resposta para uma operação é JSON, a infraestrutura WCF inspeciona o URI da solicitação de um parâmetro de cadeia de caracteres de consulta de retorno de chamada e encapsula a resposta JSON com o valor da cadeia de caracteres de consulta de retorno de chamada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a977d-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="a977d-120">No exemplo, a página da Web chama o serviço WCF REST com o URI a seguir.</span><span class="sxs-lookup"><span data-stu-id="a977d-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 <span data-ttu-id="a977d-121">Porque o parâmetro de cadeia de caracteres de consulta de retorno de chamada tem um valor de `JsonPCallback`, o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a977d-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 <span data-ttu-id="a977d-122">Essa resposta JSONP inclui os dados formatados como JSON, empacotado com o nome da função de retorno de chamada solicitou a página da Web do cliente.</span><span class="sxs-lookup"><span data-stu-id="a977d-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="a977d-123">ScriptManager executar esse retorno de chamada usando uma marca de script para fazer a solicitação de domínio cruzado e, em seguida, passe o resultado para o manipulador de onSuccess que foi passado para a operação GetCustomer do proxy do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="a977d-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>  
  
 <span data-ttu-id="a977d-124">O exemplo consiste em dois aplicativos da web ASP.NET: um contém apenas um serviço WCF e a outra contém a página da Web. aspx, que chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="a977d-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="a977d-125">Ao executar a solução, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] hospedará os dois sites em portas diferentes, que cria um ambiente onde o serviço e o cliente residir em domínios diferentes.</span><span class="sxs-lookup"><span data-stu-id="a977d-125">When running the solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a977d-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a977d-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a977d-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a977d-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a977d-128">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a977d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a977d-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a977d-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="a977d-130">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="a977d-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="a977d-131">Abra a solução do exemplo JSONP.</span><span class="sxs-lookup"><span data-stu-id="a977d-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="a977d-132">Pressione F5 para iniciar `http://localhost:26648/JSONPClientPage.aspx` no navegador.</span><span class="sxs-lookup"><span data-stu-id="a977d-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3.  <span data-ttu-id="a977d-133">Observe que, depois que a página for carregada, as entradas de texto para "Nome" e "Address" são preenchidas por valores.</span><span class="sxs-lookup"><span data-stu-id="a977d-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="a977d-134">Esses valores foram fornecidos de uma chamada para o serviço WCF após o navegador renderização da página.</span><span class="sxs-lookup"><span data-stu-id="a977d-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
