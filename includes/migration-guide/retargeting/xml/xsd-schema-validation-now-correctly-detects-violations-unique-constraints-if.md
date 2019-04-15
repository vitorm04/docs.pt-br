---
ms.openlocfilehash: 5844dbc2c3c89baeb39b69f16846f92ac10e97f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234337"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>A validação do Esquema XSD agora detecta corretamente as violações de restrições exclusivas se chaves compostas forem usadas e uma chave estiver vazia

|   |   |
|---|---|
|Detalhes|As versões do .NET Framework anteriores a 4.6 tinham um bug que fazia com que a validação de XSD não detectasse restrições exclusivas em chaves compostas se uma das chaves estivesse vazia. No .NET Framework 4.6, esse problema foi corrigido. Isso resultará na validação mais correta, mas também pode resultar na não validação de algum XML que anteriormente seria validado.|
|Sugestão|Se for necessária uma validação menos rigorosa do .NET Framework 4.0, o aplicativo de validação poderá ser destinado à versão 4.5 (ou anterior) do .NET Framework. No entanto, ao redirecionar para o .NET Framework 4.6, será necessário fazer uma revisão de código para garantir que não seja esperado que chaves compostas duplicadas (conforme é descrito na descrição desse problema) sejam validadas.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Redirecionando|
