---
title: Visão geral do global.json
description: Saiba como usar o arquivo global.json para definir a versão do SDK do .NET Core ao executar comandos de CLI do .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 12/03/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 7cb118c16460ed593d210f5e816b2a6fd5af2ee3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150843"
---
# <a name="globaljson-overview"></a>Visão geral do global.json

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

O arquivo *global.json* permite que você defina qual versão do SDK do .NET Core é usada ao executar comandos de CLI do .NET Core. A seleção do SDK do .NET Core não depende da especificação do tempo de execução ao qual o projeto é direcionado. A versão do SDK do .NET Core indica quais versões das ferramentas de CLI do .NET Core são usadas. Em geral, o ideal é usar a versão mais recente das ferramentas, portanto, não há necessidade de usar um arquivo *global.json*.

Para obter mais informações de como especificar o tempo de execução nesse caso, confira [Estruturas de destino](../../standard/frameworks.md).

O SDK do .NET Core procura um arquivo *global.json* no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.

## <a name="globaljson-schema"></a>Esquema do global.json

### <a name="sdk"></a>sdk

Tipo: Object

Especifica as informações sobre o SDK do .NET Core a ser selecionado.

#### <a name="version"></a>version

Tipo: String

A versão do SDK do .NET Core a ser usada.

Observe que esse campo:

- Não tem suporte para recurso de curinga, ou seja, o número de versão completo deve ser especificado.
- Não dá suporte para intervalos de versão.

O exemplo a seguir mostra o conteúdo de um arquivo *global.json*:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json e CLI do .NET Core

É bom saber quais versões estão disponíveis para definir um arquivo *global.json*. Encontre a lista completa de SDKs com suporte disponíveis no site [Downloads do .NET](https://www.microsoft.com/net/download/all). A partir do SDK do .NET Core 2.1, você pode executar o comando a seguir para verificar quais versões do SDK já estão instaladas em seu computador:

```console
dotnet --list-sdks
```

Para instalar versões adicionais do SDK do .NET Core em seu computador, visite o site [Downloads do .NET](https://www.microsoft.com/net/download/all).

Você pode criar um novo arquivo *global.json* no diretório atual executando o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:

```console
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a>Regras de correspondência

> [!NOTE]
> As regras de correspondência são controladas pelo apphost, que faz parte do tempo de execução do .NET Core.
> A versão mais recente do host é usada quando há vários tempos de execução instalados lado a lado.

Começando com o .NET Core 2.0, as seguintes regras se aplicam ao determinar qual versão do SDK será usada:

- Se não for encontrado nenhum arquivo *global.json* ou se *global.json* não especificar uma versão do SDK, a última versão do SDK instalada será usada. A versão mais recente do SDK pode ser uma versão ou um pré-lançamento. Será usado aquele que tiver o número de versão mais alto.
- Se o *global.json* especificar uma versão do SDK:
  - Se a versão do SDK especificada for encontrada no computador, a versão exata será usada.
  - Se a versão do SDK especificada não for encontrada no computador, a **versão de patch** do SDK mais recente instalada dessa versão será usada. A **versão de patch** mais recente do SDK instalada pode ser uma versão ou um pré-lançamento. Será usado o número de versão mais alto. No .NET Core 2.1 e nas versões posteriores, as **versões de patch** inferiores à **versão de patch** especificada são ignoradas na seleção do SDK.
  - Se a versão do SDK especificada e uma **versão de patch** adequada do SDK não forem encontradas, um erro será gerado.

Atualmente, a versão do SDK é composta pelas seguintes partes:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

A **versão de recursos** do SDK do .NET Core é representada pelo primeiro dígito (`x`) na última parte do número (`xyz`) para versões do SDK 2.1.100 e superiores. Em geral, o SDK do .NET Core tem um ciclo de versão mais rápido que o .NET Core.

A **versão de patch** é definida pelos dois últimos dígitos (`yz`) na última parte do número (`xyz`) do SDK versões 2.1.100 e superiores. Por exemplo, se você especificar `2.1.300` como a versão do SDK, a seleção de SDK localizará até a `2.1.399` mas a `2.1.400` não será considerada uma versão de patch para `2.1.300`.

As versões do SDK do .NET Core `2.1.100` até `2.1.201` foram lançadas durante a transição entre os esquemas de número de versão e não lidam corretamente com a notação `xyz`. Se você especificar essas versões no arquivo *global.json*, será altamente recomendado verificar se as versões especificadas estão nos computadores de destino.

Com o SDK do .NET Core 1.x, se você especificar uma versão e nenhuma correspondência exata for encontrada, a última versão do SDK instalada será usada. A versão mais recente do SDK pode ser uma versão ou um pré-lançamento. Será usado aquele que tiver o número de versão mais alto.

## <a name="troubleshooting-build-warnings"></a>Solucionando problemas de aviso de build

> [!WARNING]
> Você está trabalhando com uma versão prévia do SDK do .NET Core. Você pode definir a versão do SDK por meio de um arquivo global.json no projeto atual. Saiba mais em <https://go.microsoft.com/fwlink/?linkid=869452>

Este aviso indica que seu projeto está sendo compilado usando uma versão prévia do SDK do .NET Core, conforme é explicado na seção [Regras de correspondência](#matching-rules). As versões do SDK do .NET Core têm um histórico e o compromisso de manter a alta qualidade. No entanto, se você não quiser usar uma versão prévia, adicione um arquivo *global.json* à estrutura de hierarquia do projeto para especificar qual versão do SDK deve ser usada e, em seguida, use `dotnet --list-sdks` para confirmar se a versão está instalada em seu computador. Quando uma nova versão for lançada, para usá-la, remova o arquivo *global.json* ou atualize-o para usar a versão mais recente.

> [!WARNING]
> O projeto de inicialização '{startupProject}' é direcionado à estrutura '.NETCoreApp' versão '{targetFrameworkVersion}'. Essa versão das ferramentas de linha de comando do .NET do Entity Framework Core são compatíveis apenas com a versão 2.0 ou superiores. Para obter informações de como usar as versões mais antigas das ferramentas, confira <https://go.microsoft.com/fwlink/?linkid=871254>

A partir do SDK do .NET Core 2.1 (versão 2.1.300), o comando `dotnet ef` vem incluído no SDK. Este aviso indica que o projeto é direcionado ao EF Core 1.0 ou 1.1, que não é compatível com o SDk do .NET Core 2.1 e versões posteriores. Para compilar seu projeto, instale o SDK do .NET Core 2.0 (versão 2.1.201) e versões anteriores em seu computador e defina a versão do SDK desejada usando o arquivo *global.json*. Para saber mais sobre o comando `dotnet ef`, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Consulte também

- [Como os SDKs do projeto são resolvidos](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)