---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 380e71e462f736d4564a37b83567007fa9461b05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332963"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="d98d4-102">-importações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d98d4-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="d98d4-103">Importa namespaces de um assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="d98d4-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d98d4-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d98d4-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d98d4-105">Arguments</span></span>  
  
|<span data-ttu-id="d98d4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="d98d4-106">Term</span></span>|<span data-ttu-id="d98d4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="d98d4-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="d98d4-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d98d4-108">Required.</span></span> <span data-ttu-id="d98d4-109">Lista delimitada por vírgulas de namespaces a serem importados.</span><span class="sxs-lookup"><span data-stu-id="d98d4-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d98d4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d98d4-110">Remarks</span></span>  
 <span data-ttu-id="d98d4-111">A opção `-imports` importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="d98d4-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="d98d4-112">Os membros em um namespace especificado com `-imports` estão disponíveis para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="d98d4-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="d98d4-113">Use a [instrução Imports (namespace e tipo do .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para usar um namespace em um único arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="d98d4-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="d98d4-114">Para definir/Imports no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d98d4-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d98d4-115">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="d98d4-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d98d4-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d98d4-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d98d4-117">2. Clique na guia **referências** .</span><span class="sxs-lookup"><span data-stu-id="d98d4-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="d98d4-118">3. Insira o nome do namespace na caixa ao lado do botão **Adicionar importação de usuário** .</span><span class="sxs-lookup"><span data-stu-id="d98d4-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="d98d4-119">4. Clique no botão **Adicionar importação de usuário** .</span><span class="sxs-lookup"><span data-stu-id="d98d4-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d98d4-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d98d4-120">Example</span></span>  
 <span data-ttu-id="d98d4-121">O código a seguir é compilado quando `/imports:system.globalization` é especificado.</span><span class="sxs-lookup"><span data-stu-id="d98d4-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="d98d4-122">Sem ele, a compilação bem-sucedida requer que uma instrução `Imports System.Globalization` seja incluída no início do arquivo de código-fonte ou que a propriedade seja totalmente qualificada como `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="d98d4-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="d98d4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d98d4-123">See also</span></span>

- [<span data-ttu-id="d98d4-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d98d4-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d98d4-125">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="d98d4-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="d98d4-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d98d4-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
