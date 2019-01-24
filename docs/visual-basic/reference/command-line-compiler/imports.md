---
title: -Importa (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 9e5adcce85c4ca4863d28784a7d7f61c441a06c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588438"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="bef71-102">-Importa (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bef71-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="bef71-103">Importa namespaces de um assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="bef71-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bef71-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="bef71-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bef71-105">Arguments</span></span>  
  
|<span data-ttu-id="bef71-106">Termo</span><span class="sxs-lookup"><span data-stu-id="bef71-106">Term</span></span>|<span data-ttu-id="bef71-107">Definição</span><span class="sxs-lookup"><span data-stu-id="bef71-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="bef71-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bef71-108">Required.</span></span> <span data-ttu-id="bef71-109">Lista delimitada por vírgula de namespaces a serem importados.</span><span class="sxs-lookup"><span data-stu-id="bef71-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bef71-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bef71-110">Remarks</span></span>  
 <span data-ttu-id="bef71-111">O `-imports` opção importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="bef71-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="bef71-112">Os membros no namespace especificado com `-imports` estão disponíveis para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="bef71-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="bef71-113">Use o [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para utilizar um namespace em um arquivo de código-fonte única.</span><span class="sxs-lookup"><span data-stu-id="bef71-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="bef71-114">Para definir /Imports no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bef71-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="bef71-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="bef71-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bef71-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bef71-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="bef71-117">2.  Clique na guia **Referências**.</span><span class="sxs-lookup"><span data-stu-id="bef71-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="bef71-118">3.  Insira o nome do namespace na caixa ao lado de **Adicionar importação de usuário** botão.</span><span class="sxs-lookup"><span data-stu-id="bef71-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="bef71-119">4.  Clique o **Adicionar importação de usuário** botão.</span><span class="sxs-lookup"><span data-stu-id="bef71-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bef71-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bef71-120">Example</span></span>  
 <span data-ttu-id="bef71-121">O código a seguir compila quando `/imports:system.globalization` for especificado.</span><span class="sxs-lookup"><span data-stu-id="bef71-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="bef71-122">Sem ele, compilação bem-sucedida requer que um `Imports System.Globalization` instrução ser incluído no início do arquivo de código fonte ou a propriedade ser totalmente qualificada como `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="bef71-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span> 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bef71-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bef71-123">See also</span></span>
- [<span data-ttu-id="bef71-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bef71-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="bef71-125">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="bef71-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="bef71-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="bef71-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
