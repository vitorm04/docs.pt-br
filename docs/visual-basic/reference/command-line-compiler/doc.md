---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 13005eb55b430f6ff9b3a6408582a02e53838742
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969202"
---
# <a name="-doc"></a><span data-ttu-id="ba2d4-102">-doc</span><span class="sxs-lookup"><span data-stu-id="ba2d4-102">-doc</span></span>
<span data-ttu-id="ba2d4-103">Processa comentários de documentação para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba2d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba2d4-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba2d4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ba2d4-105">Arguments</span></span>  
  
|<span data-ttu-id="ba2d4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="ba2d4-106">Term</span></span>|<span data-ttu-id="ba2d4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="ba2d4-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="ba2d4-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ba2d4-108">`+` &#124; `-`</span></span>|<span data-ttu-id="ba2d4-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-109">Optional.</span></span> <span data-ttu-id="ba2d4-110">Especificar +, ou apenas `-doc`, faz com que o compilador gere informações sobre a documentação e as coloque em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="ba2d4-111">Especificar `-` é equivalente a não especificar `-doc`, fazendo com que nenhuma informação de documentação seja criada.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="ba2d4-112">Necessário se `-doc:` for usado.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="ba2d4-113">Especifica o arquivo XML de saída, que é preenchido com os comentários dos arquivos de código-fonte da compilação.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="ba2d4-114">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas (" ").</span><span class="sxs-lookup"><span data-stu-id="ba2d4-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba2d4-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba2d4-115">Remarks</span></span>  
 <span data-ttu-id="ba2d4-116">A opção `-doc` controla se o compilador gera um arquivo XML contendo os comentários de documentação.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="ba2d4-117">Se você usar a sintaxe `-doc:file`, o parâmetro `file` especifica o nome do arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="ba2d4-118">Se você usar `-doc` ou `-doc+`, o compilador pega o nome do arquivo XML do arquivo executável ou da biblioteca que o compilador está criando.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="ba2d4-119">Se você usar `-doc-` ou não especificar a opção `-doc`, o compilador não criará um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="ba2d4-120">Nos arquivos de código-fonte, os comentários de documentação podem preceder as seguintes definições:</span><span class="sxs-lookup"><span data-stu-id="ba2d4-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="ba2d4-121">Tipos definidos pelo usuário, como uma [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ba2d4-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="ba2d4-122">Membros, como um campo, [evento](../../../visual-basic/language-reference/statements/event-statement.md), [propriedade](../../../visual-basic/language-reference/statements/property-statement.md), [função](../../../visual-basic/language-reference/statements/function-statement.md) ou [sub-rotina](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ba2d4-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="ba2d4-123">Para usar o arquivo XML gerado com o recurso [IntelliSense](/visualstudio/ide/using-intellisense) do Visual Studio, deixe o nome do arquivo XML ser o mesmo que o assembly para o qual você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-123">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="ba2d4-124">Certifique-se de que o arquivo XML esteja no mesmo diretório que o assembly de modo que, ao referenciar o assembly no projeto do Visual Studio, o arquivo .xml também seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="ba2d4-125">Os arquivos de documentação XML não são necessários para o IntelliSense funcionar com o código dentro do projeto ou em projetos referenciados por um projeto.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="ba2d4-126">A menos que você compile com `/target:module`, o arquivo XML contém as marcações `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="ba2d4-127">Essas marcações especificam o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="ba2d4-128">Veja [Marcas de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md) para descobrir as maneiras de gerar documentação de comentários em seu código.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="ba2d4-129">Para configurar -doc no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ba2d4-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ba2d4-130">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ba2d4-131">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ba2d4-132">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ba2d4-133">3.  Defina o valor na caixa **Gerar arquivo de documentação XML**.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ba2d4-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba2d4-134">Example</span></span>  
 <span data-ttu-id="ba2d4-135">Veja [Como documentar o código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="ba2d4-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2d4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba2d4-136">See also</span></span>

- [<span data-ttu-id="ba2d4-137">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba2d4-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ba2d4-138">Documentando o Código com XML</span><span class="sxs-lookup"><span data-stu-id="ba2d4-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
