---
title: /optioncompare | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
dev_langs:
- VB
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
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
ms.openlocfilehash: c9512427cda0b6a3bcb0c1fe338b47ff9f779d19
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="optioncompare"></a><span data-ttu-id="7c045-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="7c045-102">/optioncompare</span></span>
<span data-ttu-id="7c045-103">Especifica como são feitas comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7c045-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c045-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c045-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="7c045-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c045-105">Remarks</span></span>  
 <span data-ttu-id="7c045-106">Você pode especificar `/optioncompare` em uma destas duas formas: `/optioncompare:binary` usar comparações de cadeia de caracteres binária e `/optioncompare:text` usar comparações de cadeias de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="7c045-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="7c045-107">Por padrão, o compilador usa `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="7c045-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="7c045-108">No Microsoft Windows, a página de código que está sendo usada determina a ordem de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="7c045-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="7c045-109">Uma ordem de classificação binária típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="7c045-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="7c045-110">Comparações de cadeia de caracteres com base em texto baseiam-se em uma ordem de classificação de texto diferenciam maiusculas de minúsculas determinada pela localidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="7c045-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="7c045-111">Uma ordem de classificação de texto típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="7c045-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="7c045-112">Para configurar /optioncompare no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7c045-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="7c045-113">Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="7c045-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7c045-114">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7c045-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="7c045-115">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="7c045-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="7c045-116">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="7c045-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="7c045-117">Modificar o valor de **Option Compare** caixa.</span><span class="sxs-lookup"><span data-stu-id="7c045-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="7c045-118">Para configurar /optioncompare programaticamente</span><span class="sxs-lookup"><span data-stu-id="7c045-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="7c045-119">Consulte [instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7c045-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c045-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7c045-120">Example</span></span>  
 <span data-ttu-id="7c045-121">O código a seguir compila P`rojFile.vb` e usa comparações de cadeia de caracteres binária.</span><span class="sxs-lookup"><span data-stu-id="7c045-121">The following code compiles P`rojFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c045-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c045-122">See Also</span></span>  
 <span data-ttu-id="7c045-123">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="7c045-123">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="7c045-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="7c045-124"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="7c045-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="7c045-125"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="7c045-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="7c045-126"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="7c045-127"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="7c045-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="7c045-128"> [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7c045-128"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="7c045-129"> [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="7c045-129"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
