---
title: "O que há de novo no c# 7.1"
description: "Uma visão geral dos novos recursos no c# 7.1."
keywords: Design de linguagem c#, 7.1, Visual Studio de 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a>O que há de novo no c# 7.1

7.1 c# é a primeira versão de ponto para a linguagem c#. Marca uma cadência de lançamento maior para o idioma. Você pode usar os novos recursos mais cedo, idealmente quando cada novo recurso está pronto. 7.1 c# adiciona a capacidade de configurar o compilador para corresponder a uma versão especificada do idioma. Que permite que você separe a decisão de atualizar ferramentas de decisão para atualizar versões de idioma.

7.1 c# adiciona o [seleção de versão de idioma](#language-version-selection) elemento de configuração, três novos recursos de idioma e o novo comportamento do compilador.

Os novos recursos de idioma nesta versão são:

* [`async``Main` método](#async-main)
  - O ponto de entrada para um aplicativo pode ter o `async` modificador.
* [`default`expressões literais](#default-literal-expressions)
  - Você pode usar expressões de literal padrão em expressões de valor padrão quando o tipo de destino pode ser inferido.
* [Nomes de elemento de tupla deduzido](#inferred-tuple-element-names)
  - Os nomes dos elementos de tupla podem ser inferidos de inicialização de tupla em muitos casos.

Por fim, o compilador tem duas opções `/refout` e `/refonly` que controlam [fazem referência a geração de assembly](#reference-assembly-generation).

## <a name="language-version-selection"></a>Seleção de versão de idioma

O compilador c# oferece suporte a c# 7.1 começando com Visual Studio 2017 versão 15,3 ou o .NET Core SDK 2.0. No entanto, os 7.1 recursos são desativados por padrão. Para habilitar os 7.1 recursos, você precisa alterar a configuração de versão de idioma para o seu projeto.

No Visual Studio, clique com botão direito no nó do projeto no Gerenciador de soluções e selecione **propriedades**. Selecione o **criar** guia e selecione o **avançado** botão. No menu suspenso, selecione **c# versão secundária mais recente (mais recente)**, ou a versão específica **c# 7.1** conforme mostrado na seguinte imagem. O `latest` valor significa que você deseja usar a versão secundária mais recente no computador atual. O `C# 7.1` significa que você deseja usar o c# 7.1, mesmo depois que são lançadas novas versões secundárias.

![Definindo a versão de idioma](./media/csharp-7-1/advanced-build-settings.png)

Como alternativa, você pode editar o arquivo "csproj" e adicionar ou modificar as seguintes linhas:

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Se você usar o IDE do Visual Studio para atualizar seus arquivos csproj, o IDE criará nós separados para cada configuração de compilação. Você normalmente definirá o valor a mesma em todas as configurações de compilação, mas é necessário defini-las explicitamente para cada configuração de compilação, ou selecione "Todas as configurações de" quando você modificar essa configuração. Você verá o seguinte no arquivo csproj:

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

As configurações válidas para o `LangVersion` elemento são:

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

As cadeias de caracteres especiais `default` e `latest` resolver para as versões de idioma principal e secundária mais recentes instaladas no computador de build, respectivamente.

Essa configuração separa instalar novas versões do SDK e ferramentas em seu ambiente de desenvolvimento de escolher incorporar os novos recursos de idioma em um projeto. Você pode instalar o SDK e as ferramentas mais recentes no seu computador de compilação. Cada projeto pode ser configurado para usar uma versão específica do idioma de sua compilação.

## <a name="async-main"></a>Assíncrono principal

Um *async principal* método permite que você use `await` no seu `Main` método.
Anteriormente, era necessário escrever:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Agora você pode escrever:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Se o programa não retorna um código de saída, você pode declarar uma `Main` método que retorna um <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Você pode ler mais sobre os detalhes no [async principal](../programming-guide/main-and-command-args/index.md) tópico no guia de programação.

## <a name="default-literal-expressions"></a>Expressões de literal padrão

Expressões literais padrão são um aprimoramento de expressões de valor padrão.
Essas expressões inicializar uma variável com o valor padrão. Onde você anteriormente escreve:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Agora você pode omitir o tipo do lado direito da inicialização:

```csharp
Func<string, bool> whereClause = default;
```

Você pode aprender mais sobre esse aprimoramento do tópico do guia de programação em c# em [padrão de expressões de valor](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Esse aprimoramento altera algumas das regras de análise para o [palavra-chave default](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Nomes de elemento de tupla deduzido

Esse recurso é um aprimoramento pequeno para o recurso de tuplas, introduzido no c# 7.0. Muitas vezes quando você inicializa uma tupla, as variáveis usadas para o lado direito da atribuição são iguais aos nomes que você deseja para os elementos de tupla:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Os nomes dos elementos de tupla podem ser inferidos de variáveis usadas para inicializar a tupla no c# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Você pode aprender mais sobre esse recurso no [tuplas](../tuples.md) tópico.

## <a name="reference-assembly-generation"></a>Geração de assembly de referência

Há duas novas opções de compilador que geram *assemblies de referência*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) e [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Os tópicos vinculados explicam essas opções e os assemblies de referência em mais detalhes.
