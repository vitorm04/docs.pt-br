---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235039"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>Desserialização de objetos em domínios de aplicativo podem falhar

|   |   |
|---|---|
|Detalhes|Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.|
|Sugestão|Confira [Mitigação: Desserialização de objetos em domínios do aplicativo](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)|
|Escopo|Microsoft Edge|
|Versão|4.5.1|
|Tipo|Tempo de execução|
