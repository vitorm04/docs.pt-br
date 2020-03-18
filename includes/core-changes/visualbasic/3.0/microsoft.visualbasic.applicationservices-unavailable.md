---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116351"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Tipos em Microsoft.VisualBasic.ApplicationServices namespace não disponível

Os tipos <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> no namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3.0 Visualização 8

#### <a name="change-description"></a>Descrição da alteração

Os tipos <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> no namespace estavam disponíveis em algumas versões do .NET Core 3.0 Preview. Eles não estão mais disponíveis a partir do .NET Core 3.0 Preview 9.

Os tipos foram removidos para evitar dependências de montagem desnecessárias ou alterações de quebra em versões subseqüentes.

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código depender <xref:Microsoft.VisualBasic.ApplicationServices> do uso de tipos e seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes .NET. Por exemplo, <xref:System.Environment?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> alguns e membros fornecem funcionalidade <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> equivalente às propriedades da classe.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
