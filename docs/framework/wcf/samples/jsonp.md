---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 37da57a000376f972cd6da9e04be46ddec1b7144
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329655"
---
# <a name="jsonp"></a><span data-ttu-id="eb9f1-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="eb9f1-102">JSONP</span></span>
<span data-ttu-id="eb9f1-103">Este exemplo demonstra como dar suporte a JSON com preenchimento (JSONP) nos serviços REST do WCF.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="eb9f1-104">O JSONP é uma convenção usada para invocar scripts entre domínios por gerar marcações de script no documento atual.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="eb9f1-105">O resultado é retornado em uma função de retorno de chamada especificados.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="eb9f1-106">JSONP é baseado na ideia de que as marcas como `<script src="http://..." >` pode avaliar qualquer domínio de scripts e o script recuperado por essas marcas é avaliado dentro de um escopo em que as outras funções já podem ser definidas.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eb9f1-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="eb9f1-107">Demonstrates</span></span>
 <span data-ttu-id="eb9f1-108">Entre domínios scripts com o JSONP.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="eb9f1-109">Discussão</span><span class="sxs-lookup"><span data-stu-id="eb9f1-109">Discussion</span></span>
 <span data-ttu-id="eb9f1-110">O exemplo inclui uma página da Web que adiciona dinamicamente um bloco de script depois que a página foi renderizada no navegador.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="eb9f1-111">Este bloco de script chama um serviço REST do WCF que tem uma única operação, `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="eb9f1-112">O serviço REST WCF retorna o nome e endereço encapsulado em um nome de função de retorno de chamada de um cliente.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="eb9f1-113">Quando o serviço REST WCF responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="eb9f1-114">A injeção da marca do script e a execução da função de retorno de chamada são tratados automaticamente pelo controle ScriptManager do AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="eb9f1-115">O padrão de uso é o mesmo que todos os proxies do ASP.NET AJAX, com a adição de uma linha para habilitar o JSONP, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="eb9f1-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="eb9f1-116">A página da Web pode chamar o serviço REST WCF porque o serviço está usando o <xref:System.ServiceModel.Description.WebScriptEndpoint> com `crossDomainScriptAccessEnabled` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="eb9f1-117">Ambas essas configurações são feitas no arquivo Web. config sob o \<System. ServiceModel > elemento.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="eb9f1-118">ScriptManager gerencia a interação com o serviço e oculta a complexidade de implementar manualmente acesso JSONP.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="eb9f1-119">Quando `crossDomainScriptAccessEnabled` é definido como `true` e o formato da resposta para uma operação é JSON, a infraestrutura do WCF inspeciona o URI da solicitação para um parâmetro de cadeia de caracteres de consulta de retorno de chamada e encapsula a resposta JSON com o valor da cadeia de caracteres de consulta de retorno de chamada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="eb9f1-120">No exemplo, a página da Web chama o serviço de REST do WCF com o seguinte URI.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="eb9f1-121">Porque o parâmetro de cadeia de caracteres de consulta de retorno de chamada tem um valor de `JsonPCallback`, o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="eb9f1-122">Essa resposta JSONP inclui os dados formatados como JSON, empacotado com o nome da função de retorno de chamada que solicitou a página da Web do cliente.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="eb9f1-123">ScriptManager executará esse retorno de chamada usando uma marca de script para realizar a solicitação entre domínios e, em seguida, passe o resultado para o manipulador onSuccess que foi passado para a operação GetCustomer do proxy com o ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="eb9f1-124">O exemplo consiste em dois aplicativos de web do ASP.NET: um contém apenas um serviço WCF, e outra contém a página da Web. aspx, que chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="eb9f1-125">Ao executar a solução, o Visual Studio 2012 hospedará os dois sites em portas diferentes, que cria um ambiente em que o serviço e o cliente residem em domínios diferentes.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="eb9f1-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eb9f1-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eb9f1-128">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb9f1-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="eb9f1-130">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="eb9f1-130">To run the sample</span></span>  
  
1. <span data-ttu-id="eb9f1-131">Abra a solução do exemplo JSONP.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="eb9f1-132">Pressione F5 para iniciar `http://localhost:26648/JSONPClientPage.aspx` no navegador.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="eb9f1-133">Observe que, depois que a página for carregada, as entradas de texto para "Name" e "Address" são preenchidas por valores.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="eb9f1-134">Esses valores foram fornecidos de uma chamada para o serviço WCF depois que o navegador concluída a renderização da página.</span><span class="sxs-lookup"><span data-stu-id="eb9f1-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
