---
ms.openlocfilehash: 946096cb9510ca12bbd2cecd00099142308b072a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803100"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Melhoria no comportamento das dicas de tecla no WPF

|   |   |
|---|---|
|Detalhes|O comportamento das dicas de tecla foi modificado para manter a paridade com o comportamento no Microsoft Word e no Windows Explorer. Ao verificar se o estado da dica de tecla está habilitado ou não no caso de uma <xref:System.Windows.Input.KeyEventArgs.SystemKey> (especificamente, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>) que está sendo pressionada, o WPF trata corretamente as teclas de dica de tecla. As dicas de tecla agora descartam um menu, mesmo quando ele é aberto pelo mouse.|
|Sugestão|N/D|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Tempo de execução|
