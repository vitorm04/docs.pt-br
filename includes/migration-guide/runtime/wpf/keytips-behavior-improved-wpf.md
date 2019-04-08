---
ms.openlocfilehash: d7cf32eb369e2607ee540d7188cc680b9506c261
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760713"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Melhoria no comportamento das dicas de tecla no WPF

|   |   |
|---|---|
|Detalhes|O comportamento das dicas de tecla foi modificado para manter a paridade com o comportamento no Microsoft Word e no Windows Explorer. Ao verificar se o estado da dica de tecla está habilitado ou não no caso de uma <xref:System.Windows.Input.KeyEventArgs.SystemKey> (especificamente, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>) que está sendo pressionada, o WPF trata corretamente as teclas de dica de tecla. As dicas de tecla agora descartam um menu, mesmo quando ele é aberto pelo mouse.|
|Sugestão|N/D|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Tempo de execução|

