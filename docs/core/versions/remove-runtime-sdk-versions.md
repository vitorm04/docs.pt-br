---
title: Remover o SDK e o tempo de execução do .NET Core
description: Este artigo descreve como determinar quais versões do tempo de execução e do SDK do .NET Core estão instaladas e, em seguida, como removê-las no Windows, Mac e Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 63fc441d045f62abc6776cac56571a971d64fefd
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583869"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Como remover o SDK e o Tempo de Execução do .NET Core

Ao longo do tempo, ao instalar as versões atualizadas do tempo de execução e do SDK do .NET Core, você poderá desejar remover versões desatualizadas do .NET Core do seu computador. Remover versões mais antigas do tempo de execução pode mudar o tempo de execução escolhido para executar aplicativos de estrutura compartilhada, conforme detalhado no artigo [Seleção de versão do .NET Core](selection.md).

## <a name="should-i-remove-a-version"></a>Devo remover uma versão?

Os comportamentos de [seleção de versão do .NET Core](selection.md) e a compatibilidade do tempo de execução do .NET Core com as atualizações permitem a remoção segura de versões anteriores. As atualizações de tempo de execução do .NET core são compatíveis com uma “banda” de versão principal como 1.x e 2.x. Além disso, versões mais recentes do SDK do .NET Core geralmente mantêm a capacidade de compilar aplicativos destinados a versões anteriores do tempo de execução de uma maneira compatível.

Em geral, você precisa apenas do SDK mais recente e da versão de patch mais recente dos tempos de execução necessários para seu aplicativo. Instâncias em que se deve reter versões mais antigas do SDK ou do tempo de execução incluem a manutenção de aplicativos baseados em **project.json**. A menos que seu aplicativo tenha motivos específicos para tempos de execução ou SDKs anteriores, você pode remover com segurança as versões mais antigas.

## <a name="determine-what-is-installed"></a>Determinar o que está instalado

Começando com o .NET Core 2.1, a CLI do .NET tem as opções que você pode usar para listar as versões do SDK e do tempo de execução que estão instaladas em seu computador.  Use [`dotnet --list-sdks`](../tools/dotnet.md#options) para ver a lista dos SDKs instalados em seu computador. Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) para ver a lista dos tempos de execução instalados em seu computador. O texto a seguir mostra a saída típica para Windows, macOS ou Linux:

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

```console
C:\> dotnet --list-sdks
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]

C:\> dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macostabmacos"></a>[macOS](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

***

## <a name="uninstalling-net-core"></a>Desinstalando o .NET Core

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

O .NET Core usa a caixa de diálogo **Adicionar ou Remover Programas** do Windows para remover as versões do SDK e do tempo de execução do .NET Core. A figura a seguir mostra a caixa de diálogo **Adicionar ou Remover Programas** com várias versões do tempo de execução e do SDK do .NET instaladas.

![Adicionar ou remover programas para remover o .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Selecione todas as versões que você deseja remover do seu computador e clique em **Desinstalar**.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Há mais opções para desinstalar o .NET Core (SDK ou tempo de execução) no Linux. A melhor maneira para desinstalar o .NET Core é espelhar a ação que você usou para instalar o .NET Core. As especificações dependem de sua distribuição escolhida e do método de instalação.

> [!IMPORTANT]
> Para instalações do Red Hat, consulte o [Guia de introdução do Red Hat](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) para obter informações sobre como instalar e desinstalar o .NET Core.

Começando com o .NET Core 2.1, não há necessidade de desinstalar o SDK do .NET Core ao atualizá-lo usando um gerenciador de pacotes. Os comandos `update` ou `refresh` do gerenciador de pacotes removerão automaticamente a versão mais antiga após a instalação bem-sucedida de uma versão mais recente.

Se instalou o .NET Core usando um gerenciador de pacotes, você usará esse mesmo gerenciador de pacotes para desinstalar o SDK ou o tempo de execução do .NET. As instalações do .NET core dão suporte a gerenciadores de pacotes mais populares. Consulte a documentação do gerenciador de pacotes da distribuição para a sintaxe exata em seu ambiente:

- [apt-get(8)](https://linux.die.net/man/8/apt-get) é usado por sistemas baseados em Debian, incluindo o Ubuntu.
- [yum(8)](https://linux.die.net/man/8/yum) é usado no Fedora, CentOS e Oracle Linux.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) é usado no openSUSE e no SLES (SUSE Linux Enterprise System).
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) é usado no Fedora.

Em quase todos os casos, o comando para remover um pacote é `remove`.

O nome do pacote para a instalação do SDK do .NET Core para a maioria dos gerenciadores de pacotes é `dotnet-sdk`, seguido pelo número de versão. Começando com a versão 2.1.300 do SDK do .NET Core e a versão `2.1` do tempo de execução, somente os números de versão principal e secundária são necessários: por exemplo, o SDK do .NET Core versão 2.1.300 pode ser referenciado como o pacote `dotnet-sdk-2.1`. As versões anteriores exigem a cadeia de caracteres de versão inteira: por exemplo, `dotnet-sdk-2.1.200` seria necessária para a versão 2.1.200 do SDK do .NET Core.

Para computadores apenas com o tempo de execução instalado, e não o SDK, o nome do pacote é `dotnet-runtime-<version>`, para o tempo de execução do .NET Core, e `aspnetcore-runtime-<version>`, para a pilha em tempo de execução inteira.

As instalações do .NET Core anteriores à versão 2.0 não desinstalaram o aplicativo host quando o SDK foi desinstalado usando o gerenciador de pacotes. Usando `apt-get`, o comando é:

```bash
apt-get remove dotnet-host
```

Observe que não há nenhuma versão anexada ao `dotnet-host`.

Se instalou usando um tarball, você deverá remover o .NET Core usando o método manual.

Você remove os SDKs e os tempos de execução separadamente, removendo o diretório que contém essa versão. Por exemplo, para remover o SDK 1.0.1 e o tempo de execução, você usaria os seguintes comandos de bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Os diretórios pais para o SDK e o tempo de execução são listados na saída dos comandos `dotnet --list-sdks` e `dotnet --list-runtimes`, conforme mostrado na tabela anterior.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

No Mac, você remove os SDKs e os tempos de execução separadamente, removendo o diretório que contém essa versão. Por exemplo, para remover o SDK 1.0.1 e o tempo de execução, você usaria os seguintes comandos de bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Os diretórios pais para o SDK e o tempo de execução são listados na saída dos comandos `dotnet --list-sdks` e `dotnet --list-runtimes`, conforme mostrado na tabela anterior.

---
