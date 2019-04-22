---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 5dcf9dc5cc0987e965aba7fd2b8821252e19a655
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815986"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="f5065-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5065-102">-out (Visual Basic)</span></span>
<span data-ttu-id="f5065-103">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="f5065-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5065-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5065-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5065-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f5065-105">Arguments</span></span>  
  
|<span data-ttu-id="f5065-106">Termo</span><span class="sxs-lookup"><span data-stu-id="f5065-106">Term</span></span>|<span data-ttu-id="f5065-107">Definição</span><span class="sxs-lookup"><span data-stu-id="f5065-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="f5065-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f5065-108">Required.</span></span> <span data-ttu-id="f5065-109">O nome do arquivo de saída, que o compilador cria.</span><span class="sxs-lookup"><span data-stu-id="f5065-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="f5065-110">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="f5065-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5065-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5065-111">Remarks</span></span>  
 <span data-ttu-id="f5065-112">Especifique o nome completo e a extensão de arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="f5065-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="f5065-113">Se você não fizer isso, o arquivo .exe recebe seu nome do arquivo de código-fonte que contém o `Sub Main` recebe seu nome de procedimento e o arquivo. dll do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="f5065-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="f5065-114">Se você especificar um nome de arquivo sem uma extensão .exe ou. dll, o compilador adiciona automaticamente a extensão para você, dependendo do valor especificado para o `-target` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="f5065-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="f5065-115">Definir - out no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5065-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f5065-116">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="f5065-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f5065-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f5065-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f5065-118">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="f5065-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="f5065-119">3.  Modificar o valor de **nome do Assembly** caixa.</span><span class="sxs-lookup"><span data-stu-id="f5065-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f5065-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5065-120">Example</span></span>  
 <span data-ttu-id="f5065-121">O seguinte código compila `T2.vb` e cria o arquivo de saída `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="f5065-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5065-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5065-122">See also</span></span>

- [<span data-ttu-id="f5065-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5065-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f5065-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5065-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="f5065-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5065-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
