---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234086"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException gerada pelo verificador ortográfico do WPF

|   |   |
|---|---|
|Detalhes|Ocasionalmente, os aplicativos WPF falham durante o desligamento com uma <xref:System.ObjectDisposedException?displayProperty=name> gerada pelo verificador ortográfico. Isso foi corrigido no WPF do .NET Framework 4.7 por meio do tratamento normal da exceção, garantindo que os aplicativos não sejam mais prejudicados. Observe que exceções de primeira chance ocasionais continuariam a ser observadas em aplicativos em execução em um depurador.|
|Sugestão|Atualizar para o .NET Framework 4.7|
|Escopo|Microsoft Edge|
|Versão|4.6.1|
|Tipo|Tempo de execução|
