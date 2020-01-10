---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716643"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="e355c-102">-importações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e355c-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="e355c-103">Importa namespaces de um assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="e355c-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e355c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e355c-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="e355c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e355c-105">Arguments</span></span>  
  
|<span data-ttu-id="e355c-106">Termo</span><span class="sxs-lookup"><span data-stu-id="e355c-106">Term</span></span>|<span data-ttu-id="e355c-107">Definição</span><span class="sxs-lookup"><span data-stu-id="e355c-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="e355c-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="e355c-108">Required.</span></span> <span data-ttu-id="e355c-109">Lista delimitada por vírgulas de namespaces a serem importados.</span><span class="sxs-lookup"><span data-stu-id="e355c-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e355c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e355c-110">Remarks</span></span>  
 <span data-ttu-id="e355c-111">A opção `-imports` importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="e355c-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="e355c-112">Os membros em um namespace especificado com `-imports` estão disponíveis para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="e355c-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="e355c-113">Use a [instrução Imports (namespace e tipo do .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para usar um namespace em um único arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="e355c-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="e355c-114">Para Set-Imports no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e355c-114">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="e355c-115">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="e355c-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e355c-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e355c-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e355c-117">2. Clique na guia **referências** .</span><span class="sxs-lookup"><span data-stu-id="e355c-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="e355c-118">3. Insira o nome do namespace na caixa ao lado do botão **Adicionar importação de usuário** .</span><span class="sxs-lookup"><span data-stu-id="e355c-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="e355c-119">4. Clique no botão **Adicionar importação de usuário** .</span><span class="sxs-lookup"><span data-stu-id="e355c-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e355c-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e355c-120">Example</span></span>  
 <span data-ttu-id="e355c-121">O código a seguir é compilado quando `-imports:system.globalization` é especificado.</span><span class="sxs-lookup"><span data-stu-id="e355c-121">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="e355c-122">Sem ele, a compilação bem-sucedida requer que uma instrução `Imports System.Globalization` seja incluída no início do arquivo de código-fonte ou que a propriedade seja totalmente qualificada como `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="e355c-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="e355c-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="e355c-123">See also</span></span>

- [<span data-ttu-id="e355c-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e355c-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e355c-125">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="e355c-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="e355c-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="e355c-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
