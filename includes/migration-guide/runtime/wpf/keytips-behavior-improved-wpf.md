---
ms.openlocfilehash: d7cf32eb369e2607ee540d7188cc680b9506c261
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856992"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Melhoria no comportamento das dicas de tecla no WPF

|   |   |
|---|---|
|Detalhes|O comportamento das dicas de tecla foi modificado para manter a paridade com o comportamento no Microsoft Word e no Windows Explorer. Ao verificar se o estado da dica de tecla está habilitado ou não no caso de uma <xref:System.Windows.Input.KeyEventArgs.SystemKey> (especificamente, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>) que está sendo pressionada, o WPF trata corretamente as teclas de dica de tecla. As dicas de tecla agora descartam um menu, mesmo quando ele é aberto pelo mouse.|
|Sugestão|N/D|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Tempo de execução|

