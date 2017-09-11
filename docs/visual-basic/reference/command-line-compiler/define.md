---
title: /Define (Visual Basic) | Documentos do Microsoft
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
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
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
ms.openlocfilehash: e4eac32b4ab7259b9d3fd2ec37e21406c4cec326
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="define-visual-basic"></a><span data-ttu-id="2c7c5-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c7c5-102">/define (Visual Basic)</span></span>
<span data-ttu-id="2c7c5-103">Define as constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c7c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c7c5-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2c7c5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2c7c5-105">Arguments</span></span>  
  
|<span data-ttu-id="2c7c5-106">Termo</span><span class="sxs-lookup"><span data-stu-id="2c7c5-106">Term</span></span>|<span data-ttu-id="2c7c5-107">Definição</span><span class="sxs-lookup"><span data-stu-id="2c7c5-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="2c7c5-108">Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-108">Required.</span></span> <span data-ttu-id="2c7c5-109">O símbolo a ser definido.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="2c7c5-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-110">Optional.</span></span> <span data-ttu-id="2c7c5-111">O valor para atribuir `symbol`.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-111">The value to assign `symbol`.</span></span> <span data-ttu-id="2c7c5-112">Se `value` é uma cadeia de caracteres, ele deverá ser colocado entre sequências de barra invertida/aspas (\\") em vez de aspas.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="2c7c5-113">Se nenhum valor for especificado, será considerado como True.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c7c5-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c7c5-114">Remarks</span></span>  
 <span data-ttu-id="2c7c5-115">A opção `/define` tem um efeito semelhante a usar uma diretiva de pré-processador `#Const` em seu arquivo de origem, exceto que as constantes definidas com `/define` são públicas e se aplicam a todos os arquivos do projeto.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="2c7c5-116">Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="2c7c5-117">`/d` é a forma abreviada de `/define`.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="2c7c5-118">Você pode definir vários símbolos com `/define` usando uma vírgula para separar as definições de símbolos.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="2c7c5-119">Para configurar /define no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c7c5-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="2c7c5-120">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2c7c5-121">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="2c7c5-122">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="2c7c5-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="2c7c5-123">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="2c7c5-124">3.  Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="2c7c5-125">4.  Modificar o valor de **constantes personalizadas** caixa.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2c7c5-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c7c5-126">Example</span></span>  
 <span data-ttu-id="2c7c5-127">O código a seguir define e usa duas constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="2c7c5-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 <span data-ttu-id="2c7c5-128">[!code-vb[45 VbVbalrCompiler](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2c7c5-128">[!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c7c5-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c7c5-129">See Also</span></span>  
 <span data-ttu-id="2c7c5-130">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="2c7c5-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="2c7c5-131"> [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="2c7c5-131"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="2c7c5-132"> [# Diretiva const](../../../visual-basic/language-reference/directives/const-directive.md) </span><span class="sxs-lookup"><span data-stu-id="2c7c5-132"> [#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) </span></span>  
<span data-ttu-id="2c7c5-133"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="2c7c5-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
