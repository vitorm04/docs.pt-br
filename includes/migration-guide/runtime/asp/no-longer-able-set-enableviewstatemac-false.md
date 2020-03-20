---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803168"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Não é mais possível definir EnableViewStateMac como false

|   |   |
|---|---|
|Detalhes|O ASP.NET não permite mais que os desenvolvedores especifiquem <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. O MAC (Message Authentication Code) de estado da exibição agora é obrigatório em todas as solicitações com estado de exibição embutido. Apenas aplicativos que definiram explicitamente a propriedade EnableViewStateMac como <code>false</code> são afetados.|
|Sugestão|EnableViewViewMac deve ser assumido como verdadeiro, e quaisquer erros de MAC resultantes devem ser resolvidos (como explicado [nesta orientação,](https://support.microsoft.com/kb/2915218)que contém várias resoluções dependendo das especificidades do que está causando erros de MAC).|
|Escopo|Principal|
|Versão|4.5.2|
|Type|Runtime|
