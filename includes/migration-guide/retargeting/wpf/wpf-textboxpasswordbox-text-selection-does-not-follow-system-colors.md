---
ms.openlocfilehash: 3f88c8b80518aa65c082dc3da2d75b5221dd00f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773990"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>A seleção de texto da caixa de TextBox/PasswordBox do WPF não segue as cores do sistema

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.1 e nas versões anteriores, o <code>System.Windows.Controls.TextBox</code> e o <code>System.Windows.Controls.PasswordBox</code> do WPF somente podiam renderizar uma seleção de texto na camada de Adorno. Em alguns temas do sistema, isso obstruía o texto, dificultando a leitura.  No .NET Framework 4.7.2 e nas versões posteriores, os desenvolvedores têm a opção de habilitar um esquema de renderização de seleção não baseado no Adorno que elimina esse problema.|
|Sugestão|O desenvolvedor que desejar utilizar essa alteração precisará definir o seguinte sinalizador de AppContext adequadamente.  Para utilizar esse recurso, a versão instalada do .NET Framework precisará ser a 4.7.2 ou superior. Para habilitar a seleção não baseada em Adorno, use o sinalizador de AppContext a seguir.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Redirecionando|
