---
ms.openlocfilehash: acb8ed44b7d18b257731e32339f087c8fe5fdd4a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721567"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Tipos no namespace Microsoft. VisualBasic. MyServices não estão disponíveis

Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Descrição da alteração

Os tipos no <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.

#### <a name="recommended-action"></a>Ação recomendada

Se seu código depende do uso de tipos **Microsoft. VisualBasic. MyServices** e seus membros, há tipos e membros correspondentes na biblioteca de classes do .net. Veja a seguir um mapeamento dos tipos **Microsoft. VisualBasic. MyServices** para seus tipos de biblioteca de classes do .net equivalentes:

|Tipo Microsoft. VisualBasic. MyServices|Tipo de biblioteca de classes .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>para aplicativos do WPF, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> para aplicativos Windows Forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Tipos no <xref:System.IO> namespace|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Tipos relacionados ao registro no <xref:Microsoft.Win32> namespace|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
