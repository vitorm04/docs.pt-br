---
title: dotnet nuget adicionar comando fonte
description: O comando dotnet nuget add source adiciona uma nova fonte de pacote aos seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 319501e026f1c3102006b0be5357f127b8e366a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463596"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet nuget add source`- Adicione uma fonte NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>Descrição

O `dotnet nuget add source` comando adiciona uma nova fonte de pacote aos arquivos de configuração do NuGet.

## <a name="arguments"></a>Argumentos

- **`PACKAGE_SOURCE_PATH`**

  Caminho para a fonte do pacote.

## <a name="options"></a>Opções

- **`--configfile <FILE>`**

  O arquivo de configuração NuGet. Se especificado, apenas as configurações deste arquivo serão usadas. Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada. Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name <SOURCE_NAME>`**

  Nome da fonte.

- **`-p|--password <PASSWORD>`**

  Senha a ser usada ao se conectar a uma fonte autenticada.

- **`--store-password-in-clear-text`**

  Permite armazenar credenciais de origem de pacote portátil desabilitando a criptografia de senha.

- **`-u|--username <USER>`**

  Nome de usuário a ser usado ao se conectar a uma fonte autenticada.

- **`--valid-authentication-types <TYPES>`**

  Lista separada por comma de tipos de autenticação válidos para esta fonte. Defina `basic` isso para se o servidor anunciar NTLM ou Negociar e suas credenciais devem ser enviadas usando o mecanismo Básico, por exemplo, ao usar um PAT com o Azure DevOps Server no local. Outros valores `negotiate` `kerberos`válidos incluem, `ntlm`e `digest`, mas esses valores são improváveis de serem úteis.

## <a name="examples"></a>Exemplos

- Adicionar `nuget.org` como fonte:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- Adicionar `c:\packages` como fonte local:

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Adicione uma fonte que precisa de autenticação:

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Adicione uma fonte que precise de autenticação (em seguida, vá instalar provedor de credencial):

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>Confira também

- [Seções de origem do pacote em arquivos NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [comando fontes (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
