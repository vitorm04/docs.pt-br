---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234592"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Os métodos MachineKey.Encode e MachineKey.Decode agora estão obsoletos

|   |   |
|---|---|
|Detalhes|Esses métodos são agora obsoletos. A compilação de código que chama estes métodos gera um aviso do compilador.|
|Sugestão|As alternativas recomendadas são <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> e <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo. Ainda há suporte para as APIs.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
