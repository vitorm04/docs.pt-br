---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 5dcf9dc5cc0987e965aba7fd2b8821252e19a655
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788889"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="66423-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66423-102">-out (Visual Basic)</span></span>
<span data-ttu-id="66423-103">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="66423-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66423-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66423-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="66423-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="66423-105">Arguments</span></span>  
  
|<span data-ttu-id="66423-106">Termo</span><span class="sxs-lookup"><span data-stu-id="66423-106">Term</span></span>|<span data-ttu-id="66423-107">Definição</span><span class="sxs-lookup"><span data-stu-id="66423-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="66423-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="66423-108">Required.</span></span> <span data-ttu-id="66423-109">O nome do arquivo de saída, que o compilador cria.</span><span class="sxs-lookup"><span data-stu-id="66423-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="66423-110">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="66423-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66423-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="66423-111">Remarks</span></span>  
 <span data-ttu-id="66423-112">Especifique o nome completo e a extensão de arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="66423-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="66423-113">Se você não fizer isso, o arquivo .exe recebe seu nome do arquivo de código-fonte que contém o `Sub Main` recebe seu nome de procedimento e o arquivo. dll do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="66423-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="66423-114">Se você especificar um nome de arquivo sem uma extensão .exe ou. dll, o compilador adiciona automaticamente a extensão para você, dependendo do valor especificado para o `-target` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="66423-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="66423-115">Definir - out no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66423-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="66423-116">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="66423-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="66423-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="66423-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="66423-118">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="66423-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="66423-119">3.  Modificar o valor de **nome do Assembly** caixa.</span><span class="sxs-lookup"><span data-stu-id="66423-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="66423-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="66423-120">Example</span></span>  
 <span data-ttu-id="66423-121">O seguinte código compila `T2.vb` e cria o arquivo de saída `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="66423-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="66423-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66423-122">See also</span></span>

- [<span data-ttu-id="66423-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66423-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="66423-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66423-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="66423-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="66423-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
