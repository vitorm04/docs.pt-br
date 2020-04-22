---
title: Visão geral do global.json
description: Saiba como usar o arquivo global.json para definir a versão do SDK do .NET Core ao executar comandos de CLI do .NET Core.
ms.date: 04/21/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5384b59cccb629a5409d26a8df7c81b3999fc95f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021343"
---
# <a name="globaljson-overview"></a>Visão geral do global.json

**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores

O arquivo *global.json* permite que você defina qual versão do SDK do .NET Core é usada ao executar comandos de CLI do .NET Core. A seleção do SDK do .NET Core não depende da especificação do runtime ao qual o projeto é direcionado. A versão .NET Core SDK indica quais versões do .NET Core CLI é usada.

Em geral, você deseja usar a versão mais recente das ferramentas SDK, de modo que nenhum arquivo *global.json* é necessário. Em alguns cenários avançados, você pode querer controlar a versão das ferramentas sdk, e este artigo explica como fazer isso.

Para obter mais informações de como especificar o runtime nesse caso, confira [Estruturas de destino](../../standard/frameworks.md).

O SDK do .NET Core procura um arquivo *global.json* no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.

## <a name="globaljson-schema"></a>Esquema do global.json

### <a name="sdk"></a>sdk

Digite: `object`

Especifica as informações sobre o SDK do .NET Core a ser selecionado.

#### <a name="version"></a>version

- Digite: `string`

- Disponível desde: .NET Core 1.0 SDK.

A versão do SDK do .NET Core a ser usada.

Este campo:

- Não tem suporte a curinga, ou seja, o número completo da versão tem que ser especificado.
- Não dá suporte para intervalos de versão.

#### <a name="allowprerelease"></a>permitirPré-lançamento

- Digite: `boolean`

- Disponível desde: .NET Core 3.0 SDK.

Indica se o resolver SDK deve considerar as versões de pré-lançamento ao selecionar a versão SDK para usar.

Se você não definir esse valor explicitamente, o valor padrão depende se você está executando do Visual Studio:

- Se você **não** estiver no Visual Studio, o valor padrão é `true`.
- Se você estiver no Visual Studio, ele usa o status de pré-lançamento solicitado. Ou seja, se você estiver usando uma versão preview do Visual Studio ou definir as visualizações de uso da opção `true` **.NET Core SDK** (em **Recursos** > de visualização do**ambiente** > de**opções** > de**ferramentas),** o valor padrão é ; caso contrário, `false`.

#### <a name="rollforward"></a>rollForward

- Digite: `string`

- Disponível desde: .NET Core 3.0 SDK.

