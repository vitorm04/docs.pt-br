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
# <a name="metadata-and-markdown-template"></a><span data-ttu-id="5c4c3-102">Metadados e modelo Markdown</span><span class="sxs-lookup"><span data-stu-id="5c4c3-102">Metadata and Markdown Template</span></span>

<span data-ttu-id="5c4c3-103">Esse modelo do dotnet/docs contém exemplos da sintaxe Markdown, bem como diretrizes de definição dos metadados.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-103">This dotnet/docs template contains examples of Markdown syntax, as well as guidance on setting the metadata.</span></span> <span data-ttu-id="5c4c3-104">Para aproveitá-la ao máximo, é necessário exibir o [Markdown bruto](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) e a [exibição renderizada](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (por exemplo, o Markdown bruto mostra o bloco de metadados, ao contrário da exibição renderizada).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-104">To get the most of it, you must view both the [raw Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) and the [rendered view](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (for instance, the raw Markdown shows the metadata block, while the rendered view does not).</span></span>

<span data-ttu-id="5c4c3-105">Ao criar um arquivo Markdown, é necessário copiar esse modelo para um novo arquivo, preencher os metadados conforme especificado abaixo, definir o cabeçalho H1 acima do título do artigo e excluir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-105">When creating a Markdown file, you should copy this template to a new file, fill out the metadata as specified below, set the H1 heading above to the title of the article, and delete the content.</span></span>

## <a name="metadata"></a><span data-ttu-id="5c4c3-106">Metadados</span><span class="sxs-lookup"><span data-stu-id="5c4c3-106">Metadata</span></span>

<span data-ttu-id="5c4c3-107">O bloco de metadados completo é mostrado acima (no [Markdown bruto](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), dividido em campos obrigatórios e opcionais.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-107">The full metadata block is above (in the [raw Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), divided into required fields and optional fields.</span></span> <span data-ttu-id="5c4c3-108">Algumas observações importantes:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-108">Some key notes:</span></span>

- <span data-ttu-id="5c4c3-109">**Deve** haver um espaço entre os dois-pontos (:) e o valor de um elemento de metadados.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-109">You **must** have a space between the colon (:) and the value for a metadata element.</span></span>
- <span data-ttu-id="5c4c3-110">Se um elemento de metadados opcional não tiver um valor, comente o elemento com um # ou remova-o (não o deixe em branco nem use "na").</span><span class="sxs-lookup"><span data-stu-id="5c4c3-110">If an optional metadata element doesn't have a value, comment out the element with a # or remove it (don't leave it blank or use "na").</span></span> <span data-ttu-id="5c4c3-111">Se estiver adicionando um valor a um elemento que foi comentado, lembre-se de remover o #.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-111">If you're adding a value to an element that was commented out, be sure to remove the #.</span></span>
- <span data-ttu-id="5c4c3-112">Dois-pontos em um valor (por exemplo, um título) quebram o analisador de metadados.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-112">Colons in a value (for example, a title) break the metadata parser.</span></span> <span data-ttu-id="5c4c3-113">Nesse caso, coloque o título entre aspas duplas (por exemplo, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-113">In this case, surround the title with double quotes (for example, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).</span></span>
- <span data-ttu-id="5c4c3-114">**title**: É exibido nos resultados do mecanismo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-114">**title**: Appears in search engine results.</span></span> <span data-ttu-id="5c4c3-115">O título não deve ser idêntico ao título do cabeçalho H1 e deve conter 60 caracteres ou menos.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-115">The title shouldn't be identical to the title in your H1 heading, and it should contain 60 characters or less.</span></span>
- <span data-ttu-id="5c4c3-116">**description**: Resume o conteúdo do artigo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-116">**description**: Summarizes the content of the article.</span></span> <span data-ttu-id="5c4c3-117">Geralmente, é mostrado na página dos resultados da pesquisa, mas não é usado para classificação de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-117">It's usually shown in the search results page, but it isn't used for search ranking.</span></span> <span data-ttu-id="5c4c3-118">Seu tamanho deve ter de 115 a 145 caracteres, incluindo espaços.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-118">Its length should be 115-145 characters including spaces.</span></span>
- <span data-ttu-id="5c4c3-119">**author** e **ms.author**: O campo author deve conter o **nome de usuário do GitHub** do autor, não seu alias.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-119">**author** and **ms.author**: The author field should contain the **GitHub username** of the author, not his/her alias.</span></span>  <span data-ttu-id="5c4c3-120">O campo **ms.author**, por outro lado, deve conter um alias da Microsoft e indica a pessoa responsável por manter o artigo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-120">The **ms.author** field, on the other hand, should contain a Microsoft alias and indicates the person responsible for maintaining the article.</span></span>
- <span data-ttu-id="5c4c3-121">**ms.topic**: O tipo de tópico.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-121">**ms.topic**: The topic type.</span></span> <span data-ttu-id="5c4c3-122">O valor mais comum é `conceptual` e é definido em um nível global.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-122">The most common value is `conceptual` and is set at a global level.</span></span> <span data-ttu-id="5c4c3-123">Outros valores comuns usados são `tutorial`, `overview` e `reference`.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-123">Other common values used are `tutorial`, `overview`, and `reference`.</span></span>
- <span data-ttu-id="5c4c3-124">**ms.devlang** define o filtro de linguagem exibido para o tópico.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-124">**ms.devlang** defines the language filter displayed for the topic.</span></span> <span data-ttu-id="5c4c3-125">Você poderá ver uma lista dos valores compatíveis na seção [Linguagens compatíveis](#supported-languages).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-125">You can see a list of the supported values in the [Supported languages](#supported-languages) section.</span></span> <span data-ttu-id="5c4c3-126">Só precisa ser definido quando há mais de uma linguagem de programação abordada no tópico.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-126">Only needs to be set when there's more than one programming language covered in the topic.</span></span> <span data-ttu-id="5c4c3-127">Normalmente, usamos apenas `csharp`, `vb`, `fsharp` e `cpp` para esse valor em nosso conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-127">Typically, we only use `csharp`, `vb`, `fsharp`, and `cpp` for this value in our content.</span></span>
- <span data-ttu-id="5c4c3-128">**ms.prod**: Identificação do produto usada para fins de BI.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-128">**ms.prod**: Product identification used for BI purposes.</span></span> <span data-ttu-id="5c4c3-129">Normalmente, definido em um nível global, portanto, geralmente não é exibido no bloco de metadados de cada artigo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-129">They're usually set at a global level, so they don't usually appear in the metadata block of each article.</span></span>
- <span data-ttu-id="5c4c3-130">**ms.technology**: Classificação de BI adicional.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-130">**ms.technology**: Additional BI classification.</span></span> <span data-ttu-id="5c4c3-131">Alguns dos valores compatíveis são: `devlang-csharp` para tópicos sobre C#, `devlang-fsharp` para tópicos sobre F# e `devlang-visual-basic` para tópicos sobre VB.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-131">Some of the supported values are: `devlang-csharp` for C# topics, `devlang-fsharp` for F# topics, and `devlang-visual-basic` for VB topics.</span></span> <span data-ttu-id="5c4c3-132">Para outros guias, os valores poderão variar; portanto, solicite as diretrizes a um membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-132">For other guides, the values will vary, so ask a member of the team for guidance.</span></span>
- <span data-ttu-id="5c4c3-133">**ms.date**: Uma data no formato MM/DD/AAAA.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-133">**ms.date**: A date in the format MM/DD/YYYY.</span></span> <span data-ttu-id="5c4c3-134">Exibido na página publicada para indicar a última vez em que o artigo foi substancialmente editado ou tem a garantia de estar "atualizado" (ou seja, o artigo foi revisado e é considerado atualizado).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-134">Displayed on the published page to indicate the last time the article was substantially edited or guaranteed "fresh" (that is, the article was reviewed and considered up-to-date).</span></span>
- <span data-ttu-id="5c4c3-135">**helpviewer_keywords**: As entradas são usadas para o índice de manuais offline (funcionalidade do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-135">**helpviewer_keywords**: Entries are used for the offline books index (functionality in Visual Studio).</span></span>
- <span data-ttu-id="5c4c3-136">**f1_keywords**: Conecta o artigo à tecla F1 (funcionalidade do Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-136">**f1_keywords**: Connects the article to the F1 key (functionality in Visual Studio).</span></span>

## <a name="basic-markdown-gfm-and-special-characters"></a><span data-ttu-id="5c4c3-137">Marcação básica, GFM e caracteres especiais</span><span class="sxs-lookup"><span data-stu-id="5c4c3-137">Basic Markdown, GFM, and special characters</span></span>

<span data-ttu-id="5c4c3-138">Há suporte para todo o GFM (GitHub Flavored Markdown) e básico.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-138">All basic and GitHub Flavored Markdown (GFM) is supported.</span></span> <span data-ttu-id="5c4c3-139">Para obter mais informações sobre eles, consulte:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-139">For more information on these, see:</span></span>

- [<span data-ttu-id="5c4c3-140">Sintaxe Markdown de linha de base</span><span class="sxs-lookup"><span data-stu-id="5c4c3-140">Baseline Markdown syntax</span></span>](https://daringfireball.net/projects/markdown/syntax)
- [<span data-ttu-id="5c4c3-141">Documentação de GFM</span><span class="sxs-lookup"><span data-stu-id="5c4c3-141">GFM documentation</span></span>](https://guides.github.com/features/mastering-markdown)

<span data-ttu-id="5c4c3-142">O Markdown usa caracteres especiais, como \*, \` e \# para formatação.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-142">Markdown uses special characters such as \*, \`, and \# for formatting.</span></span> <span data-ttu-id="5c4c3-143">Se desejar incluir um desses caracteres no conteúdo, realize uma destas ações:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-143">If you wish to include one of these characters in your content, you must do one of two things:</span></span>

- <span data-ttu-id="5c4c3-144">Coloque uma barra invertida antes do caractere especial para inserir “escape” nele (por exemplo, `\*` para um \*)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-144">Put a backslash before the special character to "escape" it (for example, `\*` for a \*)</span></span>
- <span data-ttu-id="5c4c3-145">Use o [código de entidade HTML](https://www.ascii.cl/htmlcodes.htm) do caractere (por exemplo, `&#42;` para um &#42;).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-145">Use the [HTML entity code](https://www.ascii.cl/htmlcodes.htm) for the character (for example, `&#42;` for a &#42;).</span></span>

## <a name="file-name"></a><span data-ttu-id="5c4c3-146">Nome do arquivo</span><span class="sxs-lookup"><span data-stu-id="5c4c3-146">File name</span></span>

<span data-ttu-id="5c4c3-147">Os nomes de arquivo usam as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-147">File names use the following rules:</span></span>

- <span data-ttu-id="5c4c3-148">Conter apenas letras minúsculas, números e hifens.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-148">Contain only lowercase letters, numbers, and hyphens.</span></span>
- <span data-ttu-id="5c4c3-149">Sem espaços nem caracteres de pontuação.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-149">No spaces or punctuation characters.</span></span> <span data-ttu-id="5c4c3-150">Use os hifens para separar palavras e números no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-150">Use the hyphens to separate words and numbers in the file name.</span></span>
- <span data-ttu-id="5c4c3-151">Use verbos de ação específicos, como desenvolver, comprar, compilar, solucionar problemas.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-151">Use action verbs that are specific, such as develop, buy, build, troubleshoot.</span></span> <span data-ttu-id="5c4c3-152">Sem palavras no gerúndio.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-152">No -ing words.</span></span>
- <span data-ttu-id="5c4c3-153">Sem palavras pequenas – não inclua artigos nem preposições.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-153">No small words - don't include a, and, the, in, or, etc.</span></span>
- <span data-ttu-id="5c4c3-154">Deve estar em Markdown e usar a extensão de arquivo .md.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-154">Must be in Markdown and use the .md file extension.</span></span>
- <span data-ttu-id="5c4c3-155">Mantenha os nomes de arquivo razoavelmente curtos.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-155">Keep file names reasonably short.</span></span> <span data-ttu-id="5c4c3-156">Eles fazem parte da URL dos artigos.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-156">They are part of the URL for your articles.</span></span>

## <a name="headings"></a><span data-ttu-id="5c4c3-157">Títulos</span><span class="sxs-lookup"><span data-stu-id="5c4c3-157">Headings</span></span>

<span data-ttu-id="5c4c3-158">Use a capitalização de estilo da frase.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-158">Use sentence-style capitalization.</span></span> <span data-ttu-id="5c4c3-159">Sempre coloque em maiúsculas:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-159">Always capitalize:</span></span>

- <span data-ttu-id="5c4c3-160">A primeira palavra de um cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-160">The first word of a heading.</span></span>
- <span data-ttu-id="5c4c3-161">A palavra após dois pontos em um título ou cabeçalho (por exemplo, "Como classificar uma matriz").</span><span class="sxs-lookup"><span data-stu-id="5c4c3-161">The word following a colon in a title or heading (for example, "How to: Sort an array").</span></span>

<span data-ttu-id="5c4c3-162">Os cabeçalhos devem ser feitos usando o atx-style ou seja, use de 1 a 6 caracteres de hash (#) no início da linha para indicar um cabeçalho correspondente aos níveis de cabeçalho HTML de H1 a H6.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-162">Headings should be done using atx-style, that is, use 1-6 hash characters (#) at the start of the line to indicate a heading, corresponding to HTML headings levels H1 through H6.</span></span> <span data-ttu-id="5c4c3-163">Exemplos de cabeçalhos de primeiro e segundo nível são usados acima.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-163">Examples of first- and second-level headers are used above.</span></span>

<span data-ttu-id="5c4c3-164">**Deve** haver apenas um cabeçalho de primeiro nível (H1) no tópico, que será exibido como o título na página.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-164">There **must** be only one first-level heading (H1) in your topic, which will be displayed as the on-page title.</span></span>

<span data-ttu-id="5c4c3-165">Se o cabeçalho terminar com um `#` caractere, você precisará adicionar um caractere `#` extra ao final para que o título seja renderizado corretamente.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-165">If your heading finishes with a `#` character, you need to add an extra `#` character in the end in order for the title to render correctly.</span></span> <span data-ttu-id="5c4c3-166">Por exemplo, `# Async Programming in F# #`.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-166">For example, `# Async Programming in F# #`.</span></span>

<span data-ttu-id="5c4c3-167">Os cabeçalhos de segundo nível gerarão o Sumário na página exibida na seção “Neste artigo” sob o título na página.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-167">Second-level headings will generate the on-page TOC that appears in the "In this article" section underneath the on-page title.</span></span>

### <a name="third-level-heading"></a><span data-ttu-id="5c4c3-168">Cabeçalho de terceiro nível</span><span class="sxs-lookup"><span data-stu-id="5c4c3-168">Third-level heading</span></span>
#### <a name="fourth-level-heading"></a><span data-ttu-id="5c4c3-169">Cabeçalho de quarto nível</span><span class="sxs-lookup"><span data-stu-id="5c4c3-169">Fourth-level heading</span></span>
##### <a name="fifth-level-heading"></a><span data-ttu-id="5c4c3-170">Cabeçalho de quinto nível</span><span class="sxs-lookup"><span data-stu-id="5c4c3-170">Fifth level heading</span></span>
###### <a name="sixth-level-heading"></a><span data-ttu-id="5c4c3-171">Cabeçalho de sexto nível</span><span class="sxs-lookup"><span data-stu-id="5c4c3-171">Sixth-level heading</span></span>

## <a name="text-styling"></a><span data-ttu-id="5c4c3-172">Estilo do texto</span><span class="sxs-lookup"><span data-stu-id="5c4c3-172">Text styling</span></span>

<span data-ttu-id="5c4c3-173">*Itálico* Use-o para arquivos, pastas, caminhos (para itens longos, dividido em sua própria linha) e novos termos.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-173">*Italics* Use for files, folders, paths (for long items, split onto their own line), new terms.</span></span>

<span data-ttu-id="5c4c3-174">**Negrito** Use para elementos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-174">**Bold** Use for UI elements.</span></span>

<span data-ttu-id="5c4c3-175">`Code` Use-o para código embutido, palavras-chave de linguagem, nomes de pacote NuGet, comandos de linha de comando, nomes de colunas e tabelas de banco de dados e URLs que você não deseja que sejam clicáveis.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-175">`Code` Use for inline code, language keywords, NuGet package names, command-line commands, database table and column names, and URLs that you don't want to be clickable.</span></span>

## <a name="links"></a><span data-ttu-id="5c4c3-176">Links</span><span class="sxs-lookup"><span data-stu-id="5c4c3-176">Links</span></span>

### <a name="internal-links"></a><span data-ttu-id="5c4c3-177">Links internos</span><span class="sxs-lookup"><span data-stu-id="5c4c3-177">Internal Links</span></span>

<span data-ttu-id="5c4c3-178">Para vincular a um cabeçalho no mesmo arquivo Markdown (também conhecido como links do tipo âncora), você precisará descobrir a ID do cabeçalho à qual está tentando vincular.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-178">To link to a header in the same Markdown file (also known as anchor links), you'll need to find out the id of the header you're trying to link to.</span></span> <span data-ttu-id="5c4c3-179">Para confirmar a ID, exiba a origem do artigo renderizado, localize a ID do cabeçalho (por exemplo, `id="blockquote"`) e vincule-a usando # + ID (por exemplo, `#blockquote`).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-179">To confirm the ID, view the source of the rendered article, find the id of the header (for example, `id="blockquote"`), and link using # + id (for example, `#blockquote`).</span></span>
<span data-ttu-id="5c4c3-180">A ID é gerada automaticamente com base no texto do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-180">The id is auto-generated based on the header text.</span></span> <span data-ttu-id="5c4c3-181">Assim, por exemplo, considerando uma seção exclusiva chamada `## Step 2`, a ID terá a aparência deste `id="step-2"`.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-181">So, for example, given a unique section named `## Step 2`, the id would look like this `id="step-2"`.</span></span>

- <span data-ttu-id="5c4c3-182">Exemplo: `[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` produz [Declarar blocos embutidos com um identificador de linguagem](#inline-code-blocks-with-language-identifier).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-182">Example: `[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` produces [Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier).</span></span>

<span data-ttu-id="5c4c3-183">Para vincular a um arquivo Markdown no mesmo repositório, use [links relativos](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), incluindo o “.md” ao final do nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-183">To link to a Markdown file in the same repo, use [relative links](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), including the ".md" at the end of the filename.</span></span>

- <span data-ttu-id="5c4c3-184">Exemplo: `[Readme file](../README.md)` produz [arquivo Leiame](../README.md).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-184">Example: `[Readme file](../README.md)` produces [Readme file](../README.md).</span></span> <span data-ttu-id="5c4c3-185">(Observe que os links diferenciam maiúsculas de minúsculas.)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-185">(Note that links are case-sensitive.)</span></span>
- <span data-ttu-id="5c4c3-186">Exemplo: `[Welcome to .NET](../docs/welcome.md)` produz [Bem-vindo ao .NET](../docs/welcome.md).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-186">Example: `[Welcome to .NET](../docs/welcome.md)` produces [Welcome to .NET](../docs/welcome.md).</span></span>

<span data-ttu-id="5c4c3-187">Para vincular a um cabeçalho em um arquivo Markdown no mesmo repositório, use a vinculação relativa + vinculação de hashtag.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-187">To link to a header in a Markdown file in the same repo, use relative linking + hashtag linking.</span></span>

- <span data-ttu-id="5c4c3-188">Exemplo: `[.NET Community](../docs/welcome.md#open-source)` produz [.NET Community](../docs/welcome.md#open-source).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-188">Example: `[.NET Community](../docs/welcome.md#open-source)` produces [.NET Community](../docs/welcome.md#open-source).</span></span>

<span data-ttu-id="5c4c3-189">Na maioria dos casos, usamos os links relativos e não incentivamos o uso de `~/` em links, pois os links relativos são resolvidos na origem no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-189">In most cases, we use the relative links and discourage the use of `~/` in links because relative links resolve in the source on GitHub.</span></span> <span data-ttu-id="5c4c3-190">No entanto, sempre que usarmos um link para um arquivo em um repositório dependente, usaremos o caractere `~/` para fornecer o caminho.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-190">However, whenever we link to a file in a dependent repo, we'll use the `~/` character to provide the path.</span></span> <span data-ttu-id="5c4c3-191">Como os arquivos do repositório dependente estão em uma localização diferente no GitHub, os links não serão resolvidos corretamente com links relativos, independentemente de como foram gravados.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-191">Because the files in the dependent repo are in a different location in GitHub the links won't resolve correctly with relative links regardless of how they were written.</span></span>

<span data-ttu-id="5c4c3-192">A especificação da linguagem C# e a especificação da linguagem Visual Basic estão incluídas na documentação do .NET, incluindo a origem dos repositórios de linguagem.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-192">The C# language specification and the Visual Basic language specification are included in the .NET docs by including the source from the language repositories.</span></span> <span data-ttu-id="5c4c3-193">As origens de markdown são gerenciadas nos repositórios [csharplang](https://github.com/dotnet/csharplang) e [visual basic](https://github.com/dotnet/vblang).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-193">The markdown sources are managed in the [csharplang](https://github.com/dotnet/csharplang) and [visual basic](https://github.com/dotnet/vblang) repositories.</span></span>

<span data-ttu-id="5c4c3-194">Os links para a especificação precisam apontar para os diretórios de origem nos quais essas especificações estão incluídas.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-194">Links to the spec must point to the source directories where those specs are included.</span></span> <span data-ttu-id="5c4c3-195">Para o C#, ele é **~/_csharplang/spec** e para o VB, ele é **~/_vblang/spec**.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-195">For C#, it's **~/_csharplang/spec** and for VB, it's **~/_vblang/spec**.</span></span>

- <span data-ttu-id="5c4c3-196">Exemplo: `[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` produz [Expressões de consulta C#](~/_csharplang/spec/expressions.md#query-expressions).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-196">Example: `[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` produces [C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions).</span></span>

### <a name="external-links"></a><span data-ttu-id="5c4c3-197">Links externos</span><span class="sxs-lookup"><span data-stu-id="5c4c3-197">External Links</span></span>

<span data-ttu-id="5c4c3-198">Para vincular a um arquivo externo, use a URL completa como o link.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-198">To link to an external file, use the full URL as the link.</span></span>

- <span data-ttu-id="5c4c3-199">Exemplo: `[GitHub](https://www.github.com)` produz [GitHub](https://www.github.com).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-199">Example: `[GitHub](https://www.github.com)` produces [GitHub](https://www.github.com).</span></span>

<span data-ttu-id="5c4c3-200">Se uma URL for exibida em um arquivo Markdown, ela será transformada em um link clicável.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-200">If a URL appears in a Markdown file, it will be transformed into a clickable link.</span></span>

- <span data-ttu-id="5c4c3-201">Exemplo: `<https://www.github.com>` produz <https://www.github.com>.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-201">Example: `<https://www.github.com>` produces <https://www.github.com>.</span></span>

<span data-ttu-id="5c4c3-202">Prefira o protocolo `https` para links externos.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-202">Prefer the `https` protocol for external links.</span></span> <span data-ttu-id="5c4c3-203">Só use links `http` para sites que não dão suporte a `https`.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-203">Only use `http` links for sites that do not support `https`.</span></span>

### <a name="links-to-apis"></a><span data-ttu-id="5c4c3-204">Links para APIs</span><span class="sxs-lookup"><span data-stu-id="5c4c3-204">Links to APIs</span></span>

<span data-ttu-id="5c4c3-205">O sistema de build tem algumas extensões que permitem vincular a APIs do .NET sem a necessidade de usar links externos.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-205">The build system has some extensions that allow us to link to .NET APIs without having to use external links.</span></span>
<span data-ttu-id="5c4c3-206">Ao vincular a uma API, é possível usar seu UID (identificador exclusivo) que é gerado automaticamente com base no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-206">When linking to an API, you can use its unique identifier (UID) that is auto-generated from the source code.</span></span>

<span data-ttu-id="5c4c3-207">O UID equivale ao tipo e ao nome totalmente qualificados do membro.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-207">The UID equates to the fully qualified type and member name.</span></span>

<span data-ttu-id="5c4c3-208">Se você adicionar um \* (ou %2A) após o UID, o link representará a página de sobrecarga e não uma API específica.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-208">If you add a \* (or %2A) after the UID, the link then represents the overload page and not a specific API.</span></span> <span data-ttu-id="5c4c3-209">Por exemplo, você poderá usar isso quando desejar criar um link para a página [List\<T>.BinarySearch Method](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch) de uma maneira genérica, em vez de uma sobrecarga específica, como [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-209">For example, you can use that when you want to link to the [List\<T>.BinarySearch Method](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch) page in a generic way instead of a specific overload such as [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_).</span></span> <span data-ttu-id="5c4c3-210">Use também \* para criar um link para uma página de membro quando o membro não estiver sobrecarregado; isso evita que você precise incluir a lista de parâmetros no UID.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-210">You can also use \* to link to a member page when the member is not overloaded; this saves you from having to include the parameter list in the UID.</span></span>

<span data-ttu-id="5c4c3-211">Para criar um link para uma sobrecarga de método específica, você precisará incluir o nome do tipo totalmente qualificado de cada um dos parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-211">To link to a specific method overload, you must include the fully qualified type name of each of the method's parameters.</span></span> <span data-ttu-id="5c4c3-212">Por exemplo, \<xref:System.DateTime.ToString> é vinculado ao método [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) sem parâmetros, enquanto \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> é vinculado ao método [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-212">For example, \<xref:System.DateTime.ToString> links to the parameterless [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) method, while \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> links to the  [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_) method.</span></span> <span data-ttu-id="5c4c3-213">Encontre os UIDs de um membro sobrecarregado específico em `https://xref.docs.microsoft.com/autocomplete`.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-213">You can find the UIDs of a particular overloaded member from `https://xref.docs.microsoft.com/autocomplete`.</span></span> <span data-ttu-id="5c4c3-214">A cadeia de consulta "?text= *\<type-member-name>* " identifica o tipo ou o membro cujos UIDs você deseja ver.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-214">The query string "?text=*\<type-member-name>*" identifies the type or member whose UIDs you'd like to see.</span></span> <span data-ttu-id="5c4c3-215">Por exemplo, `https://xref.docs.microsoft.com/autocomplete?text=string.format` recupera as sobrecargas de [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-215">For example, `https://xref.docs.microsoft.com/autocomplete?text=string.format` retrieves the [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format) overloads.</span></span>

<span data-ttu-id="5c4c3-216">Para criar um link para um tipo genérico, como [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1), use o caractere \` (%60) seguido pelo número de parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-216">To link to a generic type, such as [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1), you use the \` (%60) character followed by the number of generic type parameters.</span></span> <span data-ttu-id="5c4c3-217">Por exemplo, \<xref:System.Nullable%601> é vinculado ao tipo [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1), enquanto \<xref:System.Func%602> é vinculado ao delegado [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-217">For example, \<xref:System.Nullable%601> links to the [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1) type, while \<xref:System.Func%602> links to the [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2) delegate.</span></span>

<span data-ttu-id="5c4c3-218">É possível usar uma das seguintes sintaxes:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-218">You can use one of the following syntax:</span></span>

1. <span data-ttu-id="5c4c3-219">Link automático: `<xref:UID>` ou `<xref:UID?displayProperty=nameWithType>`</span><span class="sxs-lookup"><span data-stu-id="5c4c3-219">Auto-link: `<xref:UID>` or `<xref:UID?displayProperty=nameWithType>`</span></span>

   <span data-ttu-id="5c4c3-220">O parâmetro de consulta `displayProperty` produz um texto de link totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-220">The `displayProperty` query    parameter produces a fully qualified link text.</span></span> <span data-ttu-id="5c4c3-221">Por padrão, o texto do link mostra apenas o nome do membro ou do tipo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-221">By default, link text shows only the member or type name.</span></span>

2. <span data-ttu-id="5c4c3-222">Link de markdown: `[link text](xref:UID)`</span><span class="sxs-lookup"><span data-stu-id="5c4c3-222">Markdown link: `[link text](xref:UID)`</span></span>

   <span data-ttu-id="5c4c3-223">Use-o quando desejar personalizar o texto do link exibido.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-223">Use when you want to customize the link text displayed.</span></span>

<span data-ttu-id="5c4c3-224">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-224">Examples:</span></span>

- <span data-ttu-id="5c4c3-225">`<xref:System.String>` é renderizado como [String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-225">`<xref:System.String>` renders as [String](https://docs.microsoft.com/dotnet/api/system.string)</span></span>
- <span data-ttu-id="5c4c3-226">`<xref:System.String?displayProperty=nameWithType>` é renderizado como [System.String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-226">`<xref:System.String?displayProperty=nameWithType>` renders as [System.String](https://docs.microsoft.com/dotnet/api/system.string)</span></span>
- <span data-ttu-id="5c4c3-227">`[String class](xref:System.String)` é renderizado como uma [classe String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-227">`[String class](xref:System.String)` renders as [String class](https://docs.microsoft.com/dotnet/api/system.string)</span></span>

<span data-ttu-id="5c4c3-228">Para obter mais informações sobre como usar essa notação, consulte [Using cross reference](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference) (Usando a referência cruzada).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-228">For more information about using this notation, see [Using cross reference](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).</span></span>

<span data-ttu-id="5c4c3-229">Há duas maneiras de encontrar o UID:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-229">There are two ways to find the UID:</span></span>

- <span data-ttu-id="5c4c3-230">Exiba a origem da página de API para a qual deseja criar um link e encontre o valor de ms.assetid.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-230">View the source for the API page you want to link to and find the ms.assetid value.</span></span> <span data-ttu-id="5c4c3-231">Observe que os valores de sobrecarga individuais não são mostrados na origem.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-231">Note that individual overload values are not shown in the source.</span></span>
- <span data-ttu-id="5c4c3-232">Use a seguinte ferramenta para pesquisar UIDs: https://xref.docs.microsoft.com/autocomplete?text=tostring (substitua tostring pelas partes do nome da API que você está tentando encontrar).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-232">Use the following tool to search for UIDs: https://xref.docs.microsoft.com/autocomplete?text=tostring (replace tostring with parts of the API name you're trying to find).</span></span> <span data-ttu-id="5c4c3-233">A ferramenta pesquisa o parâmetro de consulta `text` fornecido em qualquer parte do UID.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-233">The tool searches for the provided `text` query parameter in any part of the UID.</span></span> <span data-ttu-id="5c4c3-234">Por exemplo, você pode pesquisar o nome do membro (ToString), o nome do membro parcial (ToStri), o nome do tipo e do membro (Double.ToString) etc.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-234">For example, you can search for member name (ToString), partial member name (ToStri), type and member name (Double.ToString), etc.</span></span>

<span data-ttu-id="5c4c3-235">Quando o UID contém os caracteres especiais \`, \# ou \*, o valor do UID precisa ser codificado em HTML como `%60`, `%23` e `%2A`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-235">When the UID contains the special characters \`, \# or \*, the UID value needs to be HTML encoded as `%60`, `%23` and `%2A` respectively.</span></span> <span data-ttu-id="5c4c3-236">Às vezes, você verá parênteses codificados, mas isso não é um requisito.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-236">You'll sometimes see parentheses encoded but it's not a requirement.</span></span>

<span data-ttu-id="5c4c3-237">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-237">Examples:</span></span>

- <span data-ttu-id="5c4c3-238">System.Threading.Tasks.Task\`1 se torna `System.Threading.Tasks.Task%601`</span><span class="sxs-lookup"><span data-stu-id="5c4c3-238">System.Threading.Tasks.Task\`1 becomes `System.Threading.Tasks.Task%601`</span></span>
- <span data-ttu-id="5c4c3-239">System.Exception.\#ctor se torna `System.Exception.%23ctor`</span><span class="sxs-lookup"><span data-stu-id="5c4c3-239">System.Exception.\#ctor becomes `System.Exception.%23ctor`</span></span>
- <span data-ttu-id="5c4c3-240">System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) se torna `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`</span><span class="sxs-lookup"><span data-stu-id="5c4c3-240">System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) becomes  `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`</span></span>

## <a name="lists"></a><span data-ttu-id="5c4c3-241">Listas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-241">Lists</span></span>

### <a name="ordered-lists"></a><span data-ttu-id="5c4c3-242">Listas ordenadas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-242">Ordered lists</span></span>

1. <span data-ttu-id="5c4c3-243">Este</span><span class="sxs-lookup"><span data-stu-id="5c4c3-243">This</span></span>
1. <span data-ttu-id="5c4c3-244">É</span><span class="sxs-lookup"><span data-stu-id="5c4c3-244">Is</span></span>
1. <span data-ttu-id="5c4c3-245">Uma</span><span class="sxs-lookup"><span data-stu-id="5c4c3-245">An</span></span>
1. <span data-ttu-id="5c4c3-246">Ordenada</span><span class="sxs-lookup"><span data-stu-id="5c4c3-246">Ordered</span></span>
1. <span data-ttu-id="5c4c3-247">Lista</span><span class="sxs-lookup"><span data-stu-id="5c4c3-247">List</span></span>

#### <a name="ordered-list-with-an-embedded-list"></a><span data-ttu-id="5c4c3-248">Lista ordenada com uma lista inserida</span><span class="sxs-lookup"><span data-stu-id="5c4c3-248">Ordered list with an embedded list</span></span>

1. <span data-ttu-id="5c4c3-249">Esta</span><span class="sxs-lookup"><span data-stu-id="5c4c3-249">Here</span></span>
1. <span data-ttu-id="5c4c3-250">é</span><span class="sxs-lookup"><span data-stu-id="5c4c3-250">comes</span></span>
1. <span data-ttu-id="5c4c3-251">uma</span><span class="sxs-lookup"><span data-stu-id="5c4c3-251">an</span></span>
1. <span data-ttu-id="5c4c3-252">lista</span><span class="sxs-lookup"><span data-stu-id="5c4c3-252">embedded</span></span>
    1. <span data-ttu-id="5c4c3-253">Senhorita Costa</span><span class="sxs-lookup"><span data-stu-id="5c4c3-253">Miss Scarlett</span></span>
    1. <span data-ttu-id="5c4c3-254">Professor Mendes</span><span class="sxs-lookup"><span data-stu-id="5c4c3-254">Professor Plum</span></span>
1. <span data-ttu-id="5c4c3-255">ordered</span><span class="sxs-lookup"><span data-stu-id="5c4c3-255">ordered</span></span>
1. <span data-ttu-id="5c4c3-256">lista</span><span class="sxs-lookup"><span data-stu-id="5c4c3-256">list</span></span>

### <a name="unordered-lists"></a><span data-ttu-id="5c4c3-257">Listas não ordenadas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-257">Unordered Lists</span></span>

- <span data-ttu-id="5c4c3-258">Este</span><span class="sxs-lookup"><span data-stu-id="5c4c3-258">This</span></span>
- <span data-ttu-id="5c4c3-259">is</span><span class="sxs-lookup"><span data-stu-id="5c4c3-259">is</span></span>
- <span data-ttu-id="5c4c3-260">a</span><span class="sxs-lookup"><span data-stu-id="5c4c3-260">a</span></span>
- <span data-ttu-id="5c4c3-261">com marcadores</span><span class="sxs-lookup"><span data-stu-id="5c4c3-261">bulleted</span></span>
- <span data-ttu-id="5c4c3-262">lista</span><span class="sxs-lookup"><span data-stu-id="5c4c3-262">list</span></span>

#### <a name="unordered-list-with-an-embedded-list"></a><span data-ttu-id="5c4c3-263">Lista não ordenada com uma lista inserida</span><span class="sxs-lookup"><span data-stu-id="5c4c3-263">Unordered list with an embedded list</span></span>

- <span data-ttu-id="5c4c3-264">Este</span><span class="sxs-lookup"><span data-stu-id="5c4c3-264">This</span></span>
- <span data-ttu-id="5c4c3-265">com marcadores</span><span class="sxs-lookup"><span data-stu-id="5c4c3-265">bulleted</span></span>
- <span data-ttu-id="5c4c3-266">lista</span><span class="sxs-lookup"><span data-stu-id="5c4c3-266">list</span></span>
  - <span data-ttu-id="5c4c3-267">Sra. Pereira</span><span class="sxs-lookup"><span data-stu-id="5c4c3-267">Mrs. Peacock</span></span>
  - <span data-ttu-id="5c4c3-268">Sr. Martins</span><span class="sxs-lookup"><span data-stu-id="5c4c3-268">Mr. Green</span></span>
- <span data-ttu-id="5c4c3-269">contém</span><span class="sxs-lookup"><span data-stu-id="5c4c3-269">contains</span></span>
- <span data-ttu-id="5c4c3-270">outras</span><span class="sxs-lookup"><span data-stu-id="5c4c3-270">other</span></span>
  1. <span data-ttu-id="5c4c3-271">Coronel Teixeira</span><span class="sxs-lookup"><span data-stu-id="5c4c3-271">Colonel Mustard</span></span>
  1. <span data-ttu-id="5c4c3-272">Sra. Barbosa</span><span class="sxs-lookup"><span data-stu-id="5c4c3-272">Mrs. White</span></span>
- <span data-ttu-id="5c4c3-273">listas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-273">lists</span></span>

## <a name="horizontal-rule"></a><span data-ttu-id="5c4c3-274">Régua horizontal</span><span class="sxs-lookup"><span data-stu-id="5c4c3-274">Horizontal rule</span></span>

---

## <a name="tables"></a><span data-ttu-id="5c4c3-275">Tabelas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-275">Tables</span></span>

| <span data-ttu-id="5c4c3-276">Tabelas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-276">Tables</span></span>        | <span data-ttu-id="5c4c3-277">São</span><span class="sxs-lookup"><span data-stu-id="5c4c3-277">Are</span></span>           | <span data-ttu-id="5c4c3-278">Legais</span><span class="sxs-lookup"><span data-stu-id="5c4c3-278">Cool</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="5c4c3-279">A coluna 3 está</span><span class="sxs-lookup"><span data-stu-id="5c4c3-279">col 3 is</span></span>      | <span data-ttu-id="5c4c3-280">alinhada à direita</span><span class="sxs-lookup"><span data-stu-id="5c4c3-280">right-aligned</span></span> | <span data-ttu-id="5c4c3-281">US$ 1.600</span><span class="sxs-lookup"><span data-stu-id="5c4c3-281">$1600</span></span> |
| <span data-ttu-id="5c4c3-282">A coluna 2 está</span><span class="sxs-lookup"><span data-stu-id="5c4c3-282">col 2 is</span></span>      | <span data-ttu-id="5c4c3-283">centralizada</span><span class="sxs-lookup"><span data-stu-id="5c4c3-283">centered</span></span>      |   <span data-ttu-id="5c4c3-284">US$ 12</span><span class="sxs-lookup"><span data-stu-id="5c4c3-284">$12</span></span> |
| <span data-ttu-id="5c4c3-285">A coluna 1 está por padrão</span><span class="sxs-lookup"><span data-stu-id="5c4c3-285">col 1 is default</span></span> | <span data-ttu-id="5c4c3-286">alinhada à esquerda</span><span class="sxs-lookup"><span data-stu-id="5c4c3-286">left-aligned</span></span>     |    <span data-ttu-id="5c4c3-287">US$ 1</span><span class="sxs-lookup"><span data-stu-id="5c4c3-287">$1</span></span> |

<span data-ttu-id="5c4c3-288">É possível usar uma [ferramenta de gerador de tabelas Markdown](https://www.tablesgenerator.com/markdown_tables) para ajudar a criá-las com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-288">You can use a [Markdown table generator tool](https://www.tablesgenerator.com/markdown_tables) to help creating them more easily.</span></span>

## <a name="code"></a><span data-ttu-id="5c4c3-289">Código</span><span class="sxs-lookup"><span data-stu-id="5c4c3-289">Code</span></span>

<span data-ttu-id="5c4c3-290">A melhor maneira de incluir código é incluir snippets de uma amostra funcional.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-290">The best way to include code is to include snippets from a working sample.</span></span> <span data-ttu-id="5c4c3-291">Crie a amostra seguindo as instruções do [guia de contribuição](../CONTRIBUTING.md#contributing-to-samples).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-291">Create your sample following the instructions in the [contributing guide](../CONTRIBUTING.md#contributing-to-samples).</span></span>

<span data-ttu-id="5c4c3-292">Você pode incluir o código usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-292">You can include the code using the following syntax:</span></span>

```markdown
[!code-<language>[<name>](<pathToFile><queryoption><queryoptionvalue>)]
```

- <span data-ttu-id="5c4c3-293">`-<language>` (*opcional*, mas *recomendado*)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-293">`-<language>` (*optional* but *recommended*)</span></span>
  - <span data-ttu-id="5c4c3-294">Linguagem do snippet de código que está sendo referenciado.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-294">Language of the code snippet being referenced.</span></span> <span data-ttu-id="5c4c3-295">Para obter uma lista de valores compatíveis, confira [Linguagens compatíveis](#supported-languages).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-295">For a list of supported values, see [Supported languages](#supported-languages).</span></span>

- <span data-ttu-id="5c4c3-296">`<name>` (*opcional*)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-296">`<name>` (*optional*)</span></span>
  - <span data-ttu-id="5c4c3-297">Nome do snippet de código.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-297">Name for the code snippet.</span></span> <span data-ttu-id="5c4c3-298">Ele não tem nenhum impacto no HTML de saída, mas você pode usá-lo para melhorar a legibilidade da fonte Markdown.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-298">It doesn’t have any impact on the output HTML, but you can use it to improve the readability of your Markdown source.</span></span>

- <span data-ttu-id="5c4c3-299">`<pathToFile>` (*obrigatório*)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-299">`<pathToFile>` (*mandatory*)</span></span>
  - <span data-ttu-id="5c4c3-300">Caminho relativo no sistema de arquivos que indica o arquivo de snippet de código a ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-300">Relative path in the file system that indicates the code snippet file to reference.</span></span>

- <span data-ttu-id="5c4c3-301">`<queryoption>` e `<queryoptionvalue>` (*opcional*)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-301">`<queryoption>` and `<queryoptionvalue>` (*optional*)</span></span>
  - <span data-ttu-id="5c4c3-302">Usados em conjunto para especificar como o código deve ser recuperado do arquivo:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-302">Used together to specify how the code should be retrieved from the file:</span></span>
    - <span data-ttu-id="5c4c3-303">`#`: `#L{startlinenumber}-L{endlinenumber}` (intervalo de linhas) *ou* `#{tagname}` (nome da marca).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-303">`#`:  `#L{startlinenumber}-L{endlinenumber}` (line range) *or* `#{tagname}` (tag name).</span></span>
    <span data-ttu-id="5c4c3-304">Não incentivamos o uso de números de linha, pois são muito frágeis.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-304">We discourage the use of line numbers because they are very brittle.</span></span> <span data-ttu-id="5c4c3-305">O nome da marca é a maneira preferencial de referenciar snippets de código.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-305">Tag name is the preferred way of referencing code snippets.</span></span>
    - <span data-ttu-id="5c4c3-306">`range`: `?range=1,3-5` Um intervalo de linhas.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-306">`range`: `?range=1,3-5` A range of lines.</span></span> <span data-ttu-id="5c4c3-307">Esse exemplo inclui as linhas 1, 3, 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-307">This example includes lines 1, 3, 4, and 5.</span></span>
    - <span data-ttu-id="5c4c3-308">`dedent`: `?dedent=8` Remove o recuo das linhas por um número de espaços – nesse caso, 8.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-308">`dedent`: `?dedent=8` Dedents the lines by a number of spaces--in this case, 8.</span></span> <span data-ttu-id="5c4c3-309">Isso pode ser combinado com o `range` e outras opções de consulta que selecionam um subconjunto das linhas de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-309">This can be combined with the `range` and other query options that select a subset of the lines of a file.</span></span>
    - <span data-ttu-id="5c4c3-310">`outdent`: `?outdent=8` Inverte o recuo das linhas por um número de espaços – nesse caso, 8.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-310">`outdent`: `?outdent=8` Reverses the indent of the lines by a number of spaces--in this case, 8.</span></span> <span data-ttu-id="5c4c3-311">Isso pode ser combinado com `range` e outras opções de consulta que selecionam um subconjunto das linhas de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-311">This can be combined with `range` and other query options that select a subset of the lines of a file.</span></span>

<span data-ttu-id="5c4c3-312">Recomendamos o uso da opção de nome da marca sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-312">We recommend using the tag name option whenever possible.</span></span> <span data-ttu-id="5c4c3-313">O nome da marca é o nome de uma região ou de um comentário de código no formato `Snippettagname` presente no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-313">The tag name is the name of a region or of a code comment in the format of `Snippettagname` present in the source code.</span></span> <span data-ttu-id="5c4c3-314">O seguinte exemplo mostra como referenciar o nome da marca `1`:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-314">The following example shows how to refer to the tag name `1`:</span></span>

```markdown
[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]
```

<span data-ttu-id="5c4c3-315">Você poderá ver como as marcas de snippet são estruturadas neste [arquivo de origem](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-315">And you can see how the snippet tags are structured in [this source file](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs).</span></span> <span data-ttu-id="5c4c3-316">Para obter detalhes sobre a representação de nome da marca nos arquivos de origem do snippet de código por linguagem, confira as [diretrizes do DocFX](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-316">For details about tag name representation in code snippet source files by language, see the [DocFX guidelines](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file).</span></span>

<span data-ttu-id="5c4c3-317">A inclusão de snippets de programas completos garante que todo o código é executado por meio de nosso sistema de CI (Integração Contínua).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-317">Including snippets from full programs ensures that all code runs through our Continuous Integration (CI) system.</span></span> <span data-ttu-id="5c4c3-318">No entanto, se você precisar mostrar algo que causa erros de tempo de compilação ou de execução, será possível usar blocos de código embutidos.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-318">However, if you need to show something that causes compile time or runtime errors, you can use inline code blocks.</span></span>

### <a name="inline-code-blocks-with-language-identifier"></a><span data-ttu-id="5c4c3-319">Blocos de código embutidos com identificador de linguagem</span><span class="sxs-lookup"><span data-stu-id="5c4c3-319">Inline code blocks with language identifier</span></span>

<span data-ttu-id="5c4c3-320">Use três backticks (\`\`\`) + uma ID de idioma para aplicar a codificação de cores específico a um idioma para um bloco de código.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-320">Use three backticks (\`\`\`) + a language ID to apply language-specific color coding to a code block.</span></span> <span data-ttu-id="5c4c3-321">Veja a seguir a lista de idiomais compatíveis que mostram o rótulo de markdown para cada ID de idioma.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-321">Here is the list of supported languages showing the markdown label for each language ID.</span></span>

#### <a name="supported-languages"></a><span data-ttu-id="5c4c3-322">Idiomas com suporte</span><span class="sxs-lookup"><span data-stu-id="5c4c3-322">Supported languages</span></span>

|<span data-ttu-id="5c4c3-323">Nome</span><span class="sxs-lookup"><span data-stu-id="5c4c3-323">Name</span></span>|<span data-ttu-id="5c4c3-324">Rótulo de markdown</span><span class="sxs-lookup"><span data-stu-id="5c4c3-324">Markdown label</span></span>|
|-----|-------|
|<span data-ttu-id="5c4c3-325">ASP.NET com C#</span><span class="sxs-lookup"><span data-stu-id="5c4c3-325">ASP.NET with C#</span></span>|<span data-ttu-id="5c4c3-326">aspx-csharp</span><span class="sxs-lookup"><span data-stu-id="5c4c3-326">aspx-csharp</span></span>|
|<span data-ttu-id="5c4c3-327">ASP.NET com VB</span><span class="sxs-lookup"><span data-stu-id="5c4c3-327">ASP.NET with VB</span></span>|<span data-ttu-id="5c4c3-328">aspx-vb</span><span class="sxs-lookup"><span data-stu-id="5c4c3-328">aspx-vb</span></span>|
|<span data-ttu-id="5c4c3-329">CLI do Azure</span><span class="sxs-lookup"><span data-stu-id="5c4c3-329">Azure CLI</span></span>|<span data-ttu-id="5c4c3-330">azurecli</span><span class="sxs-lookup"><span data-stu-id="5c4c3-330">azurecli</span></span>|
|<span data-ttu-id="5c4c3-331">AzCopy</span><span class="sxs-lookup"><span data-stu-id="5c4c3-331">AzCopy</span></span>|<span data-ttu-id="5c4c3-332">azcopy</span><span class="sxs-lookup"><span data-stu-id="5c4c3-332">azcopy</span></span>|
|<span data-ttu-id="5c4c3-333">C++</span><span class="sxs-lookup"><span data-stu-id="5c4c3-333">C++</span></span>|<span data-ttu-id="5c4c3-334">cpp</span><span class="sxs-lookup"><span data-stu-id="5c4c3-334">cpp</span></span>|
|<span data-ttu-id="5c4c3-335">C#</span><span class="sxs-lookup"><span data-stu-id="5c4c3-335">C#</span></span>|<span data-ttu-id="5c4c3-336">csharp</span><span class="sxs-lookup"><span data-stu-id="5c4c3-336">csharp</span></span>|
|<span data-ttu-id="5c4c3-337">C# no navegador</span><span class="sxs-lookup"><span data-stu-id="5c4c3-337">C# in browser</span></span>|<span data-ttu-id="5c4c3-338">csharp-interactive</span><span class="sxs-lookup"><span data-stu-id="5c4c3-338">csharp-interactive</span></span>|
|<span data-ttu-id="5c4c3-339">Console</span><span class="sxs-lookup"><span data-stu-id="5c4c3-339">Console</span></span>|<span data-ttu-id="5c4c3-340">console</span><span class="sxs-lookup"><span data-stu-id="5c4c3-340">console</span></span>|
|<span data-ttu-id="5c4c3-341">F#</span><span class="sxs-lookup"><span data-stu-id="5c4c3-341">F#</span></span>|<span data-ttu-id="5c4c3-342">fsharp</span><span class="sxs-lookup"><span data-stu-id="5c4c3-342">fsharp</span></span>|
|<span data-ttu-id="5c4c3-343">Java</span><span class="sxs-lookup"><span data-stu-id="5c4c3-343">Java</span></span>|<span data-ttu-id="5c4c3-344">java</span><span class="sxs-lookup"><span data-stu-id="5c4c3-344">java</span></span>|
|<span data-ttu-id="5c4c3-345">JavaScript</span><span class="sxs-lookup"><span data-stu-id="5c4c3-345">JavaScript</span></span>|<span data-ttu-id="5c4c3-346">javascript</span><span class="sxs-lookup"><span data-stu-id="5c4c3-346">javascript</span></span>|
|<span data-ttu-id="5c4c3-347">JSON</span><span class="sxs-lookup"><span data-stu-id="5c4c3-347">JSON</span></span>|<span data-ttu-id="5c4c3-348">json</span><span class="sxs-lookup"><span data-stu-id="5c4c3-348">json</span></span>|
|<span data-ttu-id="5c4c3-349">NodeJS</span><span class="sxs-lookup"><span data-stu-id="5c4c3-349">NodeJS</span></span>|<span data-ttu-id="5c4c3-350">nodejs</span><span class="sxs-lookup"><span data-stu-id="5c4c3-350">nodejs</span></span>|
|<span data-ttu-id="5c4c3-351">Objective-C</span><span class="sxs-lookup"><span data-stu-id="5c4c3-351">Objective-C</span></span>|<span data-ttu-id="5c4c3-352">objc</span><span class="sxs-lookup"><span data-stu-id="5c4c3-352">objc</span></span>|
|<span data-ttu-id="5c4c3-353">PHP</span><span class="sxs-lookup"><span data-stu-id="5c4c3-353">PHP</span></span>|<span data-ttu-id="5c4c3-354">php</span><span class="sxs-lookup"><span data-stu-id="5c4c3-354">php</span></span>|
|<span data-ttu-id="5c4c3-355">PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c4c3-355">PowerShell</span></span>|<span data-ttu-id="5c4c3-356">powershell</span><span class="sxs-lookup"><span data-stu-id="5c4c3-356">powershell</span></span>|
|<span data-ttu-id="5c4c3-357">Python</span><span class="sxs-lookup"><span data-stu-id="5c4c3-357">Python</span></span>|<span data-ttu-id="5c4c3-358">python</span><span class="sxs-lookup"><span data-stu-id="5c4c3-358">python</span></span>|
|<span data-ttu-id="5c4c3-359">Ruby</span><span class="sxs-lookup"><span data-stu-id="5c4c3-359">Ruby</span></span>|<span data-ttu-id="5c4c3-360">ruby</span><span class="sxs-lookup"><span data-stu-id="5c4c3-360">ruby</span></span>|
|<span data-ttu-id="5c4c3-361">SQL</span><span class="sxs-lookup"><span data-stu-id="5c4c3-361">SQL</span></span>|<span data-ttu-id="5c4c3-362">sql</span><span class="sxs-lookup"><span data-stu-id="5c4c3-362">sql</span></span>|
|<span data-ttu-id="5c4c3-363">Swift</span><span class="sxs-lookup"><span data-stu-id="5c4c3-363">Swift</span></span>|<span data-ttu-id="5c4c3-364">swift</span><span class="sxs-lookup"><span data-stu-id="5c4c3-364">swift</span></span>|
|<span data-ttu-id="5c4c3-365">VB</span><span class="sxs-lookup"><span data-stu-id="5c4c3-365">VB</span></span>|<span data-ttu-id="5c4c3-366">vb</span><span class="sxs-lookup"><span data-stu-id="5c4c3-366">vb</span></span>|
|<span data-ttu-id="5c4c3-367">XAML</span><span class="sxs-lookup"><span data-stu-id="5c4c3-367">XAML</span></span>|<span data-ttu-id="5c4c3-368">xaml</span><span class="sxs-lookup"><span data-stu-id="5c4c3-368">xaml</span></span>|
|<span data-ttu-id="5c4c3-369">XML</span><span class="sxs-lookup"><span data-stu-id="5c4c3-369">XML</span></span>|<span data-ttu-id="5c4c3-370">xml</span><span class="sxs-lookup"><span data-stu-id="5c4c3-370">xml</span></span>|

<span data-ttu-id="5c4c3-371">O nome `csharp-interactive` especifica a linguagem C# e a capacidade de executar as amostras no navegador.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-371">The `csharp-interactive` name specifies the C# language, and the ability to run the samples from the browser.</span></span> <span data-ttu-id="5c4c3-372">Esses snippets são compilados e executados em um contêiner do Docker, e os resultados dessa execução do programa são exibidos na janela do navegador do usuário.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-372">These snippets are compiled and executed in a Docker container, and the results of that program execution are displayed in the user's browser window.</span></span>

<span data-ttu-id="5c4c3-373">Veja a seguir exemplos de blocos de código usando as IDs de linguagem para o C# (\`\`\`csharp), o Python (\`\`\`python) e o PowerShell (\`\`\`powershell).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-373">The following are examples of code blocks using the language IDs for C# (\`\`\`csharp), Python (\`\`\`python), and PowerShell (\`\`\`powershell).</span></span>

##### <a name="c9839"></a><span data-ttu-id="5c4c3-374">C&#9839;</span><span class="sxs-lookup"><span data-stu-id="5c4c3-374">C&#9839;</span></span>

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

#### <a name="python"></a><span data-ttu-id="5c4c3-375">Python</span><span class="sxs-lookup"><span data-stu-id="5c4c3-375">Python</span></span>

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a><span data-ttu-id="5c4c3-376">PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c4c3-376">PowerShell</span></span>

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a><span data-ttu-id="5c4c3-377">Bloco de código genérico</span><span class="sxs-lookup"><span data-stu-id="5c4c3-377">Generic code block</span></span>

<span data-ttu-id="5c4c3-378">Use três backticks (&#96;&#96;&#96;) para a codificação de bloco de código genérico.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-378">Use three backticks (&#96;&#96;&#96;) for generic code block coding.</span></span>

> <span data-ttu-id="5c4c3-379">A abordagem recomendada é usar blocos de código com identificadores de linguagem, conforme explicado na seção anterior, para garantir o realce de sintaxe apropriado no site da documentação.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-379">The recommended approach is to use code blocks with language identifiers as explained in the previous section to ensure the proper syntax highlighting in the documentation site.</span></span> <span data-ttu-id="5c4c3-380">Use blocos de código genérico somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-380">Use generic code blocks only when necessary.</span></span>

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

## <a name="blockquotes"></a><span data-ttu-id="5c4c3-381">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="5c4c3-381">Blockquotes</span></span>

> <span data-ttu-id="5c4c3-382">A seca agora se estende para dez milhões de anos e o reino dos terríveis lagartos desde então foi extinto.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-382">The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended.</span></span> <span data-ttu-id="5c4c3-383">Aqui no Equador, no continente em que um dia seria conhecido como África, a luta pela existência atingiu um novo auge de ferocidade e o vencedor ainda não foi avistado.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-383">Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight.</span></span> <span data-ttu-id="5c4c3-384">Nesta terra árida e desidratada, apenas as espécies pequenas, ágeis ou ferozes poderiam prosperar ou mesmo ter a esperança de sobreviver.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-384">In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.</span></span>

## <a name="images"></a><span data-ttu-id="5c4c3-385">Imagens</span><span class="sxs-lookup"><span data-stu-id="5c4c3-385">Images</span></span>

### <a name="static-image-or-animated-gif"></a><span data-ttu-id="5c4c3-386">Imagem estática ou GIF animado</span><span class="sxs-lookup"><span data-stu-id="5c4c3-386">Static Image or Animated gif</span></span>

```markdown
![this is the alt text](../images/Logo_DotNet.png)
```

![este é o texto Alt](../images/Logo_DotNet.png)

### <a name="linked-image"></a><span data-ttu-id="5c4c3-388">Imagem vinculada</span><span class="sxs-lookup"><span data-stu-id="5c4c3-388">Linked Image</span></span>

```markdown
[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)
```

<span data-ttu-id="5c4c3-389">[![texto Alt da imagem vinculada](../images/Logo_DotNet.png)](https://dot.net)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-389">[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)</span></span>

## <a name="videos"></a><span data-ttu-id="5c4c3-390">Vídeos</span><span class="sxs-lookup"><span data-stu-id="5c4c3-390">Videos</span></span>

<span data-ttu-id="5c4c3-391">No momento, é possível inserir vídeos do Channel 9 e do YouTube com a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-391">Currently, you can embed both Channel 9 and YouTube videos with the following syntax:</span></span>

### <a name="channel-9"></a><span data-ttu-id="5c4c3-392">Channel 9</span><span class="sxs-lookup"><span data-stu-id="5c4c3-392">Channel 9</span></span>

```markdown
> [!VIDEO <channel9_video_link>]
```

<span data-ttu-id="5c4c3-393">Para obter a URL correta do vídeo, selecione a guia **Inserir** abaixo do quadro de vídeo e copie a URL do elemento `<iframe>`.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-393">To get the video's correct URL, select the **Embed** tab below the video frame, and copy the URL from the `<iframe>` element.</span></span> <span data-ttu-id="5c4c3-394">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-394">For example:</span></span>

```markdown
> [!VIDEO https://channel9.msdn.com/Blogs/dotnet/NET-Core-20-Released/player]
```

### <a name="youtube"></a><span data-ttu-id="5c4c3-395">YouTube</span><span class="sxs-lookup"><span data-stu-id="5c4c3-395">YouTube</span></span>

<span data-ttu-id="5c4c3-396">Para obter a URL correta do vídeo, clique com o botão direito do mouse no vídeo, selecione **Copiar Código de Inserção** e copie a URL do elemento `<iframe>`.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-396">To get the video's correct URL, right-click on the video, select **Copy Embed Code**, and copy the URL from the `<iframe>` element.</span></span>

```markdown
> [!VIDEO <youtube_video_link>]
```

<span data-ttu-id="5c4c3-397">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5c4c3-397">For example:</span></span>

```markdown
> [!VIDEO https://www.youtube.com/embed/Q2mMbjw6cLA]
```

## <a name="docsmicrosoft-extensions"></a><span data-ttu-id="5c4c3-398">Extensões docs.microsoft</span><span class="sxs-lookup"><span data-stu-id="5c4c3-398">docs.microsoft extensions</span></span>

<span data-ttu-id="5c4c3-399">O docs.microsoft fornece algumas extensões adicionais para o GitHub Flavored Markdown.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-399">docs.microsoft provides a few additional extensions to GitHub Flavored Markdown.</span></span>

### <a name="alerts"></a><span data-ttu-id="5c4c3-400">Alertas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-400">Alerts</span></span>

<span data-ttu-id="5c4c3-401">É importante usar os estilos de alerta a seguir para que eles sejam renderizados com o estilo adequado no site da documentação.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-401">It's important to use the following alert styles so they render with the proper style in the documentation site.</span></span> <span data-ttu-id="5c4c3-402">No entanto, o mecanismo de renderização no GitHub não os diferencia.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-402">However, the rendering engine on GitHub doesn't diferentiate them.</span></span>

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

<span data-ttu-id="5c4c3-403">Eles serão renderizados assim: ![Estilos de alerta](../images/alerts.png)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-403">And they'll render like this: ![Alert styles](../images/alerts.png)</span></span>

### <a name="includes"></a><span data-ttu-id="5c4c3-404">Inclui</span><span class="sxs-lookup"><span data-stu-id="5c4c3-404">Includes</span></span>

<span data-ttu-id="5c4c3-405">Você pode inserir o Markdown de um arquivo em outro usando uma inclusão.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-405">You can embed the Markdown of one file into another using an include.</span></span>

[!INCLUDE[sample include file](../includes/sampleinclude.md)]

### <a name="checked-lists"></a><span data-ttu-id="5c4c3-406">Listas selecionadas</span><span class="sxs-lookup"><span data-stu-id="5c4c3-406">Checked lists</span></span>

<span data-ttu-id="5c4c3-407">Um estilo personalizado está disponível para listas.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-407">A custom style is available for lists.</span></span> <span data-ttu-id="5c4c3-408">Você pode renderizar listas com marcas de seleção verdes.</span><span class="sxs-lookup"><span data-stu-id="5c4c3-408">You can render lists with green check marks.</span></span>

> [!div class="checklist"]
> - <span data-ttu-id="5c4c3-409">Como criar um aplicativo do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5c4c3-409">How to create a .NET Core app</span></span>
> - <span data-ttu-id="5c4c3-410">Como adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="5c4c3-410">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="5c4c3-411">Como editar o MyApp.csproj para adicionar dependências</span><span class="sxs-lookup"><span data-stu-id="5c4c3-411">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="5c4c3-412">Como adicionar uma classe e um XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="5c4c3-412">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="5c4c3-413">Como compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="5c4c3-413">How to build and run the application</span></span>

<span data-ttu-id="5c4c3-414">Veja um exemplo de listas selecionadas em ação na [documentação do .NET Core](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-414">You can see an example of checked lists in action in the [.NET Core docs](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator).</span></span>

### <a name="buttons"></a><span data-ttu-id="5c4c3-415">Botões</span><span class="sxs-lookup"><span data-stu-id="5c4c3-415">Buttons</span></span>

> [!div class="button"]
> [<span data-ttu-id="5c4c3-416">links de botão</span><span class="sxs-lookup"><span data-stu-id="5c4c3-416">button links</span></span>](../docs/core/index.md)

<span data-ttu-id="5c4c3-417">Veja um exemplo de botões em ação na [documentação do Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-417">You can see an example of buttons in action in the [Visual Studio docs](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio).</span></span>

### <a name="selectors"></a><span data-ttu-id="5c4c3-418">Seletores</span><span class="sxs-lookup"><span data-stu-id="5c4c3-418">Selectors</span></span>

> [!div class="op_single_selector"]
- [<span data-ttu-id="5c4c3-419">macOS</span><span class="sxs-lookup"><span data-stu-id="5c4c3-419">macOS</span></span>](../docs/core/tutorials/using-on-macos.md)
- [<span data-ttu-id="5c4c3-420">Windows</span><span class="sxs-lookup"><span data-stu-id="5c4c3-420">Windows</span></span>](../docs/core/tutorials/with-visual-studio.md)

<span data-ttu-id="5c4c3-421">Veja um exemplo de seletores em ação na [documentação do Azure](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-421">You can see an example of selectors in action at the [Azure docs](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic).</span></span>

### <a name="step-by-steps"></a><span data-ttu-id="5c4c3-422">Passo a passo</span><span class="sxs-lookup"><span data-stu-id="5c4c3-422">Step-By-Steps</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5c4c3-423">[Anterior](../docs/csharp/expression-trees-interpreting.md)
>[Próximo](../docs/csharp/expression-trees-translating.md)</span><span class="sxs-lookup"><span data-stu-id="5c4c3-423">[Previous](../docs/csharp/expression-trees-interpreting.md)
[Next](../docs/csharp/expression-trees-translating.md)</span></span>

<span data-ttu-id="5c4c3-424">Veja um exemplo de passo a passo em ação no [Guia do C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure).</span><span class="sxs-lookup"><span data-stu-id="5c4c3-424">You can see an example of step-by-steps in action at the [C# Guide](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure).</span></span>
