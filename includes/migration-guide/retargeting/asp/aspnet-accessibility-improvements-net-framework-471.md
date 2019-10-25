---
ms.openlocfilehash: f18b96eaeec8a6427ffb7776327517989d0225d0
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887719"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Melhorias de acessibilidade do ASP.NET no .NET Framework 4.7.1

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.7.1, o ASP.NET melhorou o funcionamento dos controles da Web ASP.NET com a tecnologia de acessibilidade no Visual Studio para dar melhor suporte a clientes do ASP.NET.  Isso inclui as seguintes alterações:<ul><li>Alterações para implementar padrões de acessibilidade de interface do usuário ausentes nos controles, como a caixa de diálogo Adicionar Campo no assistente de Exibição de Detalhes ou a caixa de diálogo Configurar ListView do assistente ListView.</li><li>Alterações para melhorar a exibição no modo de Alto Contraste, como o Editor de Campos do Pager de Dados.</li><li>Alterações para melhorar as experiências de navegação por teclado, como a caixa de diálogo Campos no assistente Editar Campos do Pager do controle DataPager, a caixa de diálogo Configurar ObjectContext ou a caixa de diálogo Configurar Seleção de Dados do assistente Configurar Fonte de Dados.</li></ul>|
|Sugestão|**Como aceitar ou recusar essas alterações**<br>Para que o Visual Studio Designer se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.7.1 ou posterior. O aplicativo Web pode se beneficiar dessas alterações de uma das seguintes maneiras:<ul><li>Instalar o Visual Studio 2017 15.3 ou posterior, que dá suporte a novas funcionalidades de acessibilidade com a seguinte opção de AppContext por padrão.</li><li>Recusar os comportamentos de acessibilidade herdados adicionando a opção de AppContext <code>Switch.UseLegacyAccessibilityFeatures</code> à seção <code>&lt;runtime&gt;</code> do arquivo devenv.exe.config e configurando-a como <code>false</code>, como mostra o exemplo a seguir.</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Aplicativos destinados ao .NET Framework 4.7.1 ou posterior que desejam preservar o comportamento de acessibilidade herdado pode aceitar o uso das funcionalidades de acessibilidade herdadas definindo explicitamente essa opção de AppContext como <code>true</code>.|
|Escopo|Secundário|
|Version|4.7.1|
|Digite|Redirecionando|
