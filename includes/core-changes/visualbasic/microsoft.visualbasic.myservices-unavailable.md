---
ms.openlocfilehash: 75ba041a93b71377928591967e1554742e1d17e1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237279"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Tipos no namespace Microsoft. VisualBasic. MyServices não estão disponíveis

Os tipos no namespace <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Alterar descrição

Os tipos no namespace <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> estavam disponíveis em algumas versões de visualização do .NET Core 3,0. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.
 
#### <a name="recommended-action"></a>Ação recomendada

Se seu código depende do uso de tipos **Microsoft. VisualBasic. MyServices** e seus membros, há tipos e membros correspondentes na biblioteca de classes do .net. Veja a seguir um mapeamento dos tipos **Microsoft. VisualBasic. MyServices** para seus tipos de biblioteca de classes do .net equivalentes:

|Tipo Microsoft. VisualBasic. MyServices|Tipo de biblioteca de classes .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType> para aplicativos do WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> para aplicativos Windows Forms| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Tipos no namespace <xref:System.IO>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Tipos relacionados ao registro no namespace <xref:Microsoft.Win32>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

