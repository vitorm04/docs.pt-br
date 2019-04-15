---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235087"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService agora é respeitado

|   |   |
|---|---|
|Detalhes|Essa configuração estabelece a memória mínima que deve estar disponível no servidor para que um serviço WCF possa ser ativado. Ela foi projetada para evitar exceções <xref:System.OutOfMemoryException?displayProperty=name>. No .NET Framework 4.5, essa configuração não tinha nenhum efeito. No .NET Framework 4.5.1, essa configuração é observada.|
|Sugestão|Ocorrerá uma exceção se a memória livre disponível no servidor Web for menor que a porcentagem definida pela definição de configuração. Alguns serviços WCF iniciados com êxito e executados em um ambiente de memória restrito agora podem falhar.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|
