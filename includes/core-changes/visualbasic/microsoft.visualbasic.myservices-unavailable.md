---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181748"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Tipos no namespace Microsoft. VisualBasic. MyServices não estão disponíveis

Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="details"></a>Detalhes

Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0,. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.
 
#### <a name="recommended-action"></a>Ação recomendada

Se seu código depende do uso de tipos **Microsoft. VisualBasic. MyServices** e seus membros, há tipos e membros correspondentes na biblioteca de classes do .net. Veja a seguir um mapeamento dos tipos **Microsoft. VisualBasic. MyServices** para seus tipos de biblioteca de classes do .net equivalentes:

|Tipo Microsoft. VisualBasic. MyServices|Tipo de biblioteca de classes .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>para aplicativos do WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> , para aplicativos Windows Forms| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Tipos no <xref:System.IO> namespace|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Tipos relacionados ao registro no <xref:Microsoft.Win32> namespace|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

