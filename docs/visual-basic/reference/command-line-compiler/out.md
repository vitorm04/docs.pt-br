---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 6b005ac26e3fffad350cb4ce52f7757c9fff2ac1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005337"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="20d07-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d07-102">-out (Visual Basic)</span></span>
<span data-ttu-id="20d07-103">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="20d07-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20d07-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="20d07-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="20d07-105">Arguments</span></span>  
  
|<span data-ttu-id="20d07-106">Termo</span><span class="sxs-lookup"><span data-stu-id="20d07-106">Term</span></span>|<span data-ttu-id="20d07-107">Definição</span><span class="sxs-lookup"><span data-stu-id="20d07-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="20d07-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="20d07-108">Required.</span></span> <span data-ttu-id="20d07-109">O nome do arquivo de saída criado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="20d07-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="20d07-110">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="20d07-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20d07-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="20d07-111">Remarks</span></span>  
 <span data-ttu-id="20d07-112">Especifique o nome completo e a extensão do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="20d07-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="20d07-113">Se você não fizer isso, o arquivo. exe usará o nome do arquivo de código-fonte que contém o procedimento `Sub Main` e o arquivo. dll usará seu nome do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="20d07-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="20d07-114">Se você especificar um nome de arquivo sem uma extensão. exe ou. dll, o compilador adicionará automaticamente a extensão para você, dependendo do valor especificado para a opção de compilador `-target`.</span><span class="sxs-lookup"><span data-stu-id="20d07-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="20d07-115">Para definir no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20d07-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="20d07-116">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="20d07-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="20d07-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="20d07-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="20d07-118">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="20d07-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="20d07-119">3.  Modifique o valor na caixa **nome do assembly** .</span><span class="sxs-lookup"><span data-stu-id="20d07-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20d07-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20d07-120">Example</span></span>  
 <span data-ttu-id="20d07-121">O código a seguir compila `T2.vb` e cria o arquivo de saída `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="20d07-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="20d07-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20d07-122">See also</span></span>

- [<span data-ttu-id="20d07-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20d07-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="20d07-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d07-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="20d07-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="20d07-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
