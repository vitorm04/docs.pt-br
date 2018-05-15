---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5044bc0093960fdf6b063450d8d3a57575ff07c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-libpath"></a><span data-ttu-id="1da2d-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="1da2d-102">-libpath</span></span>
<span data-ttu-id="1da2d-103">Especifica o local dos assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="1da2d-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da2d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1da2d-104">Syntax</span></span>  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="1da2d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1da2d-105">Arguments</span></span>  
  
|<span data-ttu-id="1da2d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="1da2d-106">Term</span></span>|<span data-ttu-id="1da2d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="1da2d-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="1da2d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1da2d-108">Required.</span></span> <span data-ttu-id="1da2d-109">Lista separada por ponto-e-vírgula de diretórios para o compilador ver se um assembly referenciado não foi encontrada no diretório de trabalho atual (o diretório do qual você está chamando o compilador) ou o diretório do sistema do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1da2d-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="1da2d-110">Se o nome do diretório contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="1da2d-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1da2d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1da2d-111">Remarks</span></span>  
 <span data-ttu-id="1da2d-112">O `-libpath` opção especifica o local dos assemblies referenciados pelo [-referência](../../../visual-basic/reference/command-line-compiler/reference.md) opção.</span><span class="sxs-lookup"><span data-stu-id="1da2d-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="1da2d-113">O compilador pesquisa referências de assembly que não são totalmente qualificadas na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="1da2d-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="1da2d-114">Diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="1da2d-114">Current working directory.</span></span> <span data-ttu-id="1da2d-115">Esse é o diretório do qual o compilador é invocado.</span><span class="sxs-lookup"><span data-stu-id="1da2d-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="1da2d-116">O diretório de sistema do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="1da2d-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="1da2d-117">Diretórios especificados pelo `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="1da2d-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="1da2d-118">Diretórios especificados pela variável de ambiente LIB.</span><span class="sxs-lookup"><span data-stu-id="1da2d-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="1da2d-119">O `-libpath` opção é aditivas; especificando-mais de uma vez acrescenta a valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="1da2d-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="1da2d-120">Use `-reference` para especificar uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="1da2d-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="1da2d-121">Configurar /libpath no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="1da2d-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1da2d-122">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="1da2d-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1da2d-123">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="1da2d-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1da2d-124">2.  Clique na guia **Referências**.</span><span class="sxs-lookup"><span data-stu-id="1da2d-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="1da2d-125">3.  Clique o **caminhos de referência...**  botão.</span><span class="sxs-lookup"><span data-stu-id="1da2d-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="1da2d-126">4.  No **caminhos de referência** caixa de diálogo, digite o nome do diretório no **pasta:** caixa.</span><span class="sxs-lookup"><span data-stu-id="1da2d-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="1da2d-127">5.  Clique em **adicionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="1da2d-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1da2d-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1da2d-128">Example</span></span>  
 <span data-ttu-id="1da2d-129">O código a seguir compila `T2.vb` para criar um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="1da2d-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="1da2d-130">O compilador procura no diretório de trabalho, no diretório raiz da unidade c: e no diretório da unidade c: novos Assemblies referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="1da2d-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1da2d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1da2d-131">See Also</span></span>  
 [<span data-ttu-id="1da2d-132">Assemblies e o Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="1da2d-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="1da2d-133">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1da2d-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1da2d-134">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="1da2d-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
