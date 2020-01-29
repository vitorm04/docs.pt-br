---
title: Visão geral do global.json
description: Saiba como usar o arquivo global.json para definir a versão do SDK do .NET Core ao executar comandos de CLI do .NET Core.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f02c9129a707ddddb2c5e1975b75cc35abc5cd55
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733979"
---
# <a name="globaljson-overview"></a>Visão geral do global.json

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores

O arquivo *global.json* permite que você defina qual versão do SDK do .NET Core é usada ao executar comandos de CLI do .NET Core. A seleção do SDK do .NET Core não depende da especificação do runtime ao qual o projeto é direcionado. A versão do SDK do .NET Core indica quais versões das ferramentas de CLI do .NET Core são usadas.

Em geral, você deseja usar a versão mais recente das ferramentas do SDK, portanto, nenhum arquivo *global. JSON* é necessário. Em alguns cenários avançados, talvez você queira controlar a versão das ferramentas do SDK, e este artigo explica como fazer isso.

Para obter mais informações de como especificar o runtime nesse caso, confira [Estruturas de destino](../../standard/frameworks.md).

O SDK do .NET Core procura um arquivo *global.json* no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.

## <a name="globaljson-schema"></a>Esquema do global.json

### <a name="sdk"></a>sdk

Tipo: `object`

Especifica as informações sobre o SDK do .NET Core a ser selecionado.

#### <a name="version"></a>versão

- Tipo: `string`

- Disponível desde: SDK do .NET Core 1,0.

A versão do SDK do .NET Core a ser usada.

Este campo:

- Não tem suporte a curinga, ou seja, o número de versão completo deve ser especificado.
- Não dá suporte para intervalos de versão.

#### <a name="allowprerelease"></a>allowPrerelease

- Tipo: `boolean`

- Disponível desde: SDK do .NET Core 3,0.

Indica se o resolvedor do SDK deve considerar versões de pré-lançamento ao selecionar a versão do SDK a ser usada.

Se você não definir esse valor explicitamente, o valor padrão dependerá do fato de você estar executando a partir do Visual Studio:

- Se você **não** estiver no Visual Studio, o valor padrão será `true`.
- Se você estiver no Visual Studio, ele usará o status de pré-lançamento solicitado. Ou seja, se você estiver usando uma versão prévia do Visual Studio ou se definir a opção **usar visualizações da SDK do .NET Core** (em **ferramentas** > **Opções** > **ambiente** > **recursos de visualização**), o valor padrão será `true`; caso contrário, `false`.

#### <a name="rollforward"></a>Avanço

- Tipo: `string`

- Disponível desde: SDK do .NET Core 3,0.

