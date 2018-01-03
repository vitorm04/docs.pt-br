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
ms.openlocfilehash: 62a9a4bf3428f3ee731e7ecc63be51dbf3076ee4
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="10604-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="10604-102">/optioncompare</span></span>
<span data-ttu-id="10604-103">Especifica como são feitas comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10604-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10604-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10604-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="10604-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="10604-105">Remarks</span></span>  
 <span data-ttu-id="10604-106">Você pode especificar `/optioncompare` em uma das duas formas: `/optioncompare:binary` usar comparações de cadeia de caracteres binária e `/optioncompare:text` usar comparações de cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="10604-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="10604-107">Por padrão, o compilador usa `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="10604-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="10604-108">No Microsoft Windows, a página de código que está sendo usada determina a ordem de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="10604-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="10604-109">Uma ordem de classificação binária típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="10604-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="10604-110">Comparações de cadeia de caracteres com base em texto são baseadas em uma ordem de classificação de maiusculas e minúsculas do texto determinada pela localidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="10604-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="10604-111">Uma ordem de classificação de texto típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="10604-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="10604-112">Para configurar /optioncompare no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10604-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="10604-113">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="10604-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="10604-114">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="10604-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="10604-115">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="10604-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="10604-116">Modificar o valor de **Option Compare** caixa.</span><span class="sxs-lookup"><span data-stu-id="10604-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="10604-117">Para configurar /optioncompare programaticamente</span><span class="sxs-lookup"><span data-stu-id="10604-117">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="10604-118">Consulte [instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="10604-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10604-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10604-119">Example</span></span>  
 <span data-ttu-id="10604-120">O código a seguir compila `ProjFile.vb` e usa comparações de cadeia de caracteres binária.</span><span class="sxs-lookup"><span data-stu-id="10604-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="10604-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10604-121">See Also</span></span>  
 [<span data-ttu-id="10604-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10604-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="10604-123">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="10604-123">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="10604-124">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="10604-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="10604-125">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="10604-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="10604-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="10604-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="10604-127">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="10604-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="10604-128">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="10604-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
