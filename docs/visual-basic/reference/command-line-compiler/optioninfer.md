---
title: /optioninfer | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioninfer
dev_langs:
- VB
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
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
ms.openlocfilehash: 4bcc35da2a255ca75805c8a918027d2ccb61b154
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="optioninfer"></a><span data-ttu-id="34acc-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="34acc-102">/optioninfer</span></span>
<span data-ttu-id="34acc-103">Permite o uso de inferência de tipo local nas declarações de variáveis.</span><span class="sxs-lookup"><span data-stu-id="34acc-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34acc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34acc-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="34acc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="34acc-105">Arguments</span></span>  
  
|<span data-ttu-id="34acc-106">Termo</span><span class="sxs-lookup"><span data-stu-id="34acc-106">Term</span></span>|<span data-ttu-id="34acc-107">Definição</span><span class="sxs-lookup"><span data-stu-id="34acc-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="34acc-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="34acc-108">`+` &#124; `-`</span></span>|<span data-ttu-id="34acc-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="34acc-109">Optional.</span></span> <span data-ttu-id="34acc-110">Especifique `/optioninfer+` para habilitar a inferência de tipo de local ou `/optioninfer-` para bloqueá-la.</span><span class="sxs-lookup"><span data-stu-id="34acc-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="34acc-111">A opção `/optioninfer`, sem valor especificado, é a mesma de `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="34acc-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="34acc-112">O valor padrão quando o comutador `/optioninfer` não estiver presente também é `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="34acc-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="34acc-113">O valor padrão é definido no arquivo de resposta Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="34acc-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="34acc-114">Você pode usar a opção `/noconfig` para manter os padrões internos do compilador em vez dos especificados no vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="34acc-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="34acc-115">O padrão do compilador para essa opção é `/optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="34acc-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34acc-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="34acc-116">Remarks</span></span>  
 <span data-ttu-id="34acc-117">Se o arquivo de código fonte contém uma [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), a instrução substitui a `/optioninfer` configuração do compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="34acc-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="34acc-118">Para definir /optioninfer no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="34acc-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="34acc-119">Selecione um projeto na **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="34acc-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="34acc-120">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="34acc-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="34acc-121">Para obter mais informações, consulte [NIB: Gerenciando propriedades do projeto com o Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="34acc-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="34acc-122">Sobre o **compilar** guia, modifique o valor no **Option infer** caixa.</span><span class="sxs-lookup"><span data-stu-id="34acc-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34acc-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34acc-123">Example</span></span>  
 <span data-ttu-id="34acc-124">O seguinte código compila `test.vb` com a inferência de tipo local habilitada.</span><span class="sxs-lookup"><span data-stu-id="34acc-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="34acc-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34acc-125">See Also</span></span>  
 <span data-ttu-id="34acc-126">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="34acc-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-127"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="34acc-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-128"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="34acc-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-129"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="34acc-130"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="34acc-131"> [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-131"> [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="34acc-132"> [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-132"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="34acc-133"> [Caixa de diálogo de opções de padrões, projetos do Visual Basic](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span><span class="sxs-lookup"><span data-stu-id="34acc-133"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span></span>  
<span data-ttu-id="34acc-134"> [Página de Compilação, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="34acc-134"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="34acc-135"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="34acc-135"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="34acc-136"> [Compilando da Linha de Comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span><span class="sxs-lookup"><span data-stu-id="34acc-136"> [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)</span></span>
