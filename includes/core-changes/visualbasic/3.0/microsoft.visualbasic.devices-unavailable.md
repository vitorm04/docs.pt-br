---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721786"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Os tipos no namespace Microsoft. VisualBasic. Devices não estão disponíveis

Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Descrição da alteração

Os tipos no <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0,. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código depende do uso de <xref:Microsoft.VisualBasic.Devices> tipos e de seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .net. Por exemplo, a funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> classe é fornecida pelos <xref:System.DateTime?displayProperty=nameWithType> tipos e e a <xref:System.Environment?displayProperty=nameWithType> funcionalidade equivalente à <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> classe é fornecida por tipos no <xref:System.IO.Ports?displayProperty=nameWithType> namespace.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
