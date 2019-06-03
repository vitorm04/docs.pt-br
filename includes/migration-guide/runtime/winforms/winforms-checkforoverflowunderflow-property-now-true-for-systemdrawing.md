---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379617"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>A propriedade CheckForOverflowUnderflow do WinForm agora é true para System.Drawing

|   |   |
|---|---|
|Detalhes|A propriedade CheckForOverflowUnderflow do o assembly System.Drawing.dll está definida como true.|
|Sugestão|Anteriormente, quando os estouros ocorriam, o resultado teria sido truncado silenciosamente. Agora, uma exceção <xref:System.OverflowException?displayProperty=name> é gerada.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
