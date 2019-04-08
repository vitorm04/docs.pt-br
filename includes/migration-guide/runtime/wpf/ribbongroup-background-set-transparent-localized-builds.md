---
ms.openlocfilehash: 9500907c6a1ba5b27008dcad4c9b47aef9092106
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760593"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>Tela de fundo RibbonGroup é definida como transparente em builds localizados

|   |   |
|---|---|
|Detalhes|A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim. Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, que, por sua vez, garante que o pincel correto seja selecionado.|
|Sugestão|Atualizar para o .NET Framework 4.7|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Tempo de execução|

