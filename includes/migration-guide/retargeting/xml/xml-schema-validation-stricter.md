---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234590"
---
### <a name="xml-schema-validation-is-stricter"></a>A validação do esquema XML está mais rigorosa

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, a validação do esquema XML está mais rigorosa. Se você usar xsd:anyURI para validar um URI como um protocolo mailto, a validação falhará se houver espaços no URI. Nas versões anteriores do .NET Framework, a validação foi bem-sucedida. A alteração afeta somente aplicativos destinados ao .NET Framework 4.5.|
|Sugestão|Se for necessária uma validação menos rigorosa do .NET Framework 4.0, o aplicativo de validação poderá se destinar à versão 4.0 do .NET Framework. No entanto, ao direcionar ao .NET Framework 4.5, é necessário revisar o código para verificar se URIs inválidos (com espaços) não são esperados como valores de atributo com o tipo de dados anyURI.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
