---
ms.openlocfilehash: ea0e1583cd611a624cf2d2edf9defb2294eb89d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802655"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET Corrigir a manipulação de InputAttributes e LabelAttributes para controle CheckBox de WebForms

|   |   |
|---|---|
|Detalhes|Para aplicativos que direcionam o .NET Framework 4.7.2 e versões anteriores, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> e <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> programaticamente adicionados a um controle <xref:System.Web.UI.WebControls.CheckBox> de WebForms são perdidos após o postback. Para aplicativos que direcionam o .NET Framework 4.8 ou versões posteriores, eles são preservados após o postback.|
|Sugestão|Para o comportamento correto para restaurar atributos em postback, defina <code>targetFrameworkVersion</code> como 4.8 ou superior. Por exemplo: <pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Defini-la como mais baixa ou não definir preserva o comportamento antigo incorreto.|
|Escopo|Unknown (desconhecido)|
|Versão|4.8|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
