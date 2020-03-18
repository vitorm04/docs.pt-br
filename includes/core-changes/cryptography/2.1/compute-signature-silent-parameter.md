---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449202"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Parâmetro booleano de SignedCms.ComputeSignature é respeitado

No .NET Core, `silent` o parâmetro <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> booleano do método é respeitado. Um prompt PIN não é mostrado se `true`este parâmetro estiver definido como .

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework, o `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parâmetro do método é ignorado e um prompt PIN é sempre mostrado se necessário pelo provedor. No .NET Core, o `silent` parâmetro é respeitado `true`e, se definido como , um prompt PIN nunca é mostrado, mesmo que seja exigido pelo provedor.

Suporte para CMS/PKCS #7 mensagens foi introduzida no .NET Core na versão 2.1.

#### <a name="version-introduced"></a>Versão introduzida

2.1

#### <a name="recommended-action"></a>Ação recomendada

Para garantir que um prompt PIN seja <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> exibido se necessário, os `false`aplicativos de desktop devem ligar e definir o parâmetro Boolean para . O comportamento resultante é o mesmo do .NET Framework, independentemente de o contexto silencioso estar desativado lá.

### <a name="category"></a>Categoria

Criptografia

### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
