---
title: Publicação de aplicativos
description: Saiba mais sobre as formas de publicar um aplicativo .NET Core. O .NET Core pode publicar aplicativos específicos da plataforma ou multiplataforma. Você pode publicar um aplicativo como independente ou como dependente de tempo de execução. Cada modo afeta a forma como um usuário executa seu aplicativo.
ms.date: 04/01/2020
ms.openlocfilehash: a4e5f9fe048d40c751f582bd49732cb903202db4
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665532"
---
# <a name="net-core-application-publishing-overview"></a>Visão geral da publicação de aplicativos .NET Core

Os aplicativos criados com o .NET Core podem ser publicados em dois modos diferentes, e o modo afeta a forma como um usuário executa seu aplicativo.

Publicar seu aplicativo como *autônomo* produz um aplicativo que inclui o tempo de execução e bibliotecas do .NET Core, e seu aplicativo e suas dependências. Os usuários do aplicativo podem executá-lo em uma máquina que não tenha o tempo de execução do .NET Core instalado.

Publicar seu aplicativo como *dependente de tempo de execução* (anteriormente conhecido como dependente de *framework)* produz um aplicativo que inclui apenas seu próprio aplicativo e suas dependências. Os usuários do aplicativo têm que instalar separadamente o tempo de execução do .NET Core.

Ambos os modos de publicação produzem um executável específico da plataforma por padrão. Aplicativos dependentes de tempo de execução podem ser criados sem um executável, e esses aplicativos são multiplataformas.

Quando um executável é produzido, você pode especificar a plataforma de destino com um identificador de tempo de execução (RID). Para obter mais informações sobre rids, consulte [.NET Core RID Catalog](../rid-catalog.md).

A tabela a seguir descreve os comandos usados para publicar um aplicativo como dependente de tempo de execução ou auto-contido, por versão SDK:

