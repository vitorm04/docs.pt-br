---
ms.openlocfilehash: 68da7216890da1819a994161507355a0b5ea1f9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857503"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a>Alterações de falha de SignedXml e EncryptedXml

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2, correções de segurança em <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> e <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> levam a comportamentos de tempo de execução diferentes. Por exemplo,<ul><li>Se um documento tiver vários elementos com o mesmo atributo <code>id</code> e uma assinatura tiver como destino um desses elementos como a raiz da assinatura, o documento agora será considerado inválido.</li><li>Documentos que usam algoritmos de transformação XPath não canônicos nas referências agora são considerados inválidos.</li><li>Documentos que usam algoritmos de transformação XSLT não canônicos nas referências agora são considerados inválidos.</li><li>Nenhum programa que usar assinaturas desanexadas de recursos externos poderá fazer isso.</li></ul>|
|Sugestão|Talvez os desenvolvedores queiram revisar o uso de <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> e <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, bem como dos tipos derivados de <xref:System.Security.Cryptography.Xml.Transform>, uma vez que o receptor de um documento poderá não conseguir processá-lo.|
|Escopo|Secundária|
|Versão|4.6.2|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
