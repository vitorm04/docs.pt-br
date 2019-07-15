---
ms.openlocfilehash: a4f27c0b2bf95ed19e485881aba3c52073114117
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804527"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>Arredondamento de layout do WPF foi alterado

|   |   |
|---|---|
|Detalhes|A maneira como as margens são arredondadas, bem como as bordas e a tela de fundo dentro delas, foi alterada. Como resultado dessa alteração:<ul><li>A largura ou altura dos elementos pode aumentar ou reduzir em um pixel no máximo.</li><li>O posicionamento de um objeto pode ser movido até um pixel, no máximo.</li><li>Os elementos centralizados podem estar vertical ou horizontalmente fora do centro em, no máximo, um pixel.</li></ul>Por padrão, esse novo layout é habilitado somente para aplicativos que se destinam ao .NET Framework 4.6.|
|Sugestão|Uma vez que essa modificação tende a eliminar a distorção da direita ou da parte inferior dos controles do WPF em DPIs altos, os aplicativos que de destinam a versões anteriores do .NET Framework, mas estão sendo executados no .NET Framework 4.6, podem aderir a esse novo comportamento adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>Os aplicativos que são direcionados ao .NET Framework 4.6, mas querem que os controles do WPF sejam renderizados usando o algoritmo de layout anterior podem fazer isso adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Redirecionando|

