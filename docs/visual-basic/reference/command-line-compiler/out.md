---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 234071d043b2649e2438ed20fe044fb89cdb9bf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-out-visual-basic"></a><span data-ttu-id="9a234-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a234-102">-out (Visual Basic)</span></span>
<span data-ttu-id="9a234-103">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="9a234-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a234-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a234-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a234-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9a234-105">Arguments</span></span>  
  
|<span data-ttu-id="9a234-106">Termo</span><span class="sxs-lookup"><span data-stu-id="9a234-106">Term</span></span>|<span data-ttu-id="9a234-107">Definição</span><span class="sxs-lookup"><span data-stu-id="9a234-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="9a234-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9a234-108">Required.</span></span> <span data-ttu-id="9a234-109">O nome do arquivo de saída que o compilador cria.</span><span class="sxs-lookup"><span data-stu-id="9a234-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="9a234-110">Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="9a234-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a234-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a234-111">Remarks</span></span>  
 <span data-ttu-id="9a234-112">Especifique o nome completo e a extensão de arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="9a234-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="9a234-113">Se você não fizer isso, o arquivo de .exe leva seu nome a partir do arquivo de código-fonte que contém o `Sub Main` procedimento e o arquivo. dll leva seu nome do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="9a234-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="9a234-114">Se você especificar um nome de arquivo sem uma extensão .exe ou. dll, o compilador adiciona automaticamente a extensão para você, dependendo do valor especificado para o `-target` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="9a234-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="9a234-115">Para definir - out no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9a234-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9a234-116">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="9a234-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9a234-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9a234-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9a234-118">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="9a234-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="9a234-119">3.  Modificar o valor de **nome do Assembly** caixa.</span><span class="sxs-lookup"><span data-stu-id="9a234-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9a234-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a234-120">Example</span></span>  
 <span data-ttu-id="9a234-121">O código a seguir compila `T2.vb` e cria o arquivo de saída `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="9a234-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a234-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a234-122">See Also</span></span>  
 [<span data-ttu-id="9a234-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a234-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9a234-124">-alvo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a234-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="9a234-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a234-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
