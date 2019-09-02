---
title:
- TÍTULO DO ARTIGO
description: ''
author:
- GITHUB USERNAME
ms.author:
- MICROSOFT ALIAS OF INTERNAL OWNER
ms.date:
- CREATION/UPDATE DATE - mm/dd/yyyy
ms.topic:
- TOPIC TYPE
ms.prod:
- PRODUCT VALUE
helpviewer_keywords:
- OFFLINE BOOK INDEX ENTRIES
ms.openlocfilehash: e6c912f5ff9590f3b8cbb0f7e3f88e08fa9dd556
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106909"
---
# <a name="metadata-and-markdown-template"></a>Metadados e modelo Markdown

Esse modelo do dotnet/docs contém exemplos da sintaxe Markdown, bem como diretrizes de definição dos metadados. Para aproveitá-la ao máximo, é necessário exibir o [Markdown bruto](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) e a [exibição renderizada](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (por exemplo, o Markdown bruto mostra o bloco de metadados, ao contrário da exibição renderizada).

Ao criar um arquivo Markdown, é necessário copiar esse modelo para um novo arquivo, preencher os metadados conforme especificado abaixo, definir o cabeçalho H1 acima do título do artigo e excluir o conteúdo.

## <a name="metadata"></a>Metadados

O bloco de metadados completo é mostrado acima (no [Markdown bruto](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), dividido em campos obrigatórios e opcionais. Algumas observações importantes:

- **Deve** haver um espaço entre os dois-pontos (:) e o valor de um elemento de metadados.
- Se um elemento de metadados opcional não tiver um valor, comente o elemento com um # ou remova-o (não o deixe em branco nem use "na"). Se estiver adicionando um valor a um elemento que foi comentado, lembre-se de remover o #.
- Dois-pontos em um valor (por exemplo, um título) quebram o analisador de metadados. Nesse caso, coloque o título entre aspas duplas (por exemplo, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).
- **title**: É exibido nos resultados do mecanismo de pesquisa. O título não deve ser idêntico ao título do cabeçalho H1 e deve conter 60 caracteres ou menos.
- **description**: Resume o conteúdo do artigo. Geralmente, é mostrado na página dos resultados da pesquisa, mas não é usado para classificação de pesquisa. Seu tamanho deve ter de 115 a 145 caracteres, incluindo espaços.
- **author** e **ms.author**: O campo author deve conter o **nome de usuário do GitHub** do autor, não seu alias.  O campo **ms.author**, por outro lado, deve conter um alias da Microsoft e indica a pessoa responsável por manter o artigo.
- **ms.topic**: O tipo de tópico. O valor mais comum é `conceptual` e é definido em um nível global. Outros valores comuns usados são `tutorial`, `overview` e `reference`.
- **ms.devlang** define o filtro de linguagem exibido para o tópico. Você poderá ver uma lista dos valores compatíveis na seção [Linguagens compatíveis](#supported-languages). Só precisa ser definido quando há mais de uma linguagem de programação abordada no tópico. Normalmente, usamos apenas `csharp`, `vb`, `fsharp` e `cpp` para esse valor em nosso conteúdo.
- **ms.prod**: Identificação do produto usada para fins de BI. Normalmente, definido em um nível global, portanto, geralmente não é exibido no bloco de metadados de cada artigo.
- **ms.technology**: Classificação de BI adicional. Alguns dos valores compatíveis são: `devlang-csharp` para tópicos sobre C#, `devlang-fsharp` para tópicos sobre F# e `devlang-visual-basic` para tópicos sobre VB. Para outros guias, os valores poderão variar; portanto, solicite as diretrizes a um membro da equipe.
- **ms.date**: Uma data no formato MM/DD/AAAA. Exibido na página publicada para indicar a última vez em que o artigo foi substancialmente editado ou tem a garantia de estar "atualizado" (ou seja, o artigo foi revisado e é considerado atualizado).
- **helpviewer_keywords**: As entradas são usadas para o índice de manuais offline (funcionalidade do Visual Studio).
- **f1_keywords**: Conecta o artigo à tecla F1 (funcionalidade do Visual Studio).

## <a name="basic-markdown-gfm-and-special-characters"></a>Marcação básica, GFM e caracteres especiais

Há suporte para todo o GFM (GitHub Flavored Markdown) e básico. Para obter mais informações sobre eles, consulte:

- [Sintaxe Markdown de linha de base](https://daringfireball.net/projects/markdown/syntax)
- [Documentação de GFM](https://guides.github.com/features/mastering-markdown)

O Markdown usa caracteres especiais, como \*, \` e \# para formatação. Se desejar incluir um desses caracteres no conteúdo, realize uma destas ações:

- Coloque uma barra invertida antes do caractere especial para inserir “escape” nele (por exemplo, `\*` para um \*)
- Use o [código de entidade HTML](https://www.ascii.cl/htmlcodes.htm) do caractere (por exemplo, `&#42;` para um &#42;).

## <a name="file-name"></a>Nome do arquivo

Os nomes de arquivo usam as seguintes regras:

- Conter apenas letras minúsculas, números e hifens.
- Sem espaços nem caracteres de pontuação. Use os hifens para separar palavras e números no nome do arquivo.
- Use verbos de ação específicos, como desenvolver, comprar, compilar, solucionar problemas. Sem palavras no gerúndio.
- Sem palavras pequenas – não inclua artigos nem preposições.
- Deve estar em Markdown e usar a extensão de arquivo .md.
- Mantenha os nomes de arquivo razoavelmente curtos. Eles fazem parte da URL dos artigos.

## <a name="headings"></a>Títulos

Use a capitalização de estilo da frase. Sempre coloque em maiúsculas:

- A primeira palavra de um cabeçalho.
- A palavra após dois pontos em um título ou cabeçalho (por exemplo, "Como classificar uma matriz").

Os cabeçalhos devem ser feitos usando o atx-style ou seja, use de 1 a 6 caracteres de hash (#) no início da linha para indicar um cabeçalho correspondente aos níveis de cabeçalho HTML de H1 a H6. Exemplos de cabeçalhos de primeiro e segundo nível são usados acima.

**Deve** haver apenas um cabeçalho de primeiro nível (H1) no tópico, que será exibido como o título na página.

Se o cabeçalho terminar com um `#` caractere, você precisará adicionar um caractere `#` extra ao final para que o título seja renderizado corretamente. Por exemplo, `# Async Programming in F# #`.

Os cabeçalhos de segundo nível gerarão o Sumário na página exibida na seção “Neste artigo” sob o título na página.

### <a name="third-level-heading"></a>Cabeçalho de terceiro nível
#### <a name="fourth-level-heading"></a>Cabeçalho de quarto nível
##### <a name="fifth-level-heading"></a>Cabeçalho de quinto nível
###### <a name="sixth-level-heading"></a>Cabeçalho de sexto nível

## <a name="text-styling"></a>Estilo do texto

*Itálico* Use-o para arquivos, pastas, caminhos (para itens longos, dividido em sua própria linha) e novos termos.

**Negrito** Use para elementos de interface do usuário.

`Code` Use-o para código embutido, palavras-chave de linguagem, nomes de pacote NuGet, comandos de linha de comando, nomes de colunas e tabelas de banco de dados e URLs que você não deseja que sejam clicáveis.

## <a name="links"></a>Links

### <a name="internal-links"></a>Links internos

Para vincular a um cabeçalho no mesmo arquivo Markdown (também conhecido como links do tipo âncora), você precisará descobrir a ID do cabeçalho à qual está tentando vincular. Para confirmar a ID, exiba a origem do artigo renderizado, localize a ID do cabeçalho (por exemplo, `id="blockquote"`) e vincule-a usando # + ID (por exemplo, `#blockquote`).
A ID é gerada automaticamente com base no texto do cabeçalho. Assim, por exemplo, considerando uma seção exclusiva chamada `## Step 2`, a ID terá a aparência deste `id="step-2"`.

- Exemplo: `[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` produz [Declarar blocos embutidos com um identificador de linguagem](#inline-code-blocks-with-language-identifier).

Para vincular a um arquivo Markdown no mesmo repositório, use [links relativos](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), incluindo o “.md” ao final do nome de arquivo.

- Exemplo: `[Readme file](../README.md)` produz [arquivo Leiame](../README.md). (Observe que os links diferenciam maiúsculas de minúsculas.)
- Exemplo: `[Welcome to .NET](../docs/welcome.md)` produz [Bem-vindo ao .NET](../docs/welcome.md).

Para vincular a um cabeçalho em um arquivo Markdown no mesmo repositório, use a vinculação relativa + vinculação de hashtag.

- Exemplo: `[.NET Community](../docs/welcome.md#open-source)` produz [.NET Community](../docs/welcome.md#open-source).

Na maioria dos casos, usamos os links relativos e não incentivamos o uso de `~/` em links, pois os links relativos são resolvidos na origem no GitHub. No entanto, sempre que usarmos um link para um arquivo em um repositório dependente, usaremos o caractere `~/` para fornecer o caminho. Como os arquivos do repositório dependente estão em uma localização diferente no GitHub, os links não serão resolvidos corretamente com links relativos, independentemente de como foram gravados.

A especificação da linguagem C# e a especificação da linguagem Visual Basic estão incluídas na documentação do .NET, incluindo a origem dos repositórios de linguagem. As origens de markdown são gerenciadas nos repositórios [csharplang](https://github.com/dotnet/csharplang) e [visual basic](https://github.com/dotnet/vblang).

Os links para a especificação precisam apontar para os diretórios de origem nos quais essas especificações estão incluídas. Para o C#, ele é **~/_csharplang/spec** e para o VB, ele é **~/_vblang/spec**.

- Exemplo: `[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` produz [Expressões de consulta C#](~/_csharplang/spec/expressions.md#query-expressions).

### <a name="external-links"></a>Links externos

Para vincular a um arquivo externo, use a URL completa como o link.

- Exemplo: `[GitHub](https://www.github.com)` produz [GitHub](https://www.github.com).

Se uma URL for exibida em um arquivo Markdown, ela será transformada em um link clicável.

- Exemplo: `<https://www.github.com>` produz <https://www.github.com>.

Prefira o protocolo `https` para links externos. Só use links `http` para sites que não dão suporte a `https`.

### <a name="links-to-apis"></a>Links para APIs

O sistema de build tem algumas extensões que permitem vincular a APIs do .NET sem a necessidade de usar links externos.
Ao vincular a uma API, é possível usar seu UID (identificador exclusivo) que é gerado automaticamente com base no código-fonte.

O UID equivale ao tipo e ao nome totalmente qualificados do membro.

Se você adicionar um \* (ou %2A) após o UID, o link representará a página de sobrecarga e não uma API específica. Por exemplo, você poderá usar isso quando desejar criar um link para a página [List\<T>.BinarySearch Method](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch) de uma maneira genérica, em vez de uma sobrecarga específica, como [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_). Use também \* para criar um link para uma página de membro quando o membro não estiver sobrecarregado; isso evita que você precise incluir a lista de parâmetros no UID.

Para criar um link para uma sobrecarga de método específica, você precisará incluir o nome do tipo totalmente qualificado de cada um dos parâmetros do método. Por exemplo, \<xref:System.DateTime.ToString> é vinculado ao método [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) sem parâmetros, enquanto \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> é vinculado ao método [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_). Encontre os UIDs de um membro sobrecarregado específico em `https://xref.docs.microsoft.com/autocomplete`. A cadeia de consulta "?text= *\<type-member-name>* " identifica o tipo ou o membro cujos UIDs você deseja ver. Por exemplo, `https://xref.docs.microsoft.com/autocomplete?text=string.format` recupera as sobrecargas de [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format).

Para criar um link para um tipo genérico, como [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1), use o caractere ` (%60) seguido pelo número de parâmetros de tipo genérico. Por exemplo, \<xref:System.Nullable%601> é vinculado ao tipo [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1), enquanto \<xref:System.Func%602> é vinculado ao delegado [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2).

É possível usar uma das seguintes sintaxes:

1. Link automático: `<xref:UID>` ou `<xref:UID?displayProperty=nameWithType>`

   O parâmetro de consulta `displayProperty` produz um texto de link totalmente qualificado. Por padrão, o texto do link mostra apenas o nome do membro ou do tipo.

2. Link de markdown: `[link text](xref:UID)`

   Use-o quando desejar personalizar o texto do link exibido.

Exemplos:

- `<xref:System.String>` é renderizado como [String](https://docs.microsoft.com/dotnet/api/system.string)
- `<xref:System.String?displayProperty=nameWithType>` é renderizado como [System.String](https://docs.microsoft.com/dotnet/api/system.string)
- `[String class](xref:System.String)` é renderizado como uma [classe String](https://docs.microsoft.com/dotnet/api/system.string)

Para obter mais informações sobre como usar essa notação, consulte [Using cross reference](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference) (Usando a referência cruzada).

Há duas maneiras de encontrar o UID:

- Exiba a origem da página de API para a qual deseja criar um link e encontre o valor de ms.assetid. Observe que os valores de sobrecarga individuais não são mostrados na origem.
- Use a seguinte ferramenta para pesquisar UIDs: https://xref.docs.microsoft.com/autocomplete?text=tostring (substitua tostring pelas partes do nome da API que você está tentando encontrar). A ferramenta pesquisa o parâmetro de consulta `text` fornecido em qualquer parte do UID. Por exemplo, você pode pesquisar o nome do membro (ToString), o nome do membro parcial (ToStri), o nome do tipo e do membro (Double.ToString) etc.

Quando o UID contém os caracteres especiais \`, \# ou \*, o valor do UID precisa ser codificado em HTML como `%60`, `%23` e `%2A`, respectivamente. Às vezes, você verá parênteses codificados, mas isso não é um requisito.

Exemplos:

- System.Threading.Tasks.Task\`1 se torna `System.Threading.Tasks.Task%601`
- System.Exception.\#ctor se torna `System.Exception.%23ctor`
- System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) se torna `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`

## <a name="lists"></a>Listas

### <a name="ordered-lists"></a>Listas ordenadas

1. Este
1. É
1. Uma
1. Ordenada
1. Lista

#### <a name="ordered-list-with-an-embedded-list"></a>Lista ordenada com uma lista inserida

1. Esta
1. é
1. uma
1. lista
    1. Senhorita Costa
    1. Professor Mendes
1. ordered
1. lista

### <a name="unordered-lists"></a>Listas não ordenadas

- Este
- is
- a
- com marcadores
- lista

#### <a name="unordered-list-with-an-embedded-list"></a>Lista não ordenada com uma lista inserida

- Este
- com marcadores
- lista
  - Sra. Pereira
  - Sr. Martins
- contém
- outras
  1. Coronel Teixeira
  1. Sra. Barbosa
- listas

## <a name="horizontal-rule"></a>Régua horizontal

---

## <a name="tables"></a>Tabelas

| Tabelas        | São           | Legais  |
| ------------- |:-------------:| -----:|
| A coluna 3 está      | alinhada à direita | US$ 1.600 |
| A coluna 2 está      | centralizada      |   US$ 12 |
| A coluna 1 está por padrão | alinhada à esquerda     |    US$ 1 |

É possível usar uma [ferramenta de gerador de tabelas Markdown](https://www.tablesgenerator.com/markdown_tables) para ajudar a criá-las com mais facilidade.

## <a name="code"></a>Código

A melhor maneira de incluir código é incluir snippets de uma amostra funcional. Crie a amostra seguindo as instruções do [guia de contribuição](../CONTRIBUTING.md#contributing-to-samples).

Você pode incluir o código usando a seguinte sintaxe:

```markdown
[!code-<language>[<name>](<pathToFile><queryoption><queryoptionvalue>)]
```

- `-<language>` (*opcional*, mas *recomendado*)
  - Linguagem do snippet de código que está sendo referenciado. Para obter uma lista de valores compatíveis, confira [Linguagens compatíveis](#supported-languages).

- `<name>` (*opcional*)
  - Nome do snippet de código. Ele não tem nenhum impacto no HTML de saída, mas você pode usá-lo para melhorar a legibilidade da fonte Markdown.

- `<pathToFile>` (*obrigatório*)
  - Caminho relativo no sistema de arquivos que indica o arquivo de snippet de código a ser referenciado.

- `<queryoption>` e `<queryoptionvalue>` (*opcional*)
  - Usados em conjunto para especificar como o código deve ser recuperado do arquivo:
    - `#`: `#L{startlinenumber}-L{endlinenumber}` (intervalo de linhas) *ou* `#{tagname}` (nome da marca).
    Não incentivamos o uso de números de linha, pois são muito frágeis. O nome da marca é a maneira preferencial de referenciar snippets de código.
    - `range`: `?range=1,3-5` Um intervalo de linhas. Esse exemplo inclui as linhas 1, 3, 4 e 5.
    - `dedent`: `?dedent=8` Remove o recuo das linhas por um número de espaços – nesse caso, 8. Isso pode ser combinado com o `range` e outras opções de consulta que selecionam um subconjunto das linhas de um arquivo.
    - `outdent`: `?outdent=8` Inverte o recuo das linhas por um número de espaços – nesse caso, 8. Isso pode ser combinado com `range` e outras opções de consulta que selecionam um subconjunto das linhas de um arquivo.

Recomendamos o uso da opção de nome da marca sempre que possível. O nome da marca é o nome de uma região ou de um comentário de código no formato `Snippettagname` presente no código-fonte. O seguinte exemplo mostra como referenciar o nome da marca `1`:

```markdown
[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]
```

Você poderá ver como as marcas de snippet são estruturadas neste [arquivo de origem](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs). Para obter detalhes sobre a representação de nome da marca nos arquivos de origem do snippet de código por linguagem, confira as [diretrizes do DocFX](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file).

A inclusão de snippets de programas completos garante que todo o código é executado por meio de nosso sistema de CI (Integração Contínua). No entanto, se você precisar mostrar algo que causa erros de tempo de compilação ou de execução, será possível usar blocos de código embutidos.

### <a name="inline-code-blocks-with-language-identifier"></a>Blocos de código embutidos com identificador de linguagem

Use três backticks (\`\`\`) + uma ID de idioma para aplicar a codificação de cores específico a um idioma para um bloco de código. Veja a seguir a lista de idiomais compatíveis que mostram o rótulo de markdown para cada ID de idioma.

#### <a name="supported-languages"></a>Idiomas com suporte

|Nome|Rótulo de markdown|
|-----|-------|
|ASP.NET com C#|aspx-csharp|
|ASP.NET com VB|aspx-vb|
|CLI do Azure|azurecli|
|AzCopy|azcopy|
|C++|cpp|
|C#|csharp|
|C# no navegador|csharp-interactive|
|Console|console|
|F#|fsharp|
|Java|java|
|JavaScript|javascript|
|JSON|json|
|NodeJS|nodejs|
|Objective-C|objc|
|PHP|php|
|PowerShell|powershell|
|Python|python|
|Ruby|ruby|
|SQL|sql|
|Swift|swift|
|VB|vb|
|XAML|xaml|
|XML|xml|

O nome `csharp-interactive` especifica a linguagem C# e a capacidade de executar as amostras no navegador. Esses snippets são compilados e executados em um contêiner do Docker, e os resultados dessa execução do programa são exibidos na janela do navegador do usuário.

Veja a seguir exemplos de blocos de código usando as IDs de linguagem para o C# (\`\`\`csharp), o Python (\`\`\`python) e o PowerShell (\`\`\`powershell).

##### <a name="c9839"></a>C&#9839;

```csharp
using System;
namespace HelloWorld
{
    class Hello
    {
        static void Main()
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>Bloco de código genérico

Use três backticks (&#96;&#96;&#96;) para a codificação de bloco de código genérico.

> A abordagem recomendada é usar blocos de código com identificadores de linguagem, conforme explicado na seção anterior, para garantir o realce de sintaxe apropriado no site da documentação. Use blocos de código genérico somente quando necessário.

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

## <a name="blockquotes"></a>Blockquotes

> A seca agora se estende para dez milhões de anos e o reino dos terríveis lagartos desde então foi extinto. Aqui no Equador, no continente em que um dia seria conhecido como África, a luta pela existência atingiu um novo auge de ferocidade e o vencedor ainda não foi avistado. Nesta terra árida e desidratada, apenas as espécies pequenas, ágeis ou ferozes poderiam prosperar ou mesmo ter a esperança de sobreviver.

## <a name="images"></a>Imagens

### <a name="static-image-or-animated-gif"></a>Imagem estática ou GIF animado

```markdown
![this is the alt text](../images/Logo_DotNet.png)
```

![este é o texto Alt](../images/Logo_DotNet.png)

### <a name="linked-image"></a>Imagem vinculada

```markdown
[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)
```

[![texto Alt da imagem vinculada](../images/Logo_DotNet.png)](https://dot.net)

## <a name="videos"></a>Vídeos

No momento, é possível inserir vídeos do Channel 9 e do YouTube com a seguinte sintaxe:

### <a name="channel-9"></a>Channel 9

```markdown
> [!VIDEO <channel9_video_link>]
```

Para obter a URL correta do vídeo, selecione a guia **Inserir** abaixo do quadro de vídeo e copie a URL do elemento `<iframe>`. Por exemplo:

```markdown
> [!VIDEO https://channel9.msdn.com/Blogs/dotnet/NET-Core-20-Released/player]
```

### <a name="youtube"></a>YouTube

Para obter a URL correta do vídeo, clique com o botão direito do mouse no vídeo, selecione **Copiar Código de Inserção** e copie a URL do elemento `<iframe>`.

```markdown
> [!VIDEO <youtube_video_link>]
```

Por exemplo:

```markdown
> [!VIDEO https://www.youtube.com/embed/Q2mMbjw6cLA]
```

## <a name="docsmicrosoft-extensions"></a>Extensões docs.microsoft

O docs.microsoft fornece algumas extensões adicionais para o GitHub Flavored Markdown.

### <a name="alerts"></a>Alertas

É importante usar os estilos de alerta a seguir para que eles sejam renderizados com o estilo adequado no site da documentação. No entanto, o mecanismo de renderização no GitHub não os diferencia.

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

Eles serão renderizados assim: ![Estilos de alerta](../images/alerts.png)

### <a name="includes"></a>Inclui

Você pode inserir o Markdown de um arquivo em outro usando uma inclusão.

[!INCLUDE[sample include file](../includes/sampleinclude.md)]

### <a name="checked-lists"></a>Listas selecionadas

Um estilo personalizado está disponível para listas. Você pode renderizar listas com marcas de seleção verdes.

> [!div class="checklist"]
> - Como criar um aplicativo do .NET Core
> - Como adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator
> - Como editar o MyApp.csproj para adicionar dependências
> - Como adicionar uma classe e um XmlSerializer
> - Como compilar e executar o aplicativo

Veja um exemplo de listas selecionadas em ação na [documentação do .NET Core](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator).

### <a name="buttons"></a>Botões

> [!div class="button"]
> [links de botão](../docs/core/index.md)

Veja um exemplo de botões em ação na [documentação do Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio).

### <a name="selectors"></a>Seletores

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/with-visual-studio.md)

Veja um exemplo de seletores em ação na [documentação do Azure](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic).

### <a name="step-by-steps"></a>Passo a passo

>[!div class="step-by-step"]
>[Anterior](../docs/csharp/expression-trees-interpreting.md)
>[Próximo](../docs/csharp/expression-trees-translating.md)

Veja um exemplo de passo a passo em ação no [Guia do C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure).
