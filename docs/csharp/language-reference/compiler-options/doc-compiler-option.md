---
title: -doc (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: c46118a9b02df653844a0ca04f9e8f9952a957c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333594"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="d114d-102">-doc (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="d114d-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="d114d-103">A opção **-doc** permite colocar comentários de documentação em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="d114d-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d114d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d114d-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="d114d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d114d-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="d114d-106">O arquivo de saída para XML, que é populado com os comentários nos arquivos de código-fonte da compilação.</span><span class="sxs-lookup"><span data-stu-id="d114d-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d114d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d114d-107">Remarks</span></span>  
 <span data-ttu-id="d114d-108">Nos arquivos de código-fonte, os comentários de documentação que precedem o seguinte podem ser processados e adicionados ao arquivo XML:</span><span class="sxs-lookup"><span data-stu-id="d114d-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
-   <span data-ttu-id="d114d-109">Tipos definidos pelo usuário, como [classe](../../../csharp/language-reference/keywords/class.md), [delegado](../../../csharp/language-reference/keywords/delegate.md) ou [interface](../../../csharp/language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="d114d-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
-   <span data-ttu-id="d114d-110">Membros como um campo, [evento](../../../csharp/language-reference/keywords/event.md), [propriedade](../../../csharp/programming-guide/classes-and-structs/using-properties.md) ou método</span><span class="sxs-lookup"><span data-stu-id="d114d-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="d114d-111">O arquivo de código-fonte que contém Main é gerado primeiro no XML.</span><span class="sxs-lookup"><span data-stu-id="d114d-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="d114d-112">Para usar o arquivo .xml gerado para uso com o recurso [IntelliSense](/visualstudio/ide/using-intellisense), deixe o nome do arquivo .xml igual ao do assembly a que você deseja dar suporte e, em seguida, verifique se o arquivo .xml está no mesmo diretório que o assembly.</span><span class="sxs-lookup"><span data-stu-id="d114d-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="d114d-113">Sendo assim, quando o assembly for referenciado no projeto do Visual Studio, o arquivo .xml também será encontrado.</span><span class="sxs-lookup"><span data-stu-id="d114d-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="d114d-114">Consulte [Fornecendo comentários de código](/visualstudio/ide/supplying-xml-code-comments) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="d114d-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="d114d-115">A menos que você compile com [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` conterá marcas \<assembly>\</assembly> especificando o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.</span><span class="sxs-lookup"><span data-stu-id="d114d-115">Unless you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d114d-116">A opção -doc se aplica a todos os arquivos de entrada ou, se definida nas Configurações do Projeto, todos os arquivos no projeto.</span><span class="sxs-lookup"><span data-stu-id="d114d-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="d114d-117">Para desabilitar avisos relacionados aos comentários de documentação para um arquivo ou uma seção específica do código, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="d114d-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="d114d-118">Consulte [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) para ver maneiras de gerar a documentação dos comentários em seu código.</span><span class="sxs-lookup"><span data-stu-id="d114d-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d114d-119">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d114d-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d114d-120">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="d114d-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d114d-121">Clique na guia **Build**.</span><span class="sxs-lookup"><span data-stu-id="d114d-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="d114d-122">Modifique a propriedade **Arquivo de documentação XML**.</span><span class="sxs-lookup"><span data-stu-id="d114d-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="d114d-123">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="d114d-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d114d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d114d-124">See also</span></span>

- [<span data-ttu-id="d114d-125">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="d114d-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="d114d-126">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="d114d-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
