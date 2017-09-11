---
title: /optionexplicit | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
dev_langs:
- VB
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
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
ms.openlocfilehash: 3d2622c08b863233c8e1088bad252b37b3b38b04
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="optionexplicit"></a><span data-ttu-id="e9f17-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e9f17-102">/optionexplicit</span></span>
<span data-ttu-id="e9f17-103">Faz com que o compilador reporte erros se variáveis não são declaradas antes de serem usadas.</span><span class="sxs-lookup"><span data-stu-id="e9f17-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9f17-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9f17-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9f17-105">Arguments</span></span>  
 <span data-ttu-id="e9f17-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e9f17-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e9f17-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e9f17-107">Optional.</span></span> <span data-ttu-id="e9f17-108">Especifique `/optionexplicit+` para requisitar declarações explícitas de variáveis.</span><span class="sxs-lookup"><span data-stu-id="e9f17-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="e9f17-109">O `/optionexplicit+` opção é o padrão e é o mesmo que `/optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="e9f17-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="e9f17-110">O `/optionexplicit-` opção permite declarações implícitas de variáveis.</span><span class="sxs-lookup"><span data-stu-id="e9f17-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9f17-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9f17-111">Remarks</span></span>  
 <span data-ttu-id="e9f17-112">Se o arquivo de código fonte contém uma [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a instrução substitui a `/optionexplicit` configuração do compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e9f17-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="e9f17-113">Para definir /optionexplicit na IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e9f17-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e9f17-114">Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="e9f17-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e9f17-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e9f17-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e9f17-116">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="e9f17-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="e9f17-117">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="e9f17-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e9f17-118">Modificar o valor de **Option Explicit** caixa.</span><span class="sxs-lookup"><span data-stu-id="e9f17-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9f17-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9f17-119">Example</span></span>  
 <span data-ttu-id="e9f17-120">O código a seguir compila quando `/optionexplicit-` é usado.</span><span class="sxs-lookup"><span data-stu-id="e9f17-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 <span data-ttu-id="e9f17-121">[!code-vb[VbVbalrCompiler n º&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e9f17-121">[!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f17-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9f17-122">See Also</span></span>  
 <span data-ttu-id="e9f17-123">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="e9f17-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="e9f17-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="e9f17-124"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="e9f17-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="e9f17-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="e9f17-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="e9f17-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="e9f17-127"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="e9f17-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="e9f17-128"> [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e9f17-128"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="e9f17-129"> [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="e9f17-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
