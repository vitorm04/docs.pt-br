---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 75f3ee7f24112f911803732ccb8d39eeafa95e3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400507"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="946a9-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946a9-102">-out (Visual Basic)</span></span>
<span data-ttu-id="946a9-103">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="946a9-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="946a9-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="946a9-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="946a9-105">Arguments</span></span>  
  
|<span data-ttu-id="946a9-106">Termo</span><span class="sxs-lookup"><span data-stu-id="946a9-106">Term</span></span>|<span data-ttu-id="946a9-107">Definição</span><span class="sxs-lookup"><span data-stu-id="946a9-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="946a9-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="946a9-108">Required.</span></span> <span data-ttu-id="946a9-109">O nome do arquivo de saída criado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="946a9-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="946a9-110">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="946a9-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="946a9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="946a9-111">Remarks</span></span>  
 <span data-ttu-id="946a9-112">Especifique o nome completo e a extensão do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="946a9-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="946a9-113">Se você não fizer isso, o arquivo. exe usará o nome do arquivo de código-fonte que contém o `Sub Main` procedimento e o arquivo. dll usará seu nome do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="946a9-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="946a9-114">Se você especificar um nome de arquivo sem uma extensão. exe ou. dll, o compilador adicionará automaticamente a extensão para você, dependendo do valor especificado para a `-target` opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="946a9-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="946a9-115">Para definir no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="946a9-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="946a9-116">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="946a9-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="946a9-117">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="946a9-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="946a9-118">2. Clique na guia **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="946a9-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="946a9-119">3. modifique o valor na caixa **nome do assembly** .</span><span class="sxs-lookup"><span data-stu-id="946a9-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="946a9-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="946a9-120">Example</span></span>  
 <span data-ttu-id="946a9-121">O código a seguir compila `T2.vb` e cria o arquivo de saída `T2.exe` .</span><span class="sxs-lookup"><span data-stu-id="946a9-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="946a9-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="946a9-122">See also</span></span>

- [<span data-ttu-id="946a9-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="946a9-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="946a9-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946a9-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="946a9-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="946a9-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
