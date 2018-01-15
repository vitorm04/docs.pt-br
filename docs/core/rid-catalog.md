---
title: "Catálogo do RID (Identificador de Tempo de Execução) do .NET Core"
description: "Saiba mais sobre o RID (Identificador de tempo de execução) e como os RIDs são usados no .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 180aac7635746f9ede146c3e561deb9bba9a61ab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-rid-catalog"></a>Catálogo de RIDs do .NET Core

RID é a abreviação de *Identificador de Tempo de Execução*. Os valores do RID são usados para identificar plataformas de destino onde o aplicativo é executado.
Eles são usados por pacotes .NET para representar ativos específicos de plataforma em pacotes NuGet. Os seguintes valores são exemplos de RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.
Para os pacotes com dependências nativas, o RID designará as plataformas em que o pacote pode ser restaurado.

Os RIDs podem ser definidos no elemento `<RuntimeIdentifier>` do arquivo de projeto. Eles também são usados por meio da opção `--runtime` com os seguintes [comandos da CLI do .NET Core](./tools/index.md):

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

RIDs que representem sistemas operacionais concretos geralmente seguem este padrão: `[os].[version]-[architecture]-[additional qualifiers]` em que:

- `[os]` é o moniker do sistema operacional/plataforma. Por exemplo, `ubuntu`.

- `[version]` é a versão do sistema operacional na forma de um separado de versão separado por ponto (`.`). Por exemplo, `15.10`.

  - A versão **não deve** ser uma versão de marketing, pois essas geralmente representam várias versões distintas do sistema operacional com diferentes áreas de superfície de API da plataforma.

- `[architecture]` é a arquitetura do processador. Por exemplo: `x86`, `x64`, `arm` ou `arm64`.

- `[additional qualifiers]` distingue diferentes plataformas. Por exemplo `aot` ou `corert`.

## <a name="rid-graph"></a>Gráfico RID

O gráfico RID ou gráfico de fallback de tempo de execução é uma lista de RIDs que são compatíveis entre si. Os RIDs são definidos no pacote [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/). Você pode ver a lista de RIDs suportados e o gráfico RID no arquivo [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json), que está localizado no repositório CoreFX. Nesse arquivo, você pode ver todos os RIDs, exceto para a base um, que contém uma instrução `"#import"`. Essas instruções indicam RIDs compatíveis.

Quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para o tempo de execução especificado.
Se uma correspondência exata não for encontrada, o NuGet voltará ao gráfico até encontrar o sistema compatível mais próximo de acordo com o gráfico RID.

O exemplo a seguir é a entrada real para o RID `osx.10.12-x64`:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

O RID acima especifica que `osx.10.12-x64` importa `osx.10.11-x64`. Desse modo, quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para `osx.10.12-x64` no pacote. Se o NuGet não puder encontrar o tempo de execução específico, ele poderá restaurar pacotes que especificam tempos de execução `osx.10.11-x64`, por exemplo.

O seguinte exemplo mostra um gráfico RID ligeiramente maior, também definido no arquivo *runtime.json*:

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

Todos os RIDs eventualmente mapeiam para a raiz de `any` RID.

Há algumas considerações sobre RIDs das quais você precisa se lembrar ao trabalhar com eles:

- Os RIDs são **cadeias de caracteres opacas** e devem ser tratados como caixas pretas.
- Não crie RIDs de modo programático.
- Use RIDs que já estão definidos para a plataforma.
- Os RIDs precisam ser específicos, portanto, não presuma nada usando o valor RID real.

## <a name="using-rids"></a>Usando RIDs

Para poder usar RIDs, você precisa saber quais RIDs existem. Novos RIDs são adicionados regularmente à plataforma.
Para obter a versão completa e mais recente, confira o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.

O SDK do .NET Core 2.0 apresenta o conceito de RIDs portáteis. Eles são novos valores adicionados ao gráfico RID que não estão associados a uma versão específica ou distribuição de SO. Eles são particularmente úteis ao lidar com várias distribuições Linux.

A lista a seguir mostra os RIDs mais comuns usados para cada SO. Ela não cobre os valores `arm` ou `corert`.

## <a name="windows-rids"></a>RIDs do Windows

- Portáteis
  - `win-x86`
  - `win-x64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8 / Windows Server 2012
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Consulte [Pré-requisitos para o .NET Core no Windows](windows-prerequisites.md) para obter mais informações.

## <a name="linux-rids"></a>RIDs do Linux

- Portáteis
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
- Fedora
  - `fedora-x64`
  - `fedora.24-x64`
  - `fedora.25-x64` (.NET Core 2.0 ou versões posteriores)
  - `fedora.26-x64` (.NET Core 2.0 ou versões posteriores)
- Gentoo (.NET Core 2.0 ou versões posteriores)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64` (.NET Core 2.0 ou versões posteriores)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64` (.NET Core 2.0 ou versões posteriores)
  - `rhel.7.4-x64` (.NET Core 2.0 ou versões posteriores)
- Tizen (.NET Core 2.0 ou versões posteriores)
  - `tizen`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- Derivados do Ubuntu
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - `linuxmint.18.1-x64` (.NET Core 2.0 ou versões posteriores)

Consulte [Pré-requisitos para o .NET Core no Linux](linux-prerequisites.md) para obter mais informações.

## <a name="macos-rids"></a>RIDs do macOS

Os RIDs do macOS usam a identidade visual “OSX” mais antiga.

- `osx-x64` (.NET Core 2.0 ou versões posteriores; a versão mínima é `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64` (.NET Core 1.1 ou versões posteriores)
- `osx.10.13-x64`

Consulte [Pré-requisitos para o .NET Core no macOS](macos-prerequisites.md) para obter mais informações.

## <a name="android-rids-net-core-20-or-later-versions"></a>RIDs Android (.NET Core 2.0 ou versões posteriores)

- `android`
- `android.21`

## <a name="see-also"></a>Consulte também

[IDs de Tempo de Execução](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