A política de roll-forward a ser usada ao selecionar uma versão do SDK, seja como um fallback quando uma versão específica do SDK estiver ausente ou como uma diretiva para usar uma versão superior. Uma [versão](#version) deve ser especificada com um valor `rollForward`, a menos que você esteja definindo-a como `latestMajor`.

Para entender as políticas disponíveis e seu comportamento, considere as seguintes definições para uma versão do SDK no formato `x.y.znn`:

- `x` é a versão principal.
- `y` é a versão secundária.
- `z` é a faixa de recursos.
- `nn` é a versão do patch.

A tabela a seguir mostra os valores possíveis para a chave de `rollForward`:

| Value         | Comportamento |
| ------------- | ---------- |
| `patch`       | Usa a versão especificada. <br> Se não for encontrado, roll forward para o último nível de patch. <br> Se não for encontrado, falhará. <br><br> Esse valor é o comportamento herdado das versões anteriores do SDK. |
| `feature`     | Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada. <br> Se não for encontrado, roll forward para a próxima faixa de recursos mais alta dentro do mesmo principal/secundário e usa o nível de patch mais recente para essa faixa de recurso. <br> Se não for encontrado, falhará. |
| `minor`       | Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada. <br> Se não for encontrado, roll forward para a próxima faixa de recursos mais alta na mesma versão principal/secundária e usa o nível de patch mais recente para essa faixa de recurso. <br> Se não for encontrado, roll forward para a próxima faixa secundária e de recurso na mesma principal e usa o nível de patch mais recente para essa faixa de recurso. <br> Se não for encontrado, falhará. |
| `major`       | Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada. <br> Se não for encontrado, roll forward para a próxima faixa de recursos mais alta na mesma versão principal/secundária e usa o nível de patch mais recente para essa faixa de recurso. <br> Se não for encontrado, roll forward para a próxima faixa secundária e de recurso na mesma principal e usa o nível de patch mais recente para essa faixa de recurso. <br> Se não for encontrado, rola para a próxima faixa mais alta, secundária e de recurso e usa o nível de patch mais recente para essa faixa de recurso. <br> Se não for encontrado, falhará. |
| `latestPatch` | Usa o nível de patch mais recente instalado que corresponde à faixa principal, secundária e de recursos solicitada com um nível de patch e maior ou igual ao valor especificado. <br> Se não for encontrado, falhará. |
| `latestFeature` | Usa a faixa de recursos e o nível de patch mais alto instalados que coincidem com o principal e o secundário solicitados com uma faixa de recursos maior ou igual ao valor especificado. <br> Se não for encontrado, falhará. |
| `latestMinor` | Usa a maior versão instalada, a faixa de recursos e o nível de patch que corresponde à principal solicitada com um secundário que é maior ou igual ao valor especificado. <br> Se não for encontrado, falhará. |
| `latestMajor` | Usa o SDK do .NET Core mais alto instalado com uma grande maior ou igual ao valor especificado. <br> Se não for encontrado, falha. |
| `disable`     | Não rola para frente. Correspondência exata necessária. |

## <a name="examples"></a>Exemplos

O exemplo a seguir mostra como não usar versões de pré-lançamento:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

O exemplo a seguir mostra como usar a versão mais recente instalada que é maior ou igual à versão especificada:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

O exemplo a seguir mostra como usar a versão especificada exata:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

O exemplo a seguir mostra como usar a versão de patch mais alta instalada de uma versão específica (no formato 3.1.1 XX):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json e CLI do .NET Core

É útil saber quais versões do SDK estão instaladas em seu computador para definir uma no arquivo *global. JSON* . Para obter mais informações sobre como fazer isso, consulte [como verificar se o .NET Core já está instalado](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Para instalar versões adicionais do SDK do .NET Core em seu computador, visite a página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .

Você pode criar um novo arquivo *global.json* no diretório atual executando o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Regras de correspondência

> [!NOTE]
> As regras de correspondência são governadas pelo ponto de entrada de `dotnet.exe`, que é comum em todos os tempos de execução instalados do .NET Core instalados. As regras de correspondência para a versão mais recente instalada do tempo de execução do .NET Core são usadas quando você tem vários tempos de execução instalados lado a lado.

## <a name="net-core-3xtabnetcore3x"></a>[.NET Core 3. x](#tab/netcore3x)

A partir do .NET Core 3,0, as seguintes regras se aplicam ao determinar qual versão do SDK usar:

- Se nenhum arquivo *global. JSON* for encontrado ou *global. JSON* não especificar uma versão do sdk nem um valor `allowPrerelease`, a versão mais recente do SDK instalada será usada (equivalente a definir `rollForward` como `latestMajor`). Se as versões de pré-lançamento do SDK são consideradas depende de como `dotnet` está sendo invocada.
  - Se você **não** estiver no Visual Studio, as versões de pré-lançamento serão consideradas.
  - Se você estiver no Visual Studio, ele usará o status de pré-lançamento solicitado. Ou seja, se você estiver usando uma versão prévia do Visual Studio ou se definir a opção **usar visualizações da SDK do .NET Core** (em **ferramentas** > **Opções** > **ambiente** > **recursos de visualização**), as versões de pré-lançamento serão consideradas; caso contrário, apenas versões de lançamento serão consideradas.
- Se um arquivo *global. JSON* for encontrado e não especificar uma versão do SDK, mas especificar um valor `allowPrerelease`, a versão mais recente do SDK instalada será usada (equivalente a definir `rollForward` como `latestMajor`). Se a versão mais recente do SDK pode ser Release ou pré-lançamento depende do valor de `allowPrerelease`. `true` indica que as versões de pré-lançamento são consideradas; `false` indica que apenas versões de lançamento são consideradas.
- Se um arquivo *global. JSON* for encontrado e ele especificar uma versão do SDK:

  - Se nenhum valor de `rollFoward` for definido, ele usará `latestPatch` como a política de `rollForward` padrão. Caso contrário, verifique cada valor e seu comportamento na seção [avanço](#rollforward) .
  - Se as versões de pré-lançamento são consideradas e qual é o comportamento padrão quando `allowPrerelease` não está definido é descrito na seção [allowPrerelease](#allowprerelease) .

## <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

No SDK do .NET Core 2. x, as seguintes regras se aplicam ao determinar qual versão do SDK usar:

- Se não for encontrado nenhum arquivo *global.json* ou se *global.json* não especificar uma versão do SDK, a última versão do SDK instalada será usada. A versão mais recente do SDK pode ser Release ou pré-lançamento-o número de versão mais alto vence.
- Se o *global.json* especificar uma versão do SDK:
  - Se a versão do SDK especificada for encontrada no computador, a versão exata será usada.
  - Se a versão do SDK especificada não for encontrada no computador, a **versão de patch** do SDK mais recente instalada dessa versão será usada. A versão mais recente do **patch** do SDK instalado pode ser Release ou pré-lançamento-o número de versão mais alto vence. No .NET Core 2.1 e nas versões posteriores, as **versões de patch** inferiores à **versão de patch** especificada são ignoradas na seleção do SDK.
  - Se a versão do SDK especificada e uma **versão de patch** adequada do SDK não forem encontradas, um erro será gerado.

A versão do SDK é composta pelas seguintes partes:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

A **versão de recursos** do SDK do .NET Core é representada pelo primeiro dígito (`x`) na última parte do número (`xyz`) para versões do SDK 2.1.100 e superiores. Em geral, o SDK do .NET Core tem um ciclo de versão mais rápido que o .NET Core.

A **versão de patch** é definida pelos dois últimos dígitos (`yz`) na última parte do número (`xyz`) do SDK versões 2.1.100 e superiores. Por exemplo, se você especificar `2.1.300` como a versão do SDK, a seleção de SDK localizará até a `2.1.399` mas a `2.1.400` não será considerada uma versão de patch para `2.1.300`.

As versões do SDK do .NET Core `2.1.100` até `2.1.201` foram lançadas durante a transição entre os esquemas de número de versão e não lidam corretamente com a notação `xyz`. Se você especificar essas versões no arquivo *global.json*, será altamente recomendado verificar se as versões especificadas estão nos computadores de destino.

---

## <a name="troubleshooting-build-warnings"></a>Solucionando problemas de aviso de build

> [!WARNING]
> Você está trabalhando com uma versão prévia do SDK do .NET Core. Você pode definir a versão do SDK por meio de um arquivo global.json no projeto atual. Saiba mais em <https://go.microsoft.com/fwlink/?linkid=869452>

Esse aviso indica que seu projeto foi compilado usando uma versão de pré-lançamento do SDK do .NET Core. As versões do SDK do .NET Core têm um histórico e o compromisso de manter a alta qualidade. No entanto, se você não quiser usar uma versão de pré-lançamento, verifique as diferentes estratégias que você pode usar com o SDK do .NET Core 3,0 ou uma versão posterior na seção [allowPrerelease](#allowprerelease) . Para computadores que nunca tinham um .NET Core 3,0 ou um tempo de execução ou SDK superior instalado, você precisa criar um arquivo *global. JSON* e especificar a versão exata que deseja usar.

> [!WARNING]
> O projeto de inicialização '{startupProject}' é direcionado à estrutura '.NETCoreApp' versão '{targetFrameworkVersion}'. Essa versão das ferramentas de linha de comando do .NET do Entity Framework Core são compatíveis apenas com a versão 2.0 ou superiores. Para obter informações de como usar as versões mais antigas das ferramentas, confira <https://go.microsoft.com/fwlink/?linkid=871254>

A partir do SDK do .NET Core 2.1 (versão 2.1.300), o comando `dotnet ef` vem incluído no SDK. Este aviso indica que o projeto é direcionado ao EF Core 1.0 ou 1.1, que não é compatível com o SDk do .NET Core 2.1 e versões posteriores. Para compilar seu projeto, instale o SDK do .NET Core 2.0 (versão 2.1.201) e versões anteriores em seu computador e defina a versão do SDK desejada usando o arquivo *global.json*. Para saber mais sobre o comando `dotnet ef`, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Veja também

- [Como os SDKs do projeto são resolvidos](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
