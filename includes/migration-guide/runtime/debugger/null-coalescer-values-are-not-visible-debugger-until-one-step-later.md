---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858544"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Valores nulos de união não são visíveis no depurador até uma etapa posterior

|   |   |
|---|---|
|Detalhes|Um bug no .NET Framework 4.5 faz com que os valores definidos por meio de uma operação de união nula não fiquem visíveis no depurador imediatamente após a operação de atribuição ser executada na versão de 64 bits do Framework.|
|Sugestão|Colocar um tempo adicional no depurador fará com que o valor do local/campo seja atualizado corretamente. Além disso, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Type|Runtime|
