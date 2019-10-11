---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237276"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Os tipos no namespace Microsoft. VisualBasic. Devices não estão disponíveis

Os tipos no namespace <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Alterar descrição

Os tipos no namespace <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> estavam disponíveis em algumas versões de visualização do .NET Core 3,0,. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.
 
#### <a name="recommended-action"></a>Ação recomendada

Se seu código depende do uso de tipos <xref:Microsoft.VisualBasic.Devices> e seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .NET. Por exemplo, a funcionalidade equivalente à classe <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> é fornecida pelos tipos <xref:System.DateTime?displayProperty=nameWithType> e <xref:System.Environment?displayProperty=nameWithType>, e a funcionalidade equivalente à classe <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> é fornecida por tipos no namespace <xref:System.IO.Ports?displayProperty=nameWithType>.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

