---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761241"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException gerada pelo verificador ortográfico do WPF

|   |   |
|---|---|
|Detalhes|Ocasionalmente, os aplicativos WPF falham durante o desligamento com uma <xref:System.ObjectDisposedException?displayProperty=name> gerada pelo verificador ortográfico. Isso foi corrigido no WPF do .NET Framework 4.7 por meio do tratamento normal da exceção, garantindo que os aplicativos não sejam mais prejudicados. Observe que exceções de primeira chance ocasionais continuariam a ser observadas em aplicativos em execução em um depurador.|
|Sugestão|Atualizar para o .NET Framework 4.7|
|Escopo|Microsoft Edge|
|Versão|4.6.1|
|Tipo|Tempo de execução|

