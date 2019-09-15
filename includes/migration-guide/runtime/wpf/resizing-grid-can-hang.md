---
ms.openlocfilehash: eff7e7cfc8fa0b4bc8ee3a64a7c60ee21d51f466
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997541"
---
### <a name="resizing-a-grid-can-hang"></a>Redimensionar uma grade pode causar travamento

|   |   |
|---|---|
|Detalhes|Um loop infinito pode ocorrer durante o layout de um <code>T:System.Windows.Controls.Grid</code> nas seguintes circunstâncias:<ul><li>As definições de linha contêm dois *-rows, ambos declarando um MinHeight e um MaxHeight.</li><li>O conteúdo dos *-rows não ultrapassa o MaxHeight correspondente</li><li>A altura disponível da grade é ultrapassada pelo primeiro MinHeight (além de qualquer outra linha fixa ou automática)</li><li>O aplicativo é direcionado ao .NET Framework 4.7 ou aceita o algoritmo de alocação do 4.7 definindo <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></li></ul>O loop também aconteceria com mais de duas linhas, ou no caso análogo para colunas. O problema foi corrigido no .NET Framework 4.7.1.|
|Sugestão|Atualizar para o .NET Framework 4.7.1.  Como alternativa, se não precisar do algoritmo de alocação do 4.7, você poderá usar a seguinte configuração:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Version|4.7|
|Tipo|Tempo de execução|
