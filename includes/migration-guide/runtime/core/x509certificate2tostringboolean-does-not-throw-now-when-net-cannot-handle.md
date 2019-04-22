---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774113"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>Agora, o X509Certificate2.ToString(Boolean) não é gerado quando o .NET não pode tratar o certificado

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5.2 e nas versões anteriores, esse método era gerado quando <code>true</code> era passado para o parâmetro verbose e havia certificados instalados que não eram compatíveis com o .NET Framework. Agora, o método será bem-sucedido e retornará uma cadeia de caracteres válida que omita as partes inacessíveis do certificado.|
|Sugestão|Qualquer código dependente do <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> deve ser atualizado para esperar que a cadeia de caracteres retornada possa excluir alguns dados do certificado (como chave pública, chave privada e extensões) em alguns casos nos quais a API teria sido gerada anteriormente.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
