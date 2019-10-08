---
title: -importações (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005569"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="71109-102">-importações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71109-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="71109-103">Importa namespaces de um assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="71109-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71109-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71109-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="71109-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="71109-105">Arguments</span></span>  
  
|<span data-ttu-id="71109-106">Termo</span><span class="sxs-lookup"><span data-stu-id="71109-106">Term</span></span>|<span data-ttu-id="71109-107">Definição</span><span class="sxs-lookup"><span data-stu-id="71109-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="71109-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="71109-108">Required.</span></span> <span data-ttu-id="71109-109">Lista delimitada por vírgulas de namespaces a serem importados.</span><span class="sxs-lookup"><span data-stu-id="71109-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71109-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="71109-110">Remarks</span></span>  
 <span data-ttu-id="71109-111">A opção `-imports` importa qualquer namespace definido dentro do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="71109-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="71109-112">Os membros em um namespace especificado com `-imports` estão disponíveis para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="71109-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="71109-113">Use a [instrução Imports (namespace e tipo do .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para usar um namespace em um único arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="71109-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="71109-114">Para definir/Imports no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71109-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="71109-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="71109-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="71109-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="71109-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="71109-117">2.  Clique na guia **Referências**.</span><span class="sxs-lookup"><span data-stu-id="71109-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="71109-118">3.  Digite o nome do namespace na caixa ao lado do botão **Adicionar importação de usuário** .</span><span class="sxs-lookup"><span data-stu-id="71109-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="71109-119">4.  Clique no botão **Adicionar importação de usuário** .</span><span class="sxs-lookup"><span data-stu-id="71109-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="71109-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71109-120">Example</span></span>  
 <span data-ttu-id="71109-121">O código a seguir é compilado quando `/imports:system.globalization` é especificado.</span><span class="sxs-lookup"><span data-stu-id="71109-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="71109-122">Sem ele, a compilação bem-sucedida requer que uma instrução `Imports System.Globalization` seja incluída no início do arquivo de código-fonte ou que a propriedade seja totalmente qualificada como `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="71109-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="71109-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71109-123">See also</span></span>

- [<span data-ttu-id="71109-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71109-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="71109-125">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="71109-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="71109-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="71109-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
