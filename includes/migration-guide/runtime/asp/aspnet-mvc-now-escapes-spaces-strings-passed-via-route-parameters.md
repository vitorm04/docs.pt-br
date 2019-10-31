---
ms.openlocfilehash: 8d058d3297471e67459164f18358b1d143465712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803188"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>O MVC do ASP.NET agora escapa espaços em cadeias de caracteres passadas por meio dos parâmetros de rota

|   |   |
|---|---|
|Detalhes|Para estar em conformidade com a RFC 2396, os espaços nos caminhos de rota agora são escapados na população dos parâmetros de ação usando uma rota. Portanto, enquanto <code>/controller/action/some data</code> anteriormente correspondia à rota <code>/controller/action/{data}</code> e fornecia <code>some data</code> como o parâmetro de dados, ele agora fornecerá <code>some%20data</code>.|
|Sugestão|O código deve ser atualizado para não escapar parâmetros de cadeia de caracteres de uma rota. Se o URI original for necessário, ele poderá ser acessado com a API <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString.|
|Escopo|Secundário|
|Versão|4.5.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

