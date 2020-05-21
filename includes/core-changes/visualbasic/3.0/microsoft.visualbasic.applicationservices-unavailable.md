---
ms.openlocfilehash: 09027863ff2f0009a14578db35db870c27369726
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720947"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Os tipos no namespace Microsoft. VisualBasic. ApplicationServices não estão disponíveis

Os tipos no <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace não estão disponíveis.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Descrição da alteração

Os tipos no <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> namespace estavam disponíveis em algumas versões de visualização do .NET Core 3,0. Eles não estão mais disponíveis a partir do .NET Core 3,0 Preview 9.

Os tipos foram removidos para evitar dependências de assembly desnecessárias ou alterações significativas nas versões subsequentes.

#### <a name="recommended-action"></a>Ação recomendada

Se o seu código depende do uso de <xref:Microsoft.VisualBasic.ApplicationServices> tipos e de seus membros, você poderá usar um tipo ou membro correspondente na biblioteca de classes do .net. Por exemplo, alguns <xref:System.Environment?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> Membros e fornecem funcionalidade equivalente às propriedades da <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> classe.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
