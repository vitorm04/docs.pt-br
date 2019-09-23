---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181735"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Os tipos no namespace Microsoft. VisualBasic. Devices não estão disponíveis

Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="details"></a>Detalhes

Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0,. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.
 
#### <a name="recommended-action"></a>Ação recomendada

Se o seu código depende do uso de <xref:Microsoft.VisualBasic.Devices> tipos e de seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .net. Por exemplo, a funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> classe é fornecida <xref:System.DateTime?displayProperty=nameWithType> pelos tipos e <xref:System.Environment?displayProperty=nameWithType> e a funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> classe é fornecida por tipos no <xref:System.IO.Ports?displayProperty=nameWithType> namespace.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

