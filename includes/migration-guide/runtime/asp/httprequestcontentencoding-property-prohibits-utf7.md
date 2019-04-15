---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235032"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>A propriedade HttpRequest.ContentEncoding proíbe a UTF7

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, a codificação UTF-7 está proibida nos corpos de <xref:System.Web.HttpRequest?displayProperty=name>. Os dados para aplicativos que dependem de dados de entrada UTF-7 não serão decodificados corretamente em alguns casos.|
|Sugestão|De modo ideal, os aplicativos devem ser atualizados para não usar a codificação UTF-7 em <xref:System.Web.HttpRequest?displayProperty=name>. De modo alternativo, o comportamento herdado pode ser restaurado usando o atributo <code>aspnet:AllowUtf7RequestContentEncoding</code> do elemento [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md).|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
