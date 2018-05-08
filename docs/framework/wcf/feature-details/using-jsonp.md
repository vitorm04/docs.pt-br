---
title: Usando JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 55f90c37dc4e94653f2233371a044a2f019b59a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-jsonp"></a>Usando JSONP

JSON preenchimento (JSONP) é um mecanismo que permite o suporte de scripts entre sites em navegadores da Web. JSONP foi projetada para a capacidade de carregar scripts de um site diferente do que o documento carregado atual foi recuperado de navegadores da Web. O mecanismo funciona por meio do preenchimento a carga de JSON com um nome de função de retorno de chamada definido pelo usuário, conforme mostrado no exemplo a seguir.

```javascript
callback({"a" = \\"b\\"});
```

No exemplo anterior, a carga de JSON, `{"a" = \\"b\\"}`, é encapsulado em uma chamada de função `callback`. A função de retorno de chamada já deve ser definida na página da Web atual. O tipo de conteúdo de uma resposta JSONP é `application/javascript`.

JSONP não é habilitado automaticamente. Para habilitá-lo, defina o `javascriptCallbackEnabled` atributo `true` em um dos pontos de extremidade padrão HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> ou <xref:System.ServiceModel.Description.WebScriptEndpoint>), conforme mostrado no exemplo a seguir.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

O nome da função de retorno de chamada pode ser especificado em uma variável de consulta chamada de retorno de chamada, conforme mostrado na seguinte URL.

`http://baseaddress/Service/RestService?callback=functionName`

Quando chamado, o serviço envia uma resposta semelhante ao seguinte.

```javascript
functionName({"root":"Something"});
```  

Você também pode especificar o nome da função de retorno de chamada, aplicando o <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> para a classe de serviço, conforme mostrado no exemplo a seguir.

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

Para o serviço mostrado anteriormente, uma solicitação é semelhante ao seguinte.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Quando chamado, o serviço responderá com o seguinte.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>Códigos de Status HTTP

Respostas JSONP com códigos de status HTTP diferente de 200 incluem um segundo parâmetro com a representação numérica do código de status HTTP, conforme mostrado no exemplo a seguir.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Validações

As validações a seguir são executadas quando JSONP está ativado:

- A infraestrutura WCF gera uma exceção se `javascriptCallback` é habilitada, um parâmetro de cadeia de caracteres de consulta de retorno de chamada está presente na solicitação e o formato da resposta é definido como JSON.

- Se a solicitação contém o parâmetro de cadeia de caracteres de consulta de retorno de chamada, mas a operação não é um HTTP GET, o parâmetro de retorno de chamada é ignorado.

- Se o nome do retorno de chamada é `null` ou a resposta não está formatada como JSONP de cadeia de caracteres vazia.

## <a name="see-also"></a>Consulte também

[Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
