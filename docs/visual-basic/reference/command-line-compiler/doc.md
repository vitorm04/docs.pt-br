---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: a818fd46bd93682f0bede1d22b8cbc2ca6467a40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716736"
---
# <a name="-doc"></a><span data-ttu-id="1144c-102">-doc</span><span class="sxs-lookup"><span data-stu-id="1144c-102">-doc</span></span>
<span data-ttu-id="1144c-103">Processa comentários de documentação para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="1144c-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1144c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1144c-104">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="1144c-105">ou o</span><span class="sxs-lookup"><span data-stu-id="1144c-105">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="1144c-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="1144c-106">Arguments</span></span>  
  
|<span data-ttu-id="1144c-107">Termo</span><span class="sxs-lookup"><span data-stu-id="1144c-107">Term</span></span>|<span data-ttu-id="1144c-108">Definição</span><span class="sxs-lookup"><span data-stu-id="1144c-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1144c-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1144c-109">`+` &#124; `-`</span></span>|<span data-ttu-id="1144c-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1144c-110">Optional.</span></span> <span data-ttu-id="1144c-111">Especificar +, ou apenas `-doc`, faz com que o compilador gere informações sobre a documentação e as coloque em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="1144c-111">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="1144c-112">Especificar `-` é equivalente a não especificar `-doc`, fazendo com que nenhuma informação de documentação seja criada.</span><span class="sxs-lookup"><span data-stu-id="1144c-112">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="1144c-113">Necessário se `-doc:` for usado.</span><span class="sxs-lookup"><span data-stu-id="1144c-113">Required if `-doc:` is used.</span></span> <span data-ttu-id="1144c-114">Especifica o arquivo XML de saída, que é preenchido com os comentários dos arquivos de código-fonte da compilação.</span><span class="sxs-lookup"><span data-stu-id="1144c-114">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="1144c-115">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas (" ").</span><span class="sxs-lookup"><span data-stu-id="1144c-115">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1144c-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="1144c-116">Remarks</span></span>  
 <span data-ttu-id="1144c-117">A opção `-doc` controla se o compilador gera um arquivo XML contendo os comentários de documentação.</span><span class="sxs-lookup"><span data-stu-id="1144c-117">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="1144c-118">Se você usar a sintaxe `-doc:file`, o parâmetro `file` especifica o nome do arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="1144c-118">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="1144c-119">Se você usar `-doc` ou `-doc+`, o compilador pega o nome do arquivo XML do arquivo executável ou da biblioteca que o compilador está criando.</span><span class="sxs-lookup"><span data-stu-id="1144c-119">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="1144c-120">Se você usar `-doc-` ou não especificar a opção `-doc`, o compilador não criará um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="1144c-120">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="1144c-121">Nos arquivos de código-fonte, os comentários de documentação podem preceder as seguintes definições:</span><span class="sxs-lookup"><span data-stu-id="1144c-121">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="1144c-122">Tipos definidos pelo usuário, como uma [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="1144c-122">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="1144c-123">Membros, como um campo, [evento](../../../visual-basic/language-reference/statements/event-statement.md), [propriedade](../../../visual-basic/language-reference/statements/property-statement.md), [função](../../../visual-basic/language-reference/statements/function-statement.md) ou [sub-rotina](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1144c-123">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="1144c-124">Para usar o arquivo XML gerado com o recurso [IntelliSense](/visualstudio/ide/using-intellisense) do Visual Studio, deixe o nome do arquivo XML ser o mesmo que o assembly para o qual você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="1144c-124">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="1144c-125">Certifique-se de que o arquivo XML esteja no mesmo diretório que o assembly de modo que, ao referenciar o assembly no projeto do Visual Studio, o arquivo .xml também seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="1144c-125">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="1144c-126">Os arquivos de documentação XML não são necessários para o IntelliSense funcionar com o código dentro do projeto ou em projetos referenciados por um projeto.</span><span class="sxs-lookup"><span data-stu-id="1144c-126">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="1144c-127">A menos que você compile com `-target:module`, o arquivo XML contém as marcações `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="1144c-127">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="1144c-128">Essas marcações especificam o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.</span><span class="sxs-lookup"><span data-stu-id="1144c-128">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="1144c-129">Veja [Marcas de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md) para descobrir as maneiras de gerar documentação de comentários em seu código.</span><span class="sxs-lookup"><span data-stu-id="1144c-129">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="1144c-130">Para configurar -doc no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1144c-130">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1144c-131">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="1144c-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1144c-132">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="1144c-132">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1144c-133">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="1144c-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1144c-134">3. defina o valor na caixa **gerar arquivo de documentação XML** .</span><span class="sxs-lookup"><span data-stu-id="1144c-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1144c-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1144c-135">Example</span></span>  
 <span data-ttu-id="1144c-136">Veja [Como documentar o código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="1144c-136">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1144c-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="1144c-137">See also</span></span>

- [<span data-ttu-id="1144c-138">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1144c-138">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1144c-139">Documentando o código com XML</span><span class="sxs-lookup"><span data-stu-id="1144c-139">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
