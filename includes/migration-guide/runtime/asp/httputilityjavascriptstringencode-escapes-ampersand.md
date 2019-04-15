---
ms.openlocfilehash: 0056baa1e5f0cdc5bfcf8b0e83c9490ec5722926
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235101"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode escapa o E comercial

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> ignora o caractere E comercial (&amp;).|
|Sugestão|Se seu aplicativo depende do comportamento anterior desse método, você poderá adicionar uma definição aspnet:JavaScriptDoNotEncodeAmpersand ao [elemento appSettings do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) no seu arquivo de configuração.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