A política de encaminhamento para usar ao selecionar uma versão SDK, seja como um recuo quando uma versão específica do SDK está faltando ou como uma diretiva para usar uma versão superior. Uma [versão](#version) deve ser `rollForward` especificada com um valor, `latestMajor`a menos que você esteja definindo-a para .

Para entender as políticas disponíveis e seu comportamento, considere as seguintes `x.y.znn`definições para uma versão SDK no formato :

- `x`é a versão principal.
- `y`é a versão menor.
- `z`é a banda de recursos.
- `nn`é a versão de patch.

A tabela a seguir mostra `rollForward` os valores possíveis para a chave:

| Valor         | Comportamento |
| ------------- | ---------- |
| `patch`       | Usa a versão especificada. <br> Se não for encontrado, avança para o nível de patch mais recente. <br> Se não for encontrado, falha. <br><br> Este valor é o comportamento legado das versões anteriores do SDK. |
| `feature`     | Usa o nível de patch mais recente para a banda principal, menor e de recurso especificada. <br> Se não for encontrado, rola para a próxima faixa de recurso superior dentro do mesmo maior/menor e usa o nível de patch mais recente para essa banda de recursos. <br> Se não for encontrado, falha. |
| `minor`       | Usa o nível de patch mais recente para a banda principal, menor e de recurso especificada. <br> Se não for encontrado, rola para a próxima banda de recursos mais alto dentro da mesma versão principal/menor e usa o nível de patch mais recente para essa banda de recursos. <br> Se não for encontrado, rola para a próxima faixa menor mais alta e de recurso dentro do mesmo major e usa o nível de patch mais recente para essa banda de recursos. <br> Se não for encontrado, falha. |
| `major`       | Usa o nível de patch mais recente para a banda principal, menor e de recurso especificada. <br> Se não for encontrado, rola para a próxima banda de recursos mais alto dentro da mesma versão principal/menor e usa o nível de patch mais recente para essa banda de recursos. <br> Se não for encontrado, rola para a próxima faixa menor mais alta e de recurso dentro do mesmo major e usa o nível de patch mais recente para essa banda de recursos. <br> Se não for encontrado, rola para a próxima banda maior, menor e característica e usa o nível de patch mais recente para essa banda de recursos. <br> Se não for encontrado, falha. |
| `latestPatch` | Usa o nível de patch instalado mais recente que corresponde à faixa principal, menor e de recurso solicitada com um nível de patch e que é maior ou igual ao valor especificado. <br> Se não for encontrado, falha. |
| `latestFeature` | Usa a faixa de recurso mais alta instalada e o nível de patch que corresponde ao maior e menor solicitado com uma faixa de recurso maior ou igual ao valor especificado. <br> Se não for encontrado, falha. |
| `latestMinor` | Usa o menor mais alto instalado, banda de recurso e nível de patch que corresponde ao principal solicitado com um menor que é maior ou igual ao valor especificado. <br> Se não for encontrado, falha. |
| `latestMajor` | Usa o SDK de núcleo .NET mais alto instalado com um maior que é maior ou igual ao valor especificado. <br> Se não for encontrado, falhe. |
| `disable`     | Não rola para a frente. Correspondência exata necessária. |

## <a name="examples"></a>Exemplos

O exemplo a seguir mostra como não usar versões de pré-lançamento:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

O exemplo a seguir mostra como usar a versão mais alta instalada que é maior ou igual à versão especificada:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

O exemplo a seguir mostra como usar a versão exata especificada:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

O exemplo a seguir mostra como usar a última faixa de recurso e a versão de patch instalada de uma versão específica principal e menor:

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

O exemplo a seguir mostra como usar a versão de patch mais alta instalada de uma versão específica (no formulário, 3.1.1xx):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json e CLI do .NET Core

É útil saber quais versões SDK estão instaladas em sua máquina para definir uma no arquivo *global.json.* Para obter mais informações sobre como fazer isso, consulte [Como verificar se o .NET Core já está instalado](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Para instalar versões adicionais do .NET Core SDK na máquina, visite a página [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

Você pode criar um novo arquivo *global.json* no diretório atual executando o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Regras de correspondência

> [!NOTE]
> As regras de correspondência `dotnet.exe` são regidas pelo ponto de entrada, que é comum em todos os tempos de execução instalados do .NET Core. As regras de correspondência para a versão mais recente instalada do .NET Core Runtime são usadas quando você tem vários tempos de execução instalados lado a lado.

## <a name="net-core-3x"></a>[.NET Core 3.x](#tab/netcore3x)

A partir do .NET Core 3.0, as seguintes regras se aplicam ao determinar qual versão do SDK usar:

- Se nenhum arquivo *global.json* for encontrado ou *o global.json* não `allowPrerelease` especificar uma versão SDK nem um valor, `rollForward` `latestMajor`a versão sDK mais alta será usada (equivalente à configuração de ). Se as versões sdk de `dotnet` pré-lançamento são consideradas depende de como está sendo invocada.
  - Se você **não** está no Visual Studio, as versões de pré-lançamento são consideradas.
  - Se você estiver no Visual Studio, ele usa o status de pré-lançamento solicitado. Ou seja, se você estiver usando uma versão preview do Visual Studio ou definir as visualizações de uso da opção **.NET Core SDK** (em **Recursos** > de**visualização****do ambiente** > **de ferramentas),** > as versões de pré-lançamento são consideradas; caso contrário, apenas versões de versão são consideradas.
- Se for encontrado um arquivo *global.json* que não especifique `allowPrerelease` uma versão do SDK, mas especificar um `rollForward` `latestMajor`valor, a versão sDK mais alta instalada será usada (equivalente à configuração de ). Se a versão mais recente do SDK pode ser `allowPrerelease`lançada ou pré-lançamento depende do valor de . `true`indica que as versões de pré-lançamento são consideradas; `false` indica que apenas versões de versão são consideradas.
- Se um arquivo *global.json* for encontrado e ele especificar uma versão SDK:

  - Se `rollFoward` nenhum valor for `latestPatch` definido, `rollForward` ele usará como política padrão. Caso contrário, verifique cada valor e seu comportamento na seção [rollForward.](#rollforward)
  - Se as versões de pré-lançamento `allowPrerelease` são consideradas e qual é o comportamento padrão quando não está definido é descrito na seção [permitirPré-lançamento.](#allowprerelease)

## <a name="net-core-2x"></a>[.NET Core 2.x](#tab/netcore2x)

No .NET Core 2.x SDK, as seguintes regras se aplicam ao determinar qual versão do SDK usar:

- Se não for encontrado nenhum arquivo *global.json* ou se *global.json* não especificar uma versão do SDK, a última versão do SDK instalada será usada. A versão mais recente do SDK pode ser lançada ou pré-lançada - o número mais alto da versão ganha.
- Se o *global.json* especificar uma versão do SDK:
  - Se a versão do SDK especificada for encontrada no computador, a versão exata será usada.
  - Se a versão do SDK especificada não for encontrada no computador, a **versão de patch** do SDK mais recente instalada dessa versão será usada. A versão mais recente do **patch** sdk instalada pode ser lançada ou pré-lançamento - o número mais alto da versão ganha. No .NET Core 2.1 e nas versões posteriores, as **versões de patch** inferiores à **versão de patch** especificada são ignoradas na seleção do SDK.
  - Se a versão do SDK especificada e uma **versão de patch** adequada do SDK não forem encontradas, um erro será gerado.

A versão SDK é composta pelas seguintes partes:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

A **versão de recursos** do SDK do .NET Core é representada pelo primeiro dígito (`x`) na última parte do número (`xyz`) para versões do SDK 2.1.100 e superiores. Em geral, o SDK do .NET Core tem um ciclo de versão mais rápido que o .NET Core.

A **versão de patch** é definida pelos dois últimos dígitos (`yz`) na última parte do número (`xyz`) do SDK versões 2.1.100 e superiores. Por exemplo, se você especificar `2.1.300` como a versão do SDK, a seleção de SDK localizará até a `2.1.399` mas a `2.1.400` não será considerada uma versão de patch para `2.1.300`.

As versões do SDK do .NET Core `2.1.100` até `2.1.201` foram lançadas durante a transição entre os esquemas de número de versão e não lidam corretamente com a notação `xyz`. Se você especificar essas versões no arquivo *global.json*, será altamente recomendado verificar se as versões especificadas estão nos computadores de destino.

---

## <a name="troubleshoot-build-warnings"></a>Solucionar problemas de construção de avisos

* O seguinte aviso indica que seu projeto foi compilado usando uma versão de pré-lançamento do .NET Core SDK:

  > Você está trabalhando com uma versão prévia do SDK do .NET Core. Você pode definir a versão do SDK por meio de um arquivo global.json no projeto atual. Mais <https://go.microsoft.com/fwlink/?linkid=869452>em .

  As versões do SDK do .NET Core têm um histórico e o compromisso de manter a alta qualidade. No entanto, se você não quiser usar uma versão de pré-lançamento, verifique as diferentes estratégias que você pode usar com o .NET Core 3.0 SDK ou uma versão posterior na seção [allowPrerelease.](#allowprerelease) Para máquinas que nunca tiveram um .NET Core 3.0 ou um Runtime ou SDK superior instalado, você precisa criar um arquivo *global.json* e especificar a versão exata que deseja usar.

* O aviso a seguir indica que seu projeto tem como alvo o EF Core 1.0 ou 1.1, que não é compatível com o .NET Core 2.1 SDK e versões posteriores:

  > O projeto de inicialização '{startupProject}' é direcionado à estrutura '.NETCoreApp' versão '{targetFrameworkVersion}'. Essa versão das ferramentas de linha de comando do .NET do Entity Framework Core são compatíveis apenas com a versão 2.0 ou superiores. Para obter informações sobre o uso <https://go.microsoft.com/fwlink/?linkid=871254>de versões mais antigas das ferramentas, consulte .

  A partir do SDK do .NET Core 2.1 (versão 2.1.300), o comando `dotnet ef` vem incluído no SDK. Para compilar seu projeto, instale o .NET Core 2.0 SDK (versão 2.1.201) ou anteriormente em sua máquina e defina a versão sdk desejada usando o arquivo *global.json.* Para saber mais sobre o comando `dotnet ef`, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Confira também

- [Como os SDKs de projeto são resolvidos](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
