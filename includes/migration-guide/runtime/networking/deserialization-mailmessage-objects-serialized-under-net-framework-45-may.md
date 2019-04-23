---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235110"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Desserialização de objetos MailMessage serializados no .NET Framework 4.5 pode falhar

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, os objetos <xref:System.Web.Mail.MailMessage> podem incluir caracteres não ASCII. No .NET Framework 4, somente caracteres ASCII têm suporte. <xref:System.Web.Mail.MailMessage> Os objetos que contêm caracteres não ASCII e são serializados no .NET Framework 4.5 ou versões posteriores não podem ser desserializados no .NET Framework 4.|
|Sugestão|Verifique se o seu código fornece tratamento de exceção ao desserializar um objeto <xref:System.Web.Mail.MailMessage>.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
