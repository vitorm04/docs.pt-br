---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507061"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>Extensões: alterações de referência de pacote que afetam alguns pacotes NuGet

Com a migração de alguns `Microsoft.Extensions.*` pacotes NuGet do repositório [dotnet/extensões](https://github.com/dotnet/extensions) para [dotnet/tempo de execução](https://github.com/dotnet/runtime), conforme descrito em [ASPNET/comunicados # 411](https://github.com/aspnet/Announcements/issues/411), as alterações de empacotamento estão sendo aplicadas a alguns dos pacotes migrados. Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).

#### <a name="version-introduced"></a>Versão introduzida

5,0 versão prévia 4

#### <a name="old-behavior"></a>Comportamento antigo

Alguns `Microsoft.Extensions.*` pacotes incluíram referências de pacote para APIs nas quais seu aplicativo dependa.

#### <a name="new-behavior"></a>Novo comportamento

Seu aplicativo pode ter que adicionar `Microsoft.Extensions.*` dependências de pacote.

#### <a name="reason-for-change"></a>Motivo da alteração

As políticas de empacotamento foram atualizadas para se alinharem melhor ao repositório *dotnet/tempo de execução* . Na nova política, as referências de pacote não utilizadas são removidas dos arquivos *. nupkg* durante o empacotamento.

#### <a name="recommended-action"></a>Ação recomendada

Os consumidores dos pacotes afetados devem adicionar uma dependência direta da dependência do pacote removido em seu projeto se as APIs da dependência de pacote removido forem usadas. A tabela a seguir lista os pacotes afetados e as alterações correspondentes.

|Nome do pacote|Descrição da alteração|
|------------|------------------|
|[Microsoft. Extensions. Configuration. Binder](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|Referência removida para`Microsoft.Extensions.Configuration`|
|[Microsoft. Extensions. Configuration. JSON](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |Referência removida para`System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. Hosting. abstrações](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|Referência removida para`Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft.Extensions.Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |Referência removida para`Microsoft.Extensions.Configuration.Binder`|
|[Microsoft. Extensions. Logging. console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |Referência removida para`Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft. Extensions. Logging. EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |Referência removida `System.Diagnostics.EventLog` para para o .NET Framework moniker da estrutura de destino do 4.6.1|
|[Microsoft. Extensions. Logging. EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |Referência removida para`System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. opções](https://nuget.org/packages/Microsoft.Extensions.Options)                          |Referência removida para`System.ComponentModel.Annotations`|

Por exemplo, a referência de pacote `Microsoft.Extensions.Configuration` a foi removida do `Microsoft.Extensions.Configuration.Binder`. Nenhuma API da dependência foi usada no pacote. Os usuários `Microsoft.Extensions.Configuration.Binder` de quem dependem de APIs `Microsoft.Extensions.Configuration` devem adicionar uma referência direta a ele em seu projeto.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!--

#### Affected APIs

Not detectable via API analysis

-->