| Type                                                                                 | SDK 2.1 | SDK 3.x | Comando |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [executável dependente de tempo de execução](#publish-runtime-dependent) para a plataforma atual. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [executável dependente de tempo de execução](#publish-runtime-dependent) para uma plataforma específica.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [binário multiplataforma dependente de tempo de execução](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [executável autônomo.](#publish-self-contained)                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Para obter mais informações, consulte [o comando de publicação do .NET Core .](../tools/dotnet-publish.md)

## <a name="produce-an-executable"></a>Produzir um executável

Executáveis não são multiplataformas. São específicos para um sistema operacional e arquitetura de CPU. Ao publicar seu aplicativo e criar um executável, você pode publicar o aplicativo como [independente](#publish-self-contained) ou [dependente de tempo de execução](#publish-runtime-dependent). Publicar um aplicativo como autônomo inclui o tempo de execução do .NET Core com o aplicativo, e os usuários do aplicativo não têm que se preocupar em instalar o .NET Core antes de executar o aplicativo. Os aplicativos publicados como dependentes de tempo de execução não incluem o tempo de execução do .NET Core e bibliotecas; apenas o aplicativo e as dependências de terceiros estão incluídos.

Os seguintes comandos produzem um executável:

| Type                                                                                 | SDK 2.1 | SDK 3.x | Comando |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| [executável dependente de tempo de execução](#publish-runtime-dependent) para a plataforma atual. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [executável dependente de tempo de execução](#publish-runtime-dependent) para uma plataforma específica.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [executável autônomo.](#publish-self-contained)                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Produza um binário multiplataforma

Binários multiplataforma são criados quando você publica seu aplicativo como [dependente de tempo de execução,](#publish-runtime-dependent)na forma de um arquivo *dll.* O *arquivo dll* tem o nome do seu projeto. Por exemplo, se você tiver um aplicativo chamado **word_reader,** um arquivo chamado *word_reader.dll* é criado. Os aplicativos publicados desta `dotnet <filename.dll>` forma são executados com o comando e podem ser executados em qualquer plataforma.

Binários multiplataforma podem ser executados em qualquer sistema operacional, desde que o tempo de execução do .NET Core direcionado já esteja instalado. Se o tempo de execução do .NET Core direcionado não estiver instalado, o aplicativo poderá ser executado usando um tempo de execução mais novo se o aplicativo estiver configurado para rolar para frente. Para obter mais informações, consulte [aplicativos dependentes de tempo de execução para a frente](../versions/selection.md#framework-dependent-apps-roll-forward).

O comando a seguir produz um binário multiplataforma:

| Type                                                                                 | SDK 2.1 | SDK 3.x | Comando |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [binário multiplataforma dependente de tempo de execução](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Publicar dependente de tempo de execução

Os aplicativos publicados como dependentes de tempo de execução são multiplataforma saem de plataforma e não incluem o tempo de execução do .NET Core. O usuário do seu aplicativo é obrigado a instalar o tempo de execução do .NET Core.

Publicar um aplicativo como dependente de tempo de execução produz um [binário multiplataforma](#produce-a-cross-platform-binary) como um arquivo *dll* e um [executável específico da plataforma](#produce-an-executable) que tem como alvo sua plataforma atual. A *dll* é multiplataforma enquanto o executável não é. Por exemplo, se você publicar um aplicativo chamado **word_reader** e direcionar o Windows, um executável *word_reader.exe* será criado juntamente com *word_reader.dll*. Ao direcionar o Linux ou o macOS, um *word_reader* executável é criado juntamente com *word_reader.dll*. Para obter mais informações sobre rids, consulte [.NET Core RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> O .NET Core SDK 2.1 não produz executáveis específicos da plataforma quando você publica um aplicativo dependente do tempo de execução.

O binário multiplataforma do seu aplicativo `dotnet <filename.dll>` pode ser executado com o comando, e pode ser executado em qualquer plataforma. Se o aplicativo usar um pacote NuGet que tenha implementações específicas da plataforma, todas as dependências das plataformas serão copiadas para a pasta de publicação junto com o aplicativo.

Você pode criar um executável para `-r <RID> --self-contained false` uma plataforma [`dotnet publish`](../tools/dotnet-publish.md) específica passando os parâmetros para o comando. Quando `-r` o parâmetro é omitido, um executável é criado para sua plataforma atual. Todos os pacotes NuGet que tenham dependências específicas da plataforma para a plataforma-alvo são copiados para a pasta de publicação.

### <a name="advantages"></a>Vantagens

- **Pequena implantação**\
Apenas seu aplicativo e suas dependências são distribuídos. O tempo de execução e as bibliotecas do .NET Core são instalados pelo usuário e todos os aplicativos compartilham o tempo de execução.

- **Multiplataforma**\
Seu aplicativo e qualquer . A biblioteca baseada em NET é executada em outros sistemas operacionais. Você não precisa definir uma plataforma de destino para o seu aplicativo. Para obter informações sobre o formato de arquivo .NET, consulte [.NET Assembly File Format](../../standard/assembly/file-format.md).

- **Usa o tempo de execução corrigido mais recente**\
O aplicativo usa o tempo de execução mais recente (dentro da família de menor-alvo do .NET Core) instalado no sistema de destino. Isso significa que seu aplicativo usa automaticamente a versão corrigida mais recente do tempo de execução do .NET Core. Esse comportamento padrão pode ser substituído. Para obter mais informações, consulte [aplicativos dependentes de tempo de execução para a frente](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Desvantagens

- **Requer pré-instalação do tempo de execução**\
Seu aplicativo só pode ser executado se a versão do .NET Core que seu aplicativo já está instalado no sistema host. Você pode configurar o comportamento de roll-forward para o aplicativo para exigir uma versão específica do .NET Core ou permitir uma versão mais recente do .NET Core. Para obter mais informações, consulte [aplicativos dependentes de tempo de execução para a frente](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET Core pode mudar**\
É possível que o tempo de execução do .NET Core e bibliotecas sejam atualizados na máquina onde o aplicativo é executado. Em casos raros, isso pode mudar o comportamento do seu aplicativo se você usar as bibliotecas .NET Core, o que a maioria dos aplicativos fazem. Você pode configurar como seu aplicativo usa versões mais recentes do .NET Core. Para obter mais informações, consulte [aplicativos dependentes de tempo de execução para a frente](../versions/selection.md#framework-dependent-apps-roll-forward).

A desvantagem a seguir só se aplica ao .NET Core 2.1 SDK.

- **Use `dotnet` o comando para iniciar o aplicativo**\
Os usuários `dotnet <filename.dll>` devem executar o comando para iniciar seu aplicativo. O .NET Core 2.1 SDK não produz executáveis específicos da plataforma para aplicativos publicados em tempo de execução.

### <a name="examples"></a>Exemplos

Publique um aplicativo entre plataformas que dependem do tempo de execução. Um executável que tem como alvo sua plataforma atual é criado junto com o arquivo *dll.*

```dotnet
dotnet publish
```

Publique um aplicativo entre plataformas que dependem do tempo de execução. Um executável de 64 bits do Linux é criado junto com o arquivo *dll.* Este comando não funciona com o .NET Core SDK 2.1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publicar autônomo

Publicar seu aplicativo como autônomo produz um executável específico da plataforma. A pasta de publicação de saída contém todos os componentes do aplicativo, incluindo as bibliotecas .NET Core e o tempo de execução de destino. O aplicativo é isolado de outros aplicativos .NET Core e não usa um tempo de execução compartilhado instalado localmente. O usuário do seu aplicativo não é obrigado a baixar e instalar o .NET Core.

O binário executável é produzido para a plataforma de destino especificada. Por exemplo, se você tiver um aplicativo chamado **word_reader**, e publicar um executável independente para Windows, um arquivo *word_reader.exe* será criado. Publicando para Linux ou macOS, um *arquivo word_reader* é criado. A plataforma de destino e `-r <RID>` a arquitetura [`dotnet publish`](../tools/dotnet-publish.md) são especificadas com o parâmetro para o comando. Para obter mais informações sobre rids, consulte [.NET Core RID Catalog](../rid-catalog.md).

Se o aplicativo tiver dependências específicas da plataforma, como um pacote NuGet contendo dependências específicas da plataforma, estes serão copiados para a pasta de publicação junto com o aplicativo.

### <a name="advantages"></a>Vantagens

- **Controle .NET Versão Core**\
Você controla qual versão do .NET Core é implantada com o seu aplicativo.

- **Segmentação específica da plataforma**\
Como você tem que publicar seu aplicativo para cada plataforma, você sabe onde seu aplicativo será executado. Se o .NET Core introduzir uma nova plataforma, os usuários não poderão executar seu aplicativo nessa plataforma até que você libere uma versão direcionada a essa plataforma. Você pode testar seu aplicativo para problemas de compatibilidade antes que seus usuários executem seu aplicativo na nova plataforma.

### <a name="disadvantages"></a>Desvantagens

- **Implantações maiores**\
Como seu aplicativo inclui o tempo de execução do .NET Core e todas as dependências do aplicativo, o tamanho de download e o espaço do disco rígido necessários é maior do que uma versão [dependente do tempo de execução.](#publish-runtime-dependent)

  > [!TIP]
  > Você pode reduzir o tamanho de sua implantação em sistemas Linux em aproximadamente 28 MB usando o [*modo invariante de globalização*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)do .NET Core . Isso força seu aplicativo a tratar todas as culturas como a [cultura invariante.](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)

- **Mais difícil atualizar a versão .NET Core**\
O .NET Core Runtime (distribuído com seu aplicativo) só pode ser atualizado lançando uma nova versão do seu aplicativo. Você é responsável por fornecer uma versão atualizada do seu aplicativo para patches de segurança para o .NET Core Runtime.

### <a name="examples"></a>Exemplos

Publique um aplicativo independente. Um executável macOS de 64 bits é criado.

```dotnet
dotnet publish -r osx-x64
```

Publique um aplicativo independente. Um executável de 64 bits do Windows é criado.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Confira também

- [Implantando aplicativos .NET Core com .NET Core CLI.](deploy-with-cli.md)
- [Implantando aplicativos .NET Core com o Visual Studio.](deploy-with-vs.md)
- [Pacotes, metapacotes e frameworks.](../packages.md)
- [Catálogo de Identificadores de Execução (RID) do .NET Core.](../rid-catalog.md)
- [Selecione a versão .NET Core para usar.](../versions/selection.md)
