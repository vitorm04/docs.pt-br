---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858544"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Valores nulos de união não são visíveis no depurador até uma etapa posterior

|   |   |
|---|---|
|Detalhes|Um bug no .NET Framework 4.5 faz com que os valores definidos por meio de uma operação de união nula não fiquem visíveis no depurador imediatamente após a operação de atribuição ser executada na versão de 64 bits do Framework.|
|Sugestão|Colocar um tempo adicional no depurador fará com que o valor do local/campo seja atualizado corretamente. Além disso, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|

