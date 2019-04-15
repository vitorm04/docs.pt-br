---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236332"
---
### <a name="wpf-pointer-based-touch-stack"></a>Pilha de toque baseada em ponteiro do WPF

|   |   |
|---|---|
|Detalhes|Essa alteração possibilita habilitar uma pilha de toque/caneta do WPF baseada em WM_POINTER opcional.  Desenvolvedores que não habilitarem explicitamente essa opção não deverão ver alterações no comportamento de toque/caneta do WPF. Problemas conhecidos atuais com a pilha de toque/caneta baseada em WM_POINTER opcional:<ul><li>Não há suporte para escrita à tinta em tempo real.</li><li>Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles serão processados no thread da interface do usuário, o que pode levar a um desempenho ruim.</li><li>Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.</li><li>A manipulação pode se comportar de maneira diferente</li><li>Arrastar/soltar não mostrará comentários apropriados para entrada por toque</li><li>Isso não afeta entrada de caneta</li><li>Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta</li><li>Isso pode travar o aplicativo até que a entrada do mouse seja detectada.</li><li>Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.</li></ul>|
|Sugestão|Desenvolvedores que desejam habilitar essa pilha podem adicionar/mesclar o seguinte ao arquivo app.config do aplicativo:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Remover isso ou definir o valor como false desabilita essa pilha opcional. Observe que essa pilha está disponível somente na Atualização do Windows 10 para Criadores e superiores.|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|
