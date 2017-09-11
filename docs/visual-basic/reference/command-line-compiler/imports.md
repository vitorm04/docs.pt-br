---
title: /Imports (Visual Basic) | Documentos do Microsoft
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
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
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
ms.openlocfilehash: e994e94dcc3cd00f868b6ae90e4c019eb5b9e2eb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="imports-visual-basic"></a><span data-ttu-id="acbd4-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acbd4-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="acbd4-103">Importa namespaces de um assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="acbd4-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acbd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acbd4-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="acbd4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="acbd4-105">Arguments</span></span>  
  
|<span data-ttu-id="acbd4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="acbd4-106">Term</span></span>|<span data-ttu-id="acbd4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="acbd4-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="acbd4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="acbd4-108">Required.</span></span> <span data-ttu-id="acbd4-109">Lista delimitada por vírgula de namespaces a serem importados.</span><span class="sxs-lookup"><span data-stu-id="acbd4-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acbd4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="acbd4-110">Remarks</span></span>  
 <span data-ttu-id="acbd4-111">O `/imports` opção importa qualquer namespace definido no interior do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="acbd4-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="acbd4-112">Os membros no namespace especificado com `/imports` estão disponíveis para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="acbd4-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="acbd4-113">Use o [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para utilizar um namespace em um arquivo de código-fonte única.</span><span class="sxs-lookup"><span data-stu-id="acbd4-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="acbd4-114">Para configurar /Imports no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="acbd4-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="acbd4-115">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="acbd4-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="acbd4-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="acbd4-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="acbd4-117">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="acbd4-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="acbd4-118">2.  Clique o **referências** guia.</span><span class="sxs-lookup"><span data-stu-id="acbd4-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="acbd4-119">3.  Insira o nome do namespace na caixa ao lado de **Add User Import** botão.</span><span class="sxs-lookup"><span data-stu-id="acbd4-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="acbd4-120">4.  Clique o **Add User Import** botão.</span><span class="sxs-lookup"><span data-stu-id="acbd4-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="acbd4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acbd4-121">Example</span></span>  
 <span data-ttu-id="acbd4-122">O código a seguir compila quando `/imports:system` for especificado.</span><span class="sxs-lookup"><span data-stu-id="acbd4-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 <span data-ttu-id="acbd4-123">[!code-vb[VbVbalrCompiler&#21;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="acbd4-123">[!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acbd4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acbd4-124">See Also</span></span>  
 <span data-ttu-id="acbd4-125">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="acbd4-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="acbd4-126"> [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="acbd4-126"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="acbd4-127"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="acbd4-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
