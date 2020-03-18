---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901970"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Proteção de dados: DataProtection.AzureStorage usa novas APIs de armazenamento do Azure

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>depende das [bibliotecas de armazenamento Azure.](https://github.com/Azure/azure-storage-net) Essas bibliotecas renomearam seus conjuntos, pacotes e espaços de nome. A partir de ASP.NET `Microsoft.AspNetCore.DataProtection.AzureStorage` Core 3.0, usa as novas `Microsoft.Azure.Storage.`APIs e pacotes prefixados.

Para dúvidas sobre as APIs <https://github.com/Azure/azure-storage-net>de armazenamento do Azure, use . Para discussão sobre este assunto, consulte [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O pacote fazia `WindowsAzure.Storage` referência ao pacote NuGet.

#### <a name="new-behavior"></a>Novo comportamento

O pacote faz `Microsoft.Azure.Storage.Blob` referência ao pacote NuGet.

#### <a name="reason-for-change"></a>Motivo da mudança

Essa alteração `Microsoft.AspNetCore.DataProtection.AzureStorage` permite migrar para os pacotes recomendados do Azure Storage.

#### <a name="recommended-action"></a>Ação recomendada

Se você ainda precisar usar as APIs de armazenamento azure mais antigas com ASP.NET Core 3.0, adicione uma dependência direta ao pacote [WindowsAzure.Storage.](https://www.nuget.org/packages/WindowsAzure.Storage/) Este pacote pode ser instalado `Microsoft.Azure.Storage` junto com as novas APIs.

Em muitos casos, a atualização `using` envolve apenas alterar as instruções para usar os novos namespaces:

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
