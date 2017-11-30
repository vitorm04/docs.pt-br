---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6f602e0b0b23345bf1f5aae843bd44bd2642bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="26819-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="26819-102">/optioncompare</span></span>
<span data-ttu-id="26819-103">Especifica como são feitas comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="26819-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26819-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26819-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="26819-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="26819-105">Remarks</span></span>  
 <span data-ttu-id="26819-106">Você pode especificar `/optioncompare` em uma das duas formas: `/optioncompare:binary` usar comparações de cadeia de caracteres binária e `/optioncompare:text` usar comparações de cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="26819-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="26819-107">Por padrão, o compilador usa `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="26819-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="26819-108">No Microsoft Windows, a página de código que está sendo usada determina a ordem de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="26819-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="26819-109">Uma ordem de classificação binária típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="26819-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="26819-110">Comparações de cadeia de caracteres com base em texto são baseadas em uma ordem de classificação de maiusculas e minúsculas do texto determinada pela localidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="26819-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="26819-111">Uma ordem de classificação de texto típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="26819-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="26819-112">Para configurar /optioncompare no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26819-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="26819-113">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="26819-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="26819-114">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="26819-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="26819-115">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="26819-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="26819-116">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="26819-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="26819-117">Modificar o valor de **Option Compare** caixa.</span><span class="sxs-lookup"><span data-stu-id="26819-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="26819-118">Para configurar /optioncompare programaticamente</span><span class="sxs-lookup"><span data-stu-id="26819-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="26819-119">Consulte [instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="26819-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26819-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26819-120">Example</span></span>  
 <span data-ttu-id="26819-121">O código a seguir compila `ProjFile.vb` e usa comparações de cadeia de caracteres binária.</span><span class="sxs-lookup"><span data-stu-id="26819-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="26819-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26819-122">See Also</span></span>  
 [<span data-ttu-id="26819-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26819-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="26819-124">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="26819-124">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="26819-125">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="26819-125">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="26819-126">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="26819-126">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="26819-127">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="26819-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="26819-128">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="26819-128">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="26819-129">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="26819-129">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
