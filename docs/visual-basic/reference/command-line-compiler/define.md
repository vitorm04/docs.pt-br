---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="1ec34-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ec34-102">/define (Visual Basic)</span></span>
<span data-ttu-id="1ec34-103">Define as constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="1ec34-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec34-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ec34-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ec34-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1ec34-105">Arguments</span></span>  
  
|<span data-ttu-id="1ec34-106">Termo</span><span class="sxs-lookup"><span data-stu-id="1ec34-106">Term</span></span>|<span data-ttu-id="1ec34-107">Definição</span><span class="sxs-lookup"><span data-stu-id="1ec34-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="1ec34-108">Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1ec34-108">Required.</span></span> <span data-ttu-id="1ec34-109">O símbolo a ser definido.</span><span class="sxs-lookup"><span data-stu-id="1ec34-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="1ec34-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1ec34-110">Optional.</span></span> <span data-ttu-id="1ec34-111">O valor para atribuir `symbol`.</span><span class="sxs-lookup"><span data-stu-id="1ec34-111">The value to assign `symbol`.</span></span> <span data-ttu-id="1ec34-112">Se `value` é uma cadeia de caracteres, ele deve estar entre sequências de barra invertida/aspas (\\") em vez de aspas.</span><span class="sxs-lookup"><span data-stu-id="1ec34-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="1ec34-113">Se nenhum valor for especificado, será considerado como True.</span><span class="sxs-lookup"><span data-stu-id="1ec34-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ec34-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ec34-114">Remarks</span></span>  
 <span data-ttu-id="1ec34-115">A opção `/define` tem um efeito semelhante a usar uma diretiva de pré-processador `#Const` em seu arquivo de origem, exceto que as constantes definidas com `/define` são públicas e se aplicam a todos os arquivos do projeto.</span><span class="sxs-lookup"><span data-stu-id="1ec34-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="1ec34-116">Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="1ec34-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="1ec34-117">`/d` é a forma abreviada de `/define`.</span><span class="sxs-lookup"><span data-stu-id="1ec34-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="1ec34-118">Você pode definir vários símbolos com `/define` usando uma vírgula para separar as definições de símbolos.</span><span class="sxs-lookup"><span data-stu-id="1ec34-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="1ec34-119">Para configurar /define no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ec34-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1ec34-120">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="1ec34-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1ec34-121">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="1ec34-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1ec34-122">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1ec34-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1ec34-123">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="1ec34-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1ec34-124">3.  Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="1ec34-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="1ec34-125">4.  Modificar o valor de **constantes personalizadas** caixa.</span><span class="sxs-lookup"><span data-stu-id="1ec34-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1ec34-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ec34-126">Example</span></span>  
 <span data-ttu-id="1ec34-127">O código a seguir define e usa duas constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="1ec34-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1ec34-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ec34-128">See Also</span></span>  
 [<span data-ttu-id="1ec34-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ec34-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1ec34-130">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="1ec34-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="1ec34-131">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="1ec34-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="1ec34-132">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ec34-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
