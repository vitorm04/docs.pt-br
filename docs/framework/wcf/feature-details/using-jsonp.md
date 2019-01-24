---
title: Usando JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 622fbdbf2674aea552cfd57f528d7cc5168cfda8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713480"
---
# <a name="using-jsonp"></a>Usando JSONP

JSONP (JSON Padding) é um mecanismo que permite o suporte a scripts entre sites em navegadores da Web. JSONP é criado em torno a capacidade de carregar scripts de um site diferente do que foi recuperado para o documento carregado atual de navegadores da Web. O mecanismo funciona, preenchendo a carga JSON com um nome de função de retorno de chamada definida pelo usuário, conforme mostrado no exemplo a seguir.

```javascript
callback({"a" = \\"b\\"});
```

No exemplo anterior, o conteúdo JSON `{"a" = \\"b\\"}`, é encapsulado em uma chamada de função, `callback`. A função de retorno de chamada já deve ser definida na página da Web atual. É o tipo de conteúdo de uma resposta JSONP `application/javascript`.

JSONP não é habilitado automaticamente. Para habilitá-lo, defina as `javascriptCallbackEnabled` de atributo para `true` em um dos pontos de extremidade padrão HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> ou <xref:System.ServiceModel.Description.WebScriptEndpoint>), conforme mostrado no exemplo a seguir.

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

Quando invocado, o serviço envia uma resposta semelhante à seguinte.

```javascript
functionName({"root":"Something"});
```  

Você também pode especificar o nome da função de retorno de chamada, aplicando o <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> à classe de serviço, conforme mostrado no exemplo a seguir.

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

Quando invocado, o serviço responde com o seguinte.

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

- A infraestrutura do WCF gera uma exceção se `javascriptCallback` é habilitado, um parâmetro de cadeia de caracteres de consulta de retorno de chamada está presente na solicitação e o formato da resposta é definido como JSON.

- Se a solicitação contém o parâmetro de cadeia de caracteres de consulta de retorno de chamada, mas a operação não é um HTTP GET, o parâmetro de retorno de chamada é ignorado.

- Se o nome do retorno de chamada é `null` ou a resposta não é formatada como JSONP de cadeia de caracteres vazia.

## <a name="see-also"></a>Consulte também

- [Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
