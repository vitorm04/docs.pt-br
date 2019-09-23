---
ms.openlocfilehash: c3211752282b231e818d9af25322efbb6c93cf78
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181812"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Os tipos no namespace Microsoft. VisualBasic. ApplicationServices não estão disponíveis

Os tipos no <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="details"></a>Detalhes

Os tipos no <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.
 
#### <a name="recommended-action"></a>Ação recomendada

Se o seu código depende do uso de <xref:Microsoft.VisualBasic.ApplicationServices> tipos e de seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .net. Por exemplo, alguns <xref:System.Environment?displayProperty=nameWithType> Membros <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> e fornecem funcionalidade equivalente <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> às propriedades da classe.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-- >

