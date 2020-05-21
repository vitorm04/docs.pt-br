---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721466"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>O parâmetro booliano de SignedCms. ComputeSignature é respeitado

No .NET Core, o parâmetro booliano `silent` do <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> método é respeitado. Um prompt de PIN não será exibido se esse parâmetro for definido como `true` .

#### <a name="change-description"></a>Descrição da alteração

No .NET Framework, o `silent` parâmetro do <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> método é ignorado e um prompt de PIN é sempre mostrado se exigido pelo provedor. No .NET Core, o `silent` parâmetro é respeitado e, se definido como `true` , um aviso de PIN nunca é mostrado, mesmo que seja exigido pelo provedor.

O suporte para mensagens #7 CMS/PKCS foi introduzido no .NET Core na versão 2,1.

#### <a name="version-introduced"></a>Versão introduzida

2.1

#### <a name="recommended-action"></a>Ação recomendada

Para garantir que um prompt de PIN apareça se necessário, os aplicativos de área de trabalho devem chamar <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> e definir o parâmetro booliano como `false` . O comportamento resultante é o mesmo que em .NET Framework, independentemente de o contexto silencioso estar desabilitado lá.

#### <a name="category"></a>Categoria

Criptografia

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
