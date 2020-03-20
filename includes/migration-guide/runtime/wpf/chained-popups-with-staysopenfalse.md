---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857269"
---
### <a name="chained-popups-with-staysopenfalse"></a>Pop-ups encadeados com StaysOpen=False

|   |   |
|---|---|
|Detalhes|Um pop-up com StaysOpen=False deve fechar quando você clica fora dele. Quando dois ou mais pop-ups do tipo estão encadeados (por exemplo, quando um contém o outro), há muitos problemas, incluindo:<ul><li>Abra dois níveis, clique fora do P2, mas dentro do P1.  Nada acontecerá.</li><li>Abra dois níveis, clique fora do P1.  Ambos pop-ups serão fechados.</li><li>Abra e feche dois níveis.  Em seguida, tente abrir novamente o P2.  Nada acontecerá.</li><li>Tente abrir três níveis.  Não é possível fazer isso.  (Ou nada acontece ou os dois primeiros níveis fecham, dependendo de onde você clica.) Esses casos (e outras variantes) agora funcionam como esperado.</li></ul>|
|Escopo|Microsoft Edge|
|Versão|4.7.1|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
