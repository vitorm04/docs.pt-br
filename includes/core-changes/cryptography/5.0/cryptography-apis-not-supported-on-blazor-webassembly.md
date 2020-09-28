---
ms.openlocfilehash: 6c2aff4abf558307d599ff7533c82286e037bc71
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406136"
---
### <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a>APIs de System. Security. Cryptography não têm suporte no Webassembly de mais incrivelmente

<xref:System.Security.Cryptography> As APIs lançam a <xref:System.PlatformNotSupportedException> em tempo de execução quando executadas em um navegador.

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, a maioria das <xref:System.Security.Cryptography> APIs não está disponível para aplicativos Webassembly mais incrivelmente. A partir do .NET 5,0, os aplicativos Webassembly mais completos têm como destino a área completa da superfície da API do .NET 5, no entanto, nem todas as APIs do .NET 5 têm suporte devido a restrições de área restrita do navegador. No .NET 5,0 e versões posteriores, as APIs sem suporte <xref:System.Security.Cryptography> lançam um <xref:System.PlatformNotSupportedException> quando executado no Webassembly.

> [!TIP]
> O [analisador de compatibilidade de plataforma](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) sinalizará todas as chamadas para as APIs afetadas quando você criar um projeto que dê suporte à plataforma do navegador. Esse analisador é executado por padrão no .NET 5,0 e em aplicativos posteriores.

#### <a name="reason-for-change"></a>Motivo da alteração

A Microsoft não pode enviar o OpenSSL como uma dependência na configuração de Webassembly mais incrivelmente. Tentamos solucionar isso tentando integrar com a API do navegador `SubtleCrypto` . Infelizmente, isso exigiu alterações significativas na API que tornaram muito difícil a integração.

#### <a name="version-introduced"></a>Versão introduzida

RC1 5,0

#### <a name="recommended-action"></a>Ação recomendada

Não há boas soluções alternativas a serem sugeridas no momento.

#### <a name="category"></a>Categoria

- ASP.NET Core
- Criptografia

#### <a name="affected-apis"></a>APIs afetadas

Todas as <xref:System.Security.Cryptography?displayProperty=fullName> APIs, exceto as seguintes:

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

#### Affected APIs

- `T:System.Security.Cryptography`

-->
