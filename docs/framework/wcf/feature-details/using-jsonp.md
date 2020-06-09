---
title: Usando JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 82290319b5d8b58708f0b2ebf40522ee76127b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594953"
---
# <a name="using-jsonp"></a><span data-ttu-id="b07aa-102">Usando JSONP</span><span class="sxs-lookup"><span data-stu-id="b07aa-102">Using JSONP</span></span>

<span data-ttu-id="b07aa-103">O preenchimento JSON (JSONP) é um mecanismo que permite o suporte a scripts entre sites em navegadores da Web.</span><span class="sxs-lookup"><span data-stu-id="b07aa-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="b07aa-104">O JSONP foi projetado em relação à capacidade dos navegadores da Web de carregar scripts de um site diferente daquele no qual o documento carregado atual foi recuperado.</span><span class="sxs-lookup"><span data-stu-id="b07aa-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="b07aa-105">O mecanismo funciona preenchendo a carga JSON com um nome de função de retorno de chamada definido pelo usuário, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b07aa-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="b07aa-106">No exemplo anterior, o conteúdo JSON, `{"a" = \\"b\\"}` , é encapsulado em uma chamada de função, `callback` .</span><span class="sxs-lookup"><span data-stu-id="b07aa-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="b07aa-107">A função de retorno de chamada já deve estar definida na página da Web atual.</span><span class="sxs-lookup"><span data-stu-id="b07aa-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="b07aa-108">O tipo de conteúdo de uma resposta JSONP é `application/javascript` .</span><span class="sxs-lookup"><span data-stu-id="b07aa-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="b07aa-109">JSONP não é habilitado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b07aa-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="b07aa-110">Para habilitá-lo, defina o `javascriptCallbackEnabled` atributo como `true` em um dos pontos de extremidade padrão http ( <xref:System.ServiceModel.Description.WebHttpEndpoint> ou <xref:System.ServiceModel.Description.WebScriptEndpoint> ), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b07aa-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="b07aa-111">O nome da função de retorno de chamada pode ser especificado em uma variável de consulta chamada callback, conforme mostrado na URL a seguir.</span><span class="sxs-lookup"><span data-stu-id="b07aa-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="b07aa-112">Quando invocado, o serviço envia uma resposta como a seguinte.</span><span class="sxs-lookup"><span data-stu-id="b07aa-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="b07aa-113">Você também pode especificar o nome da função de retorno de chamada aplicando o <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> à classe de serviço, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b07aa-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

<span data-ttu-id="b07aa-114">Para o serviço mostrado anteriormente, uma solicitação é semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="b07aa-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="b07aa-115">Quando invocado, o serviço responde com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="b07aa-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="b07aa-116">Códigos de status HTTP</span><span class="sxs-lookup"><span data-stu-id="b07aa-116">HTTP Status Codes</span></span>

<span data-ttu-id="b07aa-117">As respostas JSONP com códigos de status HTTP diferentes de 200 incluem um segundo parâmetro com a representação numérica do código de status HTTP, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b07aa-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="b07aa-118">Validações</span><span class="sxs-lookup"><span data-stu-id="b07aa-118">Validations</span></span>

<span data-ttu-id="b07aa-119">As validações a seguir são executadas quando o JSONP está habilitado:</span><span class="sxs-lookup"><span data-stu-id="b07aa-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="b07aa-120">A infraestrutura do WCF gera uma exceção se `javascriptCallback` estiver habilitada, um parâmetro de cadeia de caracteres de consulta de retorno de chamada está presente na solicitação e o formato de resposta é definido como JSON.</span><span class="sxs-lookup"><span data-stu-id="b07aa-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="b07aa-121">Se a solicitação contiver o parâmetro de cadeia de caracteres de consulta de retorno de chamada, mas a operação não for um HTTP GET, o parâmetro de retorno de chamada será ignorado.</span><span class="sxs-lookup"><span data-stu-id="b07aa-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="b07aa-122">Se o nome do retorno de chamada for `null` ou uma cadeia de caracteres vazia, a resposta não será formatada como JSONP.</span><span class="sxs-lookup"><span data-stu-id="b07aa-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="b07aa-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="b07aa-123">See also</span></span>

- [<span data-ttu-id="b07aa-124">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="b07aa-124">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
