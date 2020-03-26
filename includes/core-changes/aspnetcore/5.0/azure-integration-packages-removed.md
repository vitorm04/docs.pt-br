---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291669"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure: pacotes de integração azure prefixados pela Microsoft removidos

Os `Microsoft.*` seguintes pacotes que fornecem integração entre ASP.NET SDKs Core e Azure não estão incluídos no ASP.NET Core 5.0:

* [Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), que integra [o Azure Key Vault](/azure/key-vault/) no sistema de [configuração](/aspnet/core/fundamentals/configuration/).
* [Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), que integra o Azure Key Vault no [sistema de proteção de dados ASP.NET.](/aspnet/core/security/data-protection/introduction)
* [Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), que integra o [Azure Blob Storage](/azure/storage/blobs/) ao sistema de proteção de dados ASP.NET.

Para discussão sobre este assunto, consulte [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Versão introduzida

5.0 Visualização 1

#### <a name="old-behavior"></a>Comportamento antigo

Os `Microsoft.*` pacotes integraram os serviços do Azure com as APIs de Configuração e Proteção de Dados.

#### <a name="new-behavior"></a>Novo comportamento

Novos `Azure.*` pacotes integram os serviços do Azure com as APIs de Configuração e Proteção de Dados.

#### <a name="reason-for-change"></a>Motivo da mudança

A mudança foi `Microsoft.*` feita porque os pacotes eram:

* Usando versões desatualizadas do Azure SDK. Atualizações simples não foram possíveis porque as novas versões do Azure SDK incluíam mudanças de ruptura.
* Vinculado ao cronograma de lançamento do .NET Core. Transferir a propriedade dos pacotes para a equipe do Azure SDK permite atualizações de pacotes à medida que o SDK do Azure é atualizado.

#### <a name="recommended-action"></a>Ação recomendada

Em ASP.NET projetos Core 2.1 ou `Microsoft.*` posteriores, substitua o antigo pelos novos `Azure.*` pacotes.

| Velho | Novo |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure.AspNetCore.DataProtection.Keys](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure.AspNetCore.DataProtection.Blobs](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.Configuration.Secrets](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

Os novos pacotes usam uma nova versão do Azure SDK que inclui mudanças de quebra. Os padrões de uso geral são inalterados. Algumas sobrecargas e opções podem diferir para se adaptar às alterações nas APIs SDK subjacentes.

Os pacotes antigos:

* Seja apoiado pela equipe ASP.NET Core durante toda a vida do .NET Core 2.1 e 3.1.
* Não ser incluído em .NET 5.

Ao atualizar seu projeto para .NET `Azure.*` 5, transicione para os pacotes para manter o suporte.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
