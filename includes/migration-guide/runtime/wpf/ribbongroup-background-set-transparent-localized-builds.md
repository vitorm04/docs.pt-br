---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802544"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>Tela de fundo RibbonGroup é definida como transparente em builds localizados

|   |   |
|---|---|
|Detalhes|A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim. Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, que, por sua vez, garante que o pincel correto seja selecionado.|
|Sugestão|Atualizar para o .NET Framework 4.7|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Type|Runtime|
