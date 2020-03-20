---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804665"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET não é mais compatível com a qualificação do namespace parcial para APIs System.Windows

|   |   |
|---|---|
|Detalhes|Começando com o .NET Framework 4.5.2, os projetos VB.NET não podem especificar APIs System.Windows com namespaces parcialmente qualificados. Por exemplo, fazer referência a <code>Windows.Forms.DialogResult</code> falhará. Em vez disso, o código deve fazer referência ao nome totalmente qualificado (<xref:System.Windows.Forms.DialogResult>) ou importar o namespace específico e simplesmente fazer referência a <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Sugestão|O código deve ser atualizado para fazer referência as APIs <code>System.Windows</code> com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.|
|Escopo|Secundária|
|Versão|4.5.2|
|Type|Redirecionando|
