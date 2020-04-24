---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352381"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="6650e-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6650e-102">-out (Visual Basic)</span></span>
<span data-ttu-id="6650e-103">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6650e-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6650e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6650e-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="6650e-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="6650e-105">Arguments</span></span>  
  
|<span data-ttu-id="6650e-106">Termo</span><span class="sxs-lookup"><span data-stu-id="6650e-106">Term</span></span>|<span data-ttu-id="6650e-107">Definição</span><span class="sxs-lookup"><span data-stu-id="6650e-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="6650e-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="6650e-108">Required.</span></span> <span data-ttu-id="6650e-109">O nome do arquivo de saída criado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="6650e-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="6650e-110">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="6650e-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6650e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6650e-111">Remarks</span></span>  
 <span data-ttu-id="6650e-112">Especifique o nome completo e a extensão do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="6650e-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="6650e-113">Se você não fizer isso, o arquivo. exe usará o nome do arquivo de código-fonte `Sub Main` que contém o procedimento e o arquivo. dll usará seu nome do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="6650e-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="6650e-114">Se você especificar um nome de arquivo sem uma extensão. exe ou. dll, o compilador adicionará automaticamente a extensão para você, dependendo do valor especificado para a `-target` opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="6650e-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="6650e-115">Para definir no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6650e-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="6650e-116">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="6650e-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6650e-117">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6650e-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="6650e-118">2. Clique na guia **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="6650e-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="6650e-119">3. modifique o valor na caixa **nome do assembly** .</span><span class="sxs-lookup"><span data-stu-id="6650e-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6650e-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6650e-120">Example</span></span>  
 <span data-ttu-id="6650e-121">O código a seguir compila `T2.vb` e cria o arquivo `T2.exe`de saída.</span><span class="sxs-lookup"><span data-stu-id="6650e-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="6650e-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="6650e-122">See also</span></span>

- [<span data-ttu-id="6650e-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6650e-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6650e-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6650e-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="6650e-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="6650e-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
