---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236719"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET não é mais compatível com a qualificação do namespace parcial para APIs System.Windows

|   |   |
|---|---|
|Detalhes|Começando com o .NET Framework 4.5.2, os projetos VB.NET não podem especificar APIs System.Windows com namespaces parcialmente qualificados. Por exemplo, fazer referência a <code>Windows.Forms.DialogResult</code> falhará. Em vez disso, o código deve fazer referência ao nome totalmente qualificado (<xref:System.Windows.Forms.DialogResult>) ou importar o namespace específico e simplesmente fazer referência a <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Sugestão|O código deve ser atualizado para fazer referência as APIs <code>System.Windows</code> com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.|
|Escopo|Secundário|
|Versão|4.5.2|
|Tipo|Redirecionando|
