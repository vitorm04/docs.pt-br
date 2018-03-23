---
title: -Importa (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d81e9d2bd55e6e38e337805b950a0b85680d129b
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="952a4-102">-Importa (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="952a4-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="952a4-103">Importa namespaces de um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="952a4-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="952a4-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="952a4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="952a4-105">Arguments</span></span>  
  
|<span data-ttu-id="952a4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="952a4-106">Term</span></span>|<span data-ttu-id="952a4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="952a4-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="952a4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="952a4-108">Required.</span></span> <span data-ttu-id="952a4-109">Lista delimitada por vírgulas de namespaces a serem importados.</span><span class="sxs-lookup"><span data-stu-id="952a4-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="952a4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="952a4-110">Remarks</span></span>  
 <span data-ttu-id="952a4-111">O `-imports` opção importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="952a4-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="952a4-112">Os membros no namespace especificado com `-imports` estão disponíveis para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="952a4-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="952a4-113">Use o [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para utilizar um namespace em um arquivo de código-fonte única.</span><span class="sxs-lookup"><span data-stu-id="952a4-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="952a4-114">Para configurar /Imports no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="952a4-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="952a4-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="952a4-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="952a4-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="952a4-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="952a4-117">2.  Clique na guia **Referências**.</span><span class="sxs-lookup"><span data-stu-id="952a4-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="952a4-118">3.  Insira o nome do namespace na caixa ao lado de **Add User Import** botão.</span><span class="sxs-lookup"><span data-stu-id="952a4-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="952a4-119">4.  Clique o **Add User Import** botão.</span><span class="sxs-lookup"><span data-stu-id="952a4-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="952a4-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="952a4-120">Example</span></span>  
 <span data-ttu-id="952a4-121">O código a seguir compila quando `/imports:system.globalization` for especificado.</span><span class="sxs-lookup"><span data-stu-id="952a4-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="952a4-122">Sem ele, compilação bem-sucedida requer que um `Imports System.Globalization` instrução ser incluído no início do arquivo de código fonte ou a propriedade ser totalmente qualificada como `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="952a4-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span> 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="952a4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="952a4-123">See Also</span></span>  
 [<span data-ttu-id="952a4-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="952a4-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="952a4-125">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="952a4-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="952a4-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="952a4-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
