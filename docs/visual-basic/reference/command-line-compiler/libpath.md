---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2be2c460fddf2e8ea4fe1239ec073f208c072d34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="libpath"></a><span data-ttu-id="22fa1-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="22fa1-102">/libpath</span></span>
<span data-ttu-id="22fa1-103">Especifica o local dos assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="22fa1-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22fa1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22fa1-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="22fa1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="22fa1-105">Arguments</span></span>  
  
|<span data-ttu-id="22fa1-106">Termo</span><span class="sxs-lookup"><span data-stu-id="22fa1-106">Term</span></span>|<span data-ttu-id="22fa1-107">Definição</span><span class="sxs-lookup"><span data-stu-id="22fa1-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="22fa1-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="22fa1-108">Required.</span></span> <span data-ttu-id="22fa1-109">Lista separada por ponto-e-vírgula de diretórios para o compilador ver se um assembly referenciado não foi encontrada no diretório de trabalho atual (o diretório do qual você está chamando o compilador) ou o diretório do sistema do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="22fa1-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="22fa1-110">Se o nome do diretório contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="22fa1-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22fa1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="22fa1-111">Remarks</span></span>  
 <span data-ttu-id="22fa1-112">O `/libpath` opção especifica o local dos assemblies referenciados pelo [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção.</span><span class="sxs-lookup"><span data-stu-id="22fa1-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="22fa1-113">O compilador pesquisa referências de assembly que não são totalmente qualificadas na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="22fa1-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="22fa1-114">Diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="22fa1-114">Current working directory.</span></span> <span data-ttu-id="22fa1-115">Esse é o diretório do qual o compilador é invocado.</span><span class="sxs-lookup"><span data-stu-id="22fa1-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="22fa1-116">O diretório de sistema do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="22fa1-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="22fa1-117">Diretórios especificados pelo `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="22fa1-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="22fa1-118">Diretórios especificados pela variável de ambiente LIB.</span><span class="sxs-lookup"><span data-stu-id="22fa1-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="22fa1-119">O `/libpath` opção é aditivas; especificando-mais de uma vez acrescenta a valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="22fa1-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="22fa1-120">Use `/reference` para especificar uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="22fa1-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="22fa1-121">Configurar /libpath no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="22fa1-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="22fa1-122">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="22fa1-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="22fa1-123">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="22fa1-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="22fa1-124">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="22fa1-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="22fa1-125">2.  Clique na guia **Referências**.</span><span class="sxs-lookup"><span data-stu-id="22fa1-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="22fa1-126">3.  Clique o **caminhos de referência...**  botão.</span><span class="sxs-lookup"><span data-stu-id="22fa1-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="22fa1-127">4.  No **caminhos de referência** caixa de diálogo, digite o nome do diretório no **pasta:** caixa.</span><span class="sxs-lookup"><span data-stu-id="22fa1-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="22fa1-128">5.  Clique em **adicionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="22fa1-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="22fa1-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22fa1-129">Example</span></span>  
 <span data-ttu-id="22fa1-130">O código a seguir compila `T2.vb` para criar um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="22fa1-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="22fa1-131">O compilador procura no diretório de trabalho, no diretório raiz da unidade c: e no diretório da unidade c: novos Assemblies referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="22fa1-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="22fa1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22fa1-132">See Also</span></span>  
 [<span data-ttu-id="22fa1-133">Assemblies e o Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="22fa1-133">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="22fa1-134">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="22fa1-134">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="22fa1-135">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="22fa1-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
