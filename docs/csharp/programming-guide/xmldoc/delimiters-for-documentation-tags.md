---
title: Delimitadores para marcas de documentação – guia de programação em C#
description: Saiba mais sobre os delimitadores para marcas de documentação. Os delimitadores indicam ao compilador em que um comentário de documentação começa e termina.
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 3191e32b0ff2dbde004abaab0b699cd61fcbb150
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381977"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="c17d7-104">Delimitadores para marcas de documentação (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="c17d7-104">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="c17d7-105">O uso de comentários do documento XML requer delimitadores, que indicam ao compilador em que um comentário de documentação começa e termina.</span><span class="sxs-lookup"><span data-stu-id="c17d7-105">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="c17d7-106">Você pode usar os seguintes tipos de delimitadores com as marcas de documentação XML:</span><span class="sxs-lookup"><span data-stu-id="c17d7-106">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="c17d7-107">O delimitador de linha única.</span><span class="sxs-lookup"><span data-stu-id="c17d7-107">Single-line delimiter.</span></span> <span data-ttu-id="c17d7-108">Esse é o formulário mostrado nos exemplos de documentação e usado pelos modelos de projeto do C#.</span><span class="sxs-lookup"><span data-stu-id="c17d7-108">This is the form that is shown in documentation examples and used by the C# project templates.</span></span> <span data-ttu-id="c17d7-109">Se houver um caractere de espaço em branco depois do delimitador, esse caractere não estará incluído na saída XML.</span><span class="sxs-lookup"><span data-stu-id="c17d7-109">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c17d7-110">O IDE (ambiente de desenvolvimento integrado) do Visual Studio insere automaticamente as `<summary>` `</summary>` marcas e e move o cursor dentro dessas marcas depois que você digita o `///` delimitador no editor de código.</span><span class="sxs-lookup"><span data-stu-id="c17d7-110">The Visual Studio integrated development environment (IDE) automatically inserts the `<summary>` and `</summary>` tags and moves your cursor within these tags after you type the `///` delimiter in the code editor.</span></span> <span data-ttu-id="c17d7-111">Você pode ativar ou desativar esse recurso na [caixa de diálogo Opções](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="c17d7-111">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="c17d7-112">Delimitadores multilinha.</span><span class="sxs-lookup"><span data-stu-id="c17d7-112">Multiline delimiters.</span></span>

  <span data-ttu-id="c17d7-113">Há algumas regras de formatação a serem seguidas ao usar os `/** */` delimitadores:</span><span class="sxs-lookup"><span data-stu-id="c17d7-113">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="c17d7-114">Na linha que contém o delimitador `/**`, se o restante da linha for um espaço em branco, a linha não será processada para comentários.</span><span class="sxs-lookup"><span data-stu-id="c17d7-114">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="c17d7-115">Se o primeiro caractere após o delimitador `/**` for um espaço em branco, esse caractere de espaço em branco será ignorado e o restante da linha será processado.</span><span class="sxs-lookup"><span data-stu-id="c17d7-115">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="c17d7-116">Caso contrário, todo o texto da linha após o delimitador `/**` é processado como parte do comentário.</span><span class="sxs-lookup"><span data-stu-id="c17d7-116">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="c17d7-117">Na linha que contém o delimitador `*/`, se houver apenas espaços em branco até o delimitador `*/`, essa linha será ignorada.</span><span class="sxs-lookup"><span data-stu-id="c17d7-117">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="c17d7-118">Caso contrário, o texto na linha até o `*/` delimitador será processado como parte do comentário.</span><span class="sxs-lookup"><span data-stu-id="c17d7-118">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment.</span></span>
  
  - <span data-ttu-id="c17d7-119">Para as linhas após a que começa com o delimitador `/**`, o compilador procura um padrão comum no início de cada linha.</span><span class="sxs-lookup"><span data-stu-id="c17d7-119">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="c17d7-120">O padrão pode consistir de espaço em branco opcional e um asterisco (`*`), seguido de mais espaço em branco opcional.</span><span class="sxs-lookup"><span data-stu-id="c17d7-120">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="c17d7-121">Se o compilador encontrar um padrão comum no início de cada linha que não começa com o delimitador `/**` ou com o delimitador `*/`, ele ignorará esse padrão para cada linha.</span><span class="sxs-lookup"><span data-stu-id="c17d7-121">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="c17d7-122">Os exemplos a seguir ilustram essas regras.</span><span class="sxs-lookup"><span data-stu-id="c17d7-122">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="c17d7-123">A única parte do comentário a seguir que é processada é a linha que começa com `<summary>` .</span><span class="sxs-lookup"><span data-stu-id="c17d7-123">The only part of the following comment that's processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="c17d7-124">Os três formatos de marca produzem os mesmos comentários.</span><span class="sxs-lookup"><span data-stu-id="c17d7-124">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="c17d7-125">O compilador identifica um padrão comum de " \* " no início da segunda e terceira linhas.</span><span class="sxs-lookup"><span data-stu-id="c17d7-125">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="c17d7-126">O padrão não é incluído na saída.</span><span class="sxs-lookup"><span data-stu-id="c17d7-126">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="c17d7-127">O compilador não encontra nenhum padrão comum no seguinte comentário porque o segundo caractere na terceira linha não é um asterisco.</span><span class="sxs-lookup"><span data-stu-id="c17d7-127">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="c17d7-128">Portanto, todo o texto na segunda e terceira linhas é processado como parte do comentário.</span><span class="sxs-lookup"><span data-stu-id="c17d7-128">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="c17d7-129">O compilador não encontra nenhum padrão no seguinte comentário por dois motivos.</span><span class="sxs-lookup"><span data-stu-id="c17d7-129">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="c17d7-130">Primeiro, o número de espaços antes do asterisco não é consistente.</span><span class="sxs-lookup"><span data-stu-id="c17d7-130">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="c17d7-131">Segundo, a quinta linha começa com uma guia, que não coincide com espaços.</span><span class="sxs-lookup"><span data-stu-id="c17d7-131">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="c17d7-132">Portanto, todo o texto das linhas de dois a cinco é processado como parte do comentário.</span><span class="sxs-lookup"><span data-stu-id="c17d7-132">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a><span data-ttu-id="c17d7-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="c17d7-133">See also</span></span>

- [<span data-ttu-id="c17d7-134">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="c17d7-134">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c17d7-135">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="c17d7-135">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="c17d7-136">-Doc (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="c17d7-136">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
