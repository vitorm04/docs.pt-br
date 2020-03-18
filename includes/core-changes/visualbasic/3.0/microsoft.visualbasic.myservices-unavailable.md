---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116326"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Tipos em Microsoft.VisualBasic.MyServices namespace não disponíveis

Os tipos <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> no namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3.0 Visualização 8

#### <a name="change-description"></a>Descrição da alteração

Os tipos <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> no namespace estavam disponíveis em algumas versões do .NET Core 3.0 Preview. Eles não estão mais disponíveis a partir do .NET Core 3.0 Preview 9.

Os tipos foram removidos para evitar dependências de montagem desnecessárias ou alterações de quebra em versões subseqüentes.

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código depender do uso dos tipos **Microsoft.VisualBasic.MyServices** e seus membros, há tipos e membros correspondentes na biblioteca de classes .NET. A seguir está um mapeamento dos tipos **Microsoft.VisualBasic.MyServices** para seus tipos de biblioteca de classe .NET equivalentes:

|Microsoft.VisualBasic.MyServices tipo|Tipo de biblioteca de classe .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>para aplicativos WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> para aplicativos do Windows Forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Tipos no <xref:System.IO> namespace|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Tipos relacionados ao <xref:Microsoft.Win32> registro no namespace|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
