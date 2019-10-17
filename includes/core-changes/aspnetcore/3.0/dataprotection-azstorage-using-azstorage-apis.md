---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394019"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Proteção de dados: dataprotection. AzureStorage usa novas APIs de armazenamento do Azure

o <xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depende das [bibliotecas de armazenamento do Azure](https://github.com/Azure/azure-storage-net). Essas bibliotecas renomeam seus assemblies, pacotes e namespaces. A partir do ASP.NET Core 3,0, o `Microsoft.AspNetCore.DataProtection.AzureStorage` usa as novas APIs e pacotes prefixados do `Microsoft.Azure.Storage.`.

Para perguntas sobre as APIs de armazenamento do Azure, use <https://github.com/Azure/azure-storage-net>. Para obter uma discussão sobre esse problema, consulte [ASPNET/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O pacote referenciou o pacote NuGet `WindowsAzure.Storage`.

#### <a name="new-behavior"></a>Novo comportamento

O pacote faz referência ao pacote NuGet `Microsoft.Azure.Storage.Blob`.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração permite que `Microsoft.AspNetCore.DataProtection.AzureStorage` migre para os pacotes de armazenamento do Azure recomendados.

#### <a name="recommended-action"></a>Ação recomendada

Se você ainda precisar usar as APIs mais antigas do armazenamento do Azure com o ASP.NET Core 3,0, adicione uma dependência direta ao pacote [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) . Esse pacote pode ser instalado juntamente com as novas APIs `Microsoft.Azure.Storage`.

Em muitos casos, a atualização envolve apenas a alteração das instruções `using` para usar os novos namespaces:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
