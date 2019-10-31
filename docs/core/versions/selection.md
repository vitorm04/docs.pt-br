---
title: Selecionar qual versão do .NET Core usar
description: Saiba como o .NET Core localiza e escolhe automaticamente versões de tempo de execução para o seu programa. Além disso, este artigo ensina como forçar uma versão específica.
author: thraka
ms.author: adegeo
ms.date: 06/26/2019
ms.custom: seodec18
ms.openlocfilehash: db42ba4916aad739bd2c9d8b547f16022fce44bd
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104943"
---
# <a name="select-the-net-core-version-to-use"></a>Selecionar a versão do .NET Core a ser usada

Este artigo explica as políticas usadas pelas ferramentas do .NET Core, pelo SDK e pelo tempo de execução para a seleção de versões. Essas políticas fornecem um equilíbrio entre a execução de aplicativos usando as versões especificadas e a possibilidade de fácil atualização dos computadores de desenvolvedores e usuários finais. Essas políticas executam as seguintes ações:

- Implantação fácil e eficiente do .NET Core, incluindo atualizações de segurança e de confiabilidade.
- Uso das ferramentas e dos comandos mais recentes independentes do tempo de execução de destino.

A seleção de versão ocorre:

- Quando você executa um comando do SDK, [o SDK usa a versão mais recente instalada](#the-sdk-uses-the-latest-installed-version).
- Quando você compila um assembly [os monikers da estrutura de destino definem as APIs do tempo de build](#target-framework-monikers-define-build-time-apis).
- Quando você executa um aplicativo .NET Core, [os aplicativos dependentes da estrutura de destino efetuam roll forward](#framework-dependent-apps-roll-forward).
- Quando você publica um aplicativo autossuficiente, [as implantações autossuficientes incluem o tempo de execução selecionado](#self-contained-deployments-include-the-selected-runtime).

O restante deste documento examina esses quatro cenários.

## <a name="the-sdk-uses-the-latest-installed-version"></a>O SDK usa a versão mais recente instalada

Os comandos do SDK incluem `dotnet new` e `dotnet run`. A CLI do .NET Core precisa escolher uma versão do SDK para todos os comandos `dotnet`. Por padrão, ela usa o SDK mais recente instalado no computador, mesmo se:

- O projeto se destinar a uma versão anterior do tempo de execução do .NET Core.
- A versão mais recente do SDK do .NET Core for uma versão prévia.

Você pode aproveitar os recursos e as melhorias mais recentes do SDK mesmo ao direcionar a versões anteriores de tempo de execução do .NET Core. Você pode direcionar a várias versões de tempo de execução do .NET Core em projetos diferentes, usando as mesmas ferramentas do SDK para todos os projetos.

Em raras ocasiões, talvez você precise usar uma versão anterior do SDK. Nesse caso, especifique essa versão em um [arquivo *global. JSON*](../tools/global-json.md). A política "usar versão mais recente" significa usar o *global.json* somente para especificar uma versão do SDK do .NET Core anterior à versão mais recente instalada.

O *global.json* pode ser colocado em qualquer lugar na hierarquia de arquivos. A CLI procura no diretório do projeto em diante até encontrar o primeiro *global.json*. Você controla a quais projetos um determinado *global.json* se aplica a pelo seu lugar no sistema de arquivos. A CLI do .NET procura um arquivo *global.json* navegando iterativamente do caminho do diretório de trabalho atual em diante. O primeiro arquivo *global.json* encontrado especifica a versão usada. Se essa versão estiver instalada, ela será usada. Se o SDK especificado na *global.json* não for encontrado, a CLI do .NET efetuará roll forward para o SDK mais recente instalado. Efetuar roll forward é o mesmo que o comportamento padrão, quando não é encontrado nenhum arquivo *global.json*.

O exemplo a seguir mostra a sintaxe *global.json*:

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

O processo para selecionar uma versão do SDK é:

1. O `dotnet` procura um arquivo *global.json* navegando inversamente de forma iterativa no caminho do diretório de trabalho atual em diante.
1. O `dotnet` usa o SDK especificado no primeiro *global.json* encontrado.
1. O `dotnet` usará a versão mais recente do SDK instalada se nenhum *global.json* for encontrado.

Saiba mais sobre como selecionar uma versão do SDK na seção [Regras de correspondência](../tools/global-json.md#matching-rules) do artigo sobre o *global.json*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Os Monikers da Estrutura de Destino definem as APIs de tempo de build

Você compila seu projeto em relação às APIs definidas em um **TFM** (Moniker da Estrutura de Destino). Você especifica a [estrutura de destino](../../standard/frameworks.md) no arquivo de projeto. Defina o elemento `TargetFramework` no arquivo de projeto, conforme mostrado no exemplo a seguir:

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Você pode compilar o projeto em relação a várias TFMs. A definição de várias estruturas de destino é mais comum em bibliotecas, mas também pode ocorrer com aplicativos. Especifique uma propriedade `TargetFrameworks` (plural de `TargetFramework`). As estruturas de destino são delimitadas por ponto e vírgula, conforme mostrado no exemplo a seguir:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Um determinado SDK dá suporte a um conjunto fixo de estruturas, limitado à estrutura de destino do tempo de execução com o qual é fornecido. Por exemplo, o SDK do .NET Core 2.0 inclui o tempo de execução do .NET Core 2.0, que é uma implementação da estrutura de destino `netcoreapp2.0`. O SDK do .NET Core 2.0 dá suporte ao `netcoreapp1.0`, `netcoreapp1.1` e `netcoreapp2.0` mas não ao `netcoreapp2.1` (ou superior). Instale o SDK do .NET Core 2.1 para compilar para o `netcoreapp2.1`.

As estruturas de destino do .NET Standard também são limitadas à estrutura de destino do tempo de execução com o qual o SDK é fornecido. O SDK do .NET Core 2.0 é limitado ao `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Roll foward de aplicativos dependentes da estrutura

Quando você executa um aplicativo da fonte com [`dotnet run`](../tools/dotnet-run.md), de uma [**implantação dependente de estrutura**](../deploying/index.md#framework-dependent-deployments-fdd) com [`dotnet myapp.dll`](../tools/dotnet.md#description) ou de um [**arquivo executável dependente de estrutura**](../deploying/index.md#framework-dependent-executables-fde) com `myapp.exe`, o arquivo executável `dotnet` é o **host** do aplicativo.

O host escolhe a versão de patch mais recente instalada no computador. Por exemplo, se você especificar `netcoreapp2.0` em seu arquivo de projeto e `2.0.4` for o tempo de execução mais recente do .NET instalado, o tempo de execução `2.0.4` será usado.

Se nenhuma versão `2.0.*` aceitável for encontrada, uma nova versão `2.*` será usada. Por exemplo, se você especificar `netcoreapp2.0` e só o `2.1.0` estiver instalado, o aplicativo será executado usando o tempo de execução `2.1.0`. Esse comportamento é conhecido como "roll forward de versão secundária". As versões inferiores também não serão consideradas. Quando nenhum tempo de execução aceitável estiver instalado, o aplicativo não será executado.

Veja alguns exemplos de uso que demonstram o comportamento, caso seu destino seja a versão 2.0:

- A 2.0 é especificada. A 2.0.5 é a versão de patch mais recente instalada. A 2.0.5 é usada.
- A 2.0 é especificada. Não há nenhuma versão 2.0.* instalada. O 1.1.1 é o tempo de execução mais recente instalado. Uma mensagem de erro é exibida.
- A 2.0 é especificada. Não há nenhuma versão 2.0.* instalada. 2.2.2 é a versão de tempo de execução 2.x mais recente instalada. A 2.2.2 é usada.
- A 2.0 é especificada. Não há nenhuma versão 2.x instalada. A 3.0.0 é instalada. Uma mensagem de erro é exibida.

O roll forward de versão secundária tem um efeito colateral que pode afetar os usuários finais. Considere o seguinte cenário:

1. O aplicativo especifica que a versão 2.0 é necessária.
2. Quando ele é executado, a versão 2.0.* não está instalada, mas a 2.2.2 está. A versão 2.2.2 será usada.
3. Posteriormente, o usuário instala a versão 2.0.5 e executa o aplicativo novamente. A 2.0.5 será então usada.

É possível que a 2.0.5 e a 2.2.2 se comportem de forma diferente, principalmente para cenários como serializar dados binários.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>As implantações autossuficientes incluem o tempo de execução selecionado

É possível publicar um aplicativo como uma [ **distribuição autossuficiente**](../deploying/index.md#self-contained-deployments-scd). Essa abordagem inclui o tempo de execução e as bibliotecas do .NET Core com seu aplicativo. As implantações autossuficientes não são dependentes dos ambientes de tempo de execução. A seleção da versão do tempo de execução ocorre no momento da publicação, não no tempo de execução.

O processo de publicação seleciona a versão de patch mais recente da família de determinado tempo de execução. Por exemplo, `dotnet publish` selecionará o .NET Core 2.0.4 se ele for a versão de patch mais recente da família do tempo de execução do .NET Core 2.0. A estrutura de destino (incluindo os patches de segurança mais recentes instalados) é empacotada com o aplicativo.

É um erro quando a versão mínima especificada para um aplicativo não é atendida. O `dotnet publish` vincula-se à última versão de patch de tempo de execução (em uma determinada família de versão principal.secundária). `dotnet publish` não dá suporte à semântica de roll forward de `dotnet run`. Para obter mais informações sobre patches e implantações autossuficientes, consulte o artigo sobre [seleção de patch de tempo de execução](../deploying/runtime-patch-selection.md) na implantação de aplicativos .NET Core.

As implantações autossuficientes podem exigir uma versão de patch específica. Você pode substituir a versão de patch mínima do tempo de execução (para versões superiores ou inferiores) no arquivo de projeto, conforme é mostrado no exemplo a seguir:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

O elemento `RuntimeFrameworkVersion` substitui a política de versão padrão. Para implantações autossuficientes, o `RuntimeFrameworkVersion` especifica a versão *exata* da estrutura do tempo de execução. Para aplicativos dependentes da estrutura, o `RuntimeFrameworkVersion` especifica a versão *mínima* da estrutura de tempo de execução necessária.
