---
ms.openlocfilehash: d888aba597cb6981828ca67fba04912cbcf7935f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567402"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Os tipos no namespace Microsoft. VisualBasic. ApplicationServices não estão disponíveis

Os tipos no namespace <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Alterar descrição

Os tipos no namespace <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> estavam disponíveis em algumas versões de visualização do .NET Core 3,0. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.

#### <a name="recommended-action"></a>Ação recomendada

Se seu código depende do uso de tipos de <xref:Microsoft.VisualBasic.ApplicationServices> e seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .NET. Por exemplo, alguns membros <xref:System.Environment?displayProperty=nameWithType> e <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> fornecem funcionalidade equivalente às propriedades da classe <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType>.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-- >

