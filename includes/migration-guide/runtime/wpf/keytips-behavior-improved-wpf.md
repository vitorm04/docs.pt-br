---
ms.openlocfilehash: 946096cb9510ca12bbd2cecd00099142308b072a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856992"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Melhoria no comportamento das dicas de tecla no WPF

|   |   |
|---|---|
|Detalhes|O comportamento das dicas de tecla foi modificado para manter a paridade com o comportamento no Microsoft Word e no Windows Explorer. Ao verificar se o estado da dica de tecla está habilitado ou não no caso de uma <xref:System.Windows.Input.KeyEventArgs.SystemKey> (especificamente, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>) que está sendo pressionada, o WPF trata corretamente as teclas de dica de tecla. As dicas de tecla agora descartam um menu, mesmo quando ele é aberto pelo mouse.|
|Sugestão|N/D|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Type|Runtime|
