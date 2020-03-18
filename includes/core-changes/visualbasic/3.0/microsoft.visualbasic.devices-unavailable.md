---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116364"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Tipos em Microsoft.VisualBasic.Espaço de nome dos dispositivos não disponíveis

Os tipos <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> no namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3.0 Visualização 8

#### <a name="change-description"></a>Descrição da alteração

Os tipos <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> no namespace estavam disponíveis em algumas versões do .NET Core 3.0 Preview,. Eles não estão mais disponíveis a partir do .NET Core 3.0 Preview 9.

Os tipos foram removidos para evitar dependências de montagem desnecessárias ou alterações de quebra em versões subseqüentes.

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código depender <xref:Microsoft.VisualBasic.Devices> do uso de tipos e seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes .NET. Por <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> exemplo, a funcionalidade equivalente à classe <xref:System.DateTime?displayProperty=nameWithType> <xref:System.Environment?displayProperty=nameWithType> é fornecida pelos e <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> tipos, e a funcionalidade <xref:System.IO.Ports?displayProperty=nameWithType> equivalente à classe é fornecida por tipos no namespace.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
