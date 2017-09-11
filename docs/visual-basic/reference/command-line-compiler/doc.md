---
title: /doc | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 974c41ba6ba4104a7fe17146390e14ccfbb7a521
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="doc"></a><span data-ttu-id="86c55-102">/doc</span><span class="sxs-lookup"><span data-stu-id="86c55-102">/doc</span></span>
<span data-ttu-id="86c55-103">Processa comentários de documentação para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="86c55-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86c55-104">Syntax</span></span>  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="86c55-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="86c55-105">Arguments</span></span>  
  
|<span data-ttu-id="86c55-106">Termo</span><span class="sxs-lookup"><span data-stu-id="86c55-106">Term</span></span>|<span data-ttu-id="86c55-107">Definição</span><span class="sxs-lookup"><span data-stu-id="86c55-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="86c55-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="86c55-108">`+` &#124; `-`</span></span>|<span data-ttu-id="86c55-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="86c55-109">Optional.</span></span> <span data-ttu-id="86c55-110">Especificar +, ou apenas `/doc`, faz com que o compilador gere informações sobre a documentação e colocá-lo em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="86c55-110">Specifying +, or just `/doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="86c55-111">Especificando `-` é o equivalente de não especificar `/doc`, fazendo com que nenhuma informação documentação seja criada.</span><span class="sxs-lookup"><span data-stu-id="86c55-111">Specifying `-` is the equivalent of not specifying `/doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="86c55-112">Necessário se `/doc:` for usado.</span><span class="sxs-lookup"><span data-stu-id="86c55-112">Required if `/doc:` is used.</span></span> <span data-ttu-id="86c55-113">Especifica o arquivo XML de saída, que é preenchido com os comentários dos arquivos de código-fonte da compilação.</span><span class="sxs-lookup"><span data-stu-id="86c55-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="86c55-114">Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="86c55-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86c55-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="86c55-115">Remarks</span></span>  
 <span data-ttu-id="86c55-116">O `/doc` opção controla se o compilador gera um arquivo XML contendo comentários de documentação.</span><span class="sxs-lookup"><span data-stu-id="86c55-116">The `/doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="86c55-117">Se você usar o `/doc:``file` sintaxe, o `file` parâmetro especifica o nome do arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="86c55-117">If you use the `/doc:``file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="86c55-118">Se você usar `/doc` ou `/doc+`, o compilador pega o nome do arquivo XML do arquivo executável ou biblioteca que está sendo criada pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="86c55-118">If you use `/doc` or `/doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="86c55-119">Se você usar `/doc-` ou não especifique o `/doc` opção, o compilador não cria um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="86c55-119">If you use `/doc-` or do not specify the `/doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="86c55-120">Em arquivos de código-fonte, comentários documentação podem preceder as seguintes definições:</span><span class="sxs-lookup"><span data-stu-id="86c55-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="86c55-121">Definido pelo usuário tipos, como um [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="86c55-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="86c55-122">Membros, como um campo, [evento](../../../visual-basic/language-reference/statements/event-statement.md), [propriedade](../../../visual-basic/language-reference/statements/property-statement.md), [função](../../../visual-basic/language-reference/statements/function-statement.md), ou [sub-rotina](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="86c55-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="86c55-123">Para usar o arquivo XML gerado com o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense) recurso, deixe o nome do arquivo do arquivo XML ser o mesmo que o assembly que você deseja oferecer suporte.</span><span class="sxs-lookup"><span data-stu-id="86c55-123">To use the generated XML file with the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="86c55-124">Verifique se o arquivo XML está no mesmo diretório que o assembly para que quando o assembly for referenciado no [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] projeto, o arquivo. XML seja encontrado também.</span><span class="sxs-lookup"><span data-stu-id="86c55-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] project, the .xml file is found as well.</span></span> <span data-ttu-id="86c55-125">Arquivos de documentação XML não são necessários para IntelliSense para funcionar com código em um projeto ou em projetos referenciados por um projeto.</span><span class="sxs-lookup"><span data-stu-id="86c55-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="86c55-126">A menos que você compile com `/target:module`, o arquivo XML contém as marcas `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="86c55-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="86c55-127">Essas marcas especificam o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.</span><span class="sxs-lookup"><span data-stu-id="86c55-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="86c55-128">Consulte [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) de maneiras de gerar documentação de comentários em seu código.</span><span class="sxs-lookup"><span data-stu-id="86c55-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="86c55-129">Configurar /doc no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="86c55-129">To set /doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="86c55-130">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="86c55-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="86c55-131">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="86c55-131">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="86c55-132">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="86c55-132">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="86c55-133">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="86c55-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="86c55-134">3.  Defina o valor no **arquivo de documentação XML gerar** caixa.</span><span class="sxs-lookup"><span data-stu-id="86c55-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86c55-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86c55-135">Example</span></span>  
 <span data-ttu-id="86c55-136">Consulte [documentar seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="86c55-136">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c55-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86c55-137">See Also</span></span>  
 <span data-ttu-id="86c55-138">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="86c55-138">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="86c55-139"> [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)</span><span class="sxs-lookup"><span data-stu-id="86c55-139"> [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)</span></span>
