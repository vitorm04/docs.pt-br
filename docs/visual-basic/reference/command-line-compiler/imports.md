---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8e9cd761263b3b61a4e6d3e33c5f7f875be7a1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imports-visual-basic"></a><span data-ttu-id="7574a-102">/imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7574a-102">/imports (Visual Basic)</span></span>
<span data-ttu-id="7574a-103">Importa namespaces de um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="7574a-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7574a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7574a-104">Syntax</span></span>  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="7574a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7574a-105">Arguments</span></span>  
  
|<span data-ttu-id="7574a-106">Termo</span><span class="sxs-lookup"><span data-stu-id="7574a-106">Term</span></span>|<span data-ttu-id="7574a-107">Definição</span><span class="sxs-lookup"><span data-stu-id="7574a-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="7574a-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="7574a-108">Required.</span></span> <span data-ttu-id="7574a-109">Lista delimitada por vírgulas de namespaces a serem importados.</span><span class="sxs-lookup"><span data-stu-id="7574a-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7574a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7574a-110">Remarks</span></span>  
 <span data-ttu-id="7574a-111">O `/imports` opção importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="7574a-111">The `/imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="7574a-112">Os membros no namespace especificado com `/imports` estão disponíveis para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="7574a-112">The members in a namespace specified with `/imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="7574a-113">Use o [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para utilizar um namespace em um arquivo de código-fonte única.</span><span class="sxs-lookup"><span data-stu-id="7574a-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="7574a-114">Para configurar /Imports no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7574a-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="7574a-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="7574a-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7574a-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7574a-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="7574a-117">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="7574a-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="7574a-118">2.  Clique na guia **Referências**.</span><span class="sxs-lookup"><span data-stu-id="7574a-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="7574a-119">3.  Insira o nome do namespace na caixa ao lado de **Add User Import** botão.</span><span class="sxs-lookup"><span data-stu-id="7574a-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="7574a-120">4.  Clique o **Add User Import** botão.</span><span class="sxs-lookup"><span data-stu-id="7574a-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7574a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7574a-121">Example</span></span>  
 <span data-ttu-id="7574a-122">O código a seguir compila quando `/imports:system` for especificado.</span><span class="sxs-lookup"><span data-stu-id="7574a-122">The following code compiles when `/imports:system` is specified.</span></span>  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7574a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7574a-123">See Also</span></span>  
 [<span data-ttu-id="7574a-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7574a-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7574a-125">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="7574a-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="7574a-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="7574a-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
