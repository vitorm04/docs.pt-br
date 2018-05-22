---
title: Novidades no C# 7.1
description: Uma visão geral dos novos recursos no C# 7.1.
ms.date: 08/16/2017
ms.openlocfilehash: 00baec45d7582d3ac12c7b0865241f5cd8159246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-71"></a>Novidades no C# 7.1

O C# 7.1 é a primeira versão de ponto da linguagem C#. Ele marca uma cadência de versão maior para a linguagem. Use os novos recursos mais cedo, de preferência, quando cada novo recurso estiver pronto. O C# 7.1 adiciona a capacidade de configurar o compilador para que ele corresponda a uma versão especificada da linguagem. Isso permite que você separe a decisão de atualizar ferramentas da decisão de atualizar versões da linguagem.

O C# 7.1 adiciona a [seleção de versão da linguagem](#language-version-selection) elemento de configuração, três novos recursos de linguagem e um novo comportamento do compilador.

Os novos recursos de linguagem nesta versão são:

* [`async` Método `Main`](#async-main)
  - O ponto de entrada para um aplicativo pode ter o modificador `async`.
* [`default` Expressões literais](#default-literal-expressions)
  - Use expressões literais padrão em expressões de valor padrão quando o tipo de destino pode ser inferido.
* [Nomes de elementos de tupla inferidos](#inferred-tuple-element-names)
  - Em muitos casos, os nomes dos elementos de tupla podem ser inferidos com base na inicialização da tupla.

Por fim, o compilador traz duas opções `/refout` e `/refonly`, que controlam a [geração de assembly de referência](#reference-assembly-generation).

## <a name="language-version-selection"></a>Seleção de versão da linguagem

O compilador do C# dá suporte ao C# 7.1 desde o Visual Studio 2017 versão 15.3 ou o SDK do .NET Core 2.0. No entanto, os recursos do 7.1 estão desativados por padrão. Para habilitar os recursos do 7.1, é necessário alterar a configuração da versão da linguagem do projeto.

No Visual Studio, clique com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e selecione **Propriedades**. Selecione a guia **Build** e o botão **Avançado**. No menu suspenso, selecione **Última versão secundária do C# (última)** ou o **C# 7.1** com a versão específica, conforme mostrado na imagem a seguir. O valor `latest` significa que você deseja usar a última versão secundária no computador atual. O `C# 7.1` significa que você desejará usar o C# 7.1, mesmo depois que forem liberadas novas versões secundárias.

![Definindo a versão da linguagem](./media/csharp-7-1/advanced-build-settings.png)

Como alternativa, você pode editar o arquivo "csproj" e adicionar ou modificar as seguintes linhas:

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Se você usar o IDE do Visual Studio para atualizar os arquivos csproj, o IDE criará nós separados para cada configuração de build. Normalmente, você definirá o valor da mesma forma em todas as configurações de build, mas precisará defini-lo explicitamente para cada configuração de build ou selecionar "Todas as Configurações" ao modificar essa configuração. Você verá o seguinte no arquivo csproj:

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

As configurações válidas para o elemento `LangVersion` são:

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

As cadeias de caracteres especiais `default` e `latest` são resolvidas nas últimas versões da linguagem principal e secundária instaladas no computador de build, respectivamente.

Essa configuração desacopla a instalação de novas versões do SDK e das ferramentas no ambiente de desenvolvimento da escolha de incorporar novos recursos de linguagem em um projeto. Instale o último SDK e as últimas ferramentas no computador de build. Cada projeto pode ser configurado para usar uma versão específica da linguagem de seu build.

## <a name="async-main"></a>Async main

Um método *async main* permite que você use `await` no método `Main`.
Anteriormente, você precisava escrever:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Agora, você pode escrever:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Se o programa não retorna um código de saída, declare um método `Main` que retorna um <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Leia mais sobre os detalhes no tópico [async main](../programming-guide/main-and-command-args/index.md) no guia de programação.

## <a name="default-literal-expressions"></a>Expressões literais padrão

Expressões literais padrão são uma melhoria das expressões de valor padrão.
Essas expressões inicializam uma variável com o valor padrão. Nos casos em que você anteriormente escrevia:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Agora você pode omitir o tipo no lado direito da inicialização:

```csharp
Func<string, bool> whereClause = default;
```

Saiba mais sobre essa melhoria no tópico do Guia de Programação do C# em [expressões de valor padrão](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Essa melhoria também altera algumas das regras de análise da [palavra-chave padrão](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Nomes de elementos de tupla inferidos

Esse recurso é uma pequena melhoria do recurso de tuplas introduzido no C# 7.0. Muitas vezes quando você inicializa uma tupla, as variáveis usadas para o lado direito da atribuição são iguais aos nomes que você deseja usar para os elementos de tupla:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Os nomes dos elementos de tupla podem ser inferidos com base nas variáveis usadas para inicializar a tupla no C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Saiba mais sobre esse recurso no tópico [Tuplas](../tuples.md).

## <a name="reference-assembly-generation"></a>Geração de assembly de referência

Há duas novas opções do compilador que geram *assemblies somente de referência*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) e [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Os tópicos vinculados explicam essas opções e os assemblies de referência mais detalhadamente.
