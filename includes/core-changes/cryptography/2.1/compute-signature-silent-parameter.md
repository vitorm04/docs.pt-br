---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449202"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>O parâmetro booliano de SignedCms. ComputeSignature é respeitado

No .NET Core, o parâmetro `silent` booliano do método <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> é respeitado. Um prompt de PIN não será exibido se esse parâmetro for definido como `true`.

#### <a name="change-description"></a>Alterar descrição

No .NET Framework, o parâmetro `silent` do método <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> é ignorado e um prompt de PIN é sempre mostrado se exigido pelo provedor. No .NET Core, o parâmetro `silent` é respeitado e, se definido como `true`, um prompt de PIN nunca é mostrado, mesmo que seja exigido pelo provedor.

O suporte para mensagens #7 CMS/PKCS foi introduzido no .NET Core na versão 2,1.

#### <a name="version-introduced"></a>Versão introduzida

2.1

#### <a name="recommended-action"></a>Ação recomendada

Para garantir que um prompt de PIN apareça se necessário, os aplicativos de área de trabalho devem chamar <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> e definir o parâmetro booliano como `false`. O comportamento resultante é o mesmo que em .NET Framework, independentemente de o contexto silencioso estar desabilitado lá.

### <a name="category"></a>Categoria

Criptografia

### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
