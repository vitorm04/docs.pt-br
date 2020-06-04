---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: dff7e0c3eb696b9b18f4c4e59240a26c1cb9782c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408530"
---
# <a name="-libpath"></a><span data-ttu-id="c8d3d-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="c8d3d-102">-libpath</span></span>
<span data-ttu-id="c8d3d-103">Especifica o local dos assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8d3d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8d3d-104">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8d3d-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c8d3d-105">Arguments</span></span>  
  
|<span data-ttu-id="c8d3d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="c8d3d-106">Term</span></span>|<span data-ttu-id="c8d3d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="c8d3d-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="c8d3d-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-108">Required.</span></span> <span data-ttu-id="c8d3d-109">Lista delimitada por ponto-e-vírgula de diretórios para o compilador examinar se um assembly referenciado não for encontrado no diretório de trabalho atual (o diretório do qual você está invocando o compilador) ou o diretório do sistema do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="c8d3d-110">Se o nome do diretório contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="c8d3d-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8d3d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8d3d-111">Remarks</span></span>  
 <span data-ttu-id="c8d3d-112">A `-libpath` opção especifica o local dos assemblies referenciados pela opção [-Reference](reference.md) .</span><span class="sxs-lookup"><span data-stu-id="c8d3d-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>  
  
 <span data-ttu-id="c8d3d-113">O compilador pesquisa referências de assembly que não são totalmente qualificadas na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="c8d3d-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="c8d3d-114">Diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-114">Current working directory.</span></span> <span data-ttu-id="c8d3d-115">Esse é o diretório do qual o compilador é invocado.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="c8d3d-116">O diretório de sistema do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="c8d3d-117">Diretórios especificados por `-libpath` .</span><span class="sxs-lookup"><span data-stu-id="c8d3d-117">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="c8d3d-118">Diretórios especificados pela variável de ambiente LIB.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="c8d3d-119">A `-libpath` opção é aditiva; especificá-la mais de uma vez para todos os valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="c8d3d-120">Use `-reference` para especificar uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="c8d3d-121">Para Set-LIBPATH no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8d3d-121">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c8d3d-122">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c8d3d-123">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c8d3d-124">2. Clique na guia **referências** .</span><span class="sxs-lookup"><span data-stu-id="c8d3d-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="c8d3d-125">3. Clique no botão **Reference Paths...** .</span><span class="sxs-lookup"><span data-stu-id="c8d3d-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="c8d3d-126">4. na caixa de diálogo **caminhos de referência** , digite o nome do diretório na caixa **pasta:** .</span><span class="sxs-lookup"><span data-stu-id="c8d3d-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="c8d3d-127">5. clique em **Adicionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c8d3d-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8d3d-128">Example</span></span>  
 <span data-ttu-id="c8d3d-129">O código a seguir é compilado `T2.vb` para criar um arquivo. exe.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="c8d3d-130">O compilador procura no diretório de trabalho, no diretório raiz da unidade C:, e no novo diretório assemblies da unidade C: para referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="c8d3d-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8d3d-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8d3d-131">See also</span></span>

- [<span data-ttu-id="c8d3d-132">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="c8d3d-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="c8d3d-133">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8d3d-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c8d3d-134">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8d3d-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
