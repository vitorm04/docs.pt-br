---
title: dotnet nuget comando fonte de atualização
description: O comando dotnet nuget update source atualiza uma fonte existente em seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148543"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget fonte de atualização

**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet nuget update source`- Atualize uma fonte NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a>Descrição

O `dotnet nuget update source` comando atualiza uma fonte existente em seus arquivos de configuração NuGet.

## <a name="arguments"></a>Argumentos

- **`NAME`**

  Nome da fonte.

## <a name="options"></a>Opções

- **`--configfile`**

  O arquivo de configuração NuGet. Se especificado, apenas as configurações deste arquivo serão usadas. Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada. Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-p|--password`**

  Senha a ser usada ao se conectar a uma fonte autenticada.

- **`-s|--source`**

  Caminho para a fonte do pacote.

- **`--store-password-in-clear-text`**

  Permite armazenar credenciais de origem de pacote portátil desabilitando a criptografia de senha.

- **`-u|--username`**

  Nome de usuário a ser usado ao se conectar a uma fonte autenticada.

- **`--valid-authentication-types`**

  Lista separada por comma de tipos de autenticação válidos para esta fonte. Defina `basic` isso para se o servidor anunciar NTLM ou Negociar e suas credenciais devem ser enviadas usando o mecanismo Básico, por exemplo, ao usar um PAT com o Azure DevOps Server no local. Outros valores `negotiate` `kerberos`válidos incluem, `ntlm`e `digest`, mas esses valores são improváveis de serem úteis.

## <a name="examples"></a>Exemplos

- Atualize uma fonte `mySource`com o nome de:

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Confira também

- [Seções de origem do pacote em arquivos NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [comando fontes (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
