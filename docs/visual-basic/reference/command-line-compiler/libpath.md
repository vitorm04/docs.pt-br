---
title: /libpath | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7f24dd7707645f45677dcf7009e1adc64afaaa7c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="libpath"></a><span data-ttu-id="8f309-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="8f309-102">/libpath</span></span>
<span data-ttu-id="8f309-103">Especifica o local dos assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="8f309-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f309-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f309-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f309-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8f309-105">Arguments</span></span>  
  
|<span data-ttu-id="8f309-106">Termo</span><span class="sxs-lookup"><span data-stu-id="8f309-106">Term</span></span>|<span data-ttu-id="8f309-107">Definição</span><span class="sxs-lookup"><span data-stu-id="8f309-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="8f309-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8f309-108">Required.</span></span> <span data-ttu-id="8f309-109">Lista delimitada por ponto e vírgula de diretórios para o compilador ver se um assembly referenciado não foi encontrada no diretório de trabalho atual (o diretório do qual você está chamando o compilador) ou o diretório do sistema do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="8f309-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="8f309-110">Se o nome do diretório contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="8f309-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f309-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f309-111">Remarks</span></span>  
 <span data-ttu-id="8f309-112">O `/libpath` opção especifica o local dos assemblies referenciados pelo [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção.</span><span class="sxs-lookup"><span data-stu-id="8f309-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="8f309-113">O compilador procura por referências de assembly que não são totalmente qualificadas na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="8f309-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="8f309-114">Diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="8f309-114">Current working directory.</span></span> <span data-ttu-id="8f309-115">Este é o diretório do qual o compilador é chamado.</span><span class="sxs-lookup"><span data-stu-id="8f309-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="8f309-116">Diretório do common language runtime system.</span><span class="sxs-lookup"><span data-stu-id="8f309-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="8f309-117">Diretórios especificados pela `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="8f309-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="8f309-118">Diretórios especificados pela variável de ambiente LIB.</span><span class="sxs-lookup"><span data-stu-id="8f309-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="8f309-119">O `/libpath` opção é aditiva; especificando mais de uma vez acrescenta a valores anteriores.</span><span class="sxs-lookup"><span data-stu-id="8f309-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="8f309-120">Use `/reference` para especificar uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="8f309-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="8f309-121">Configurar /libpath no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="8f309-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8f309-122">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="8f309-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8f309-123">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8f309-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="8f309-124">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="8f309-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="8f309-125">2.  Clique o **referências** guia.</span><span class="sxs-lookup"><span data-stu-id="8f309-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="8f309-126">3.  Clique a **caminhos de referência... ** botão.</span><span class="sxs-lookup"><span data-stu-id="8f309-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="8f309-127">4.  No **caminhos de referência** caixa de diálogo, digite o nome do diretório no **pasta:** caixa.</span><span class="sxs-lookup"><span data-stu-id="8f309-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="8f309-128">5.  Clique em **adicionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="8f309-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8f309-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f309-129">Example</span></span>  
 <span data-ttu-id="8f309-130">O seguinte código compila `T2.vb` para criar um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="8f309-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="8f309-131">O compilador procura no diretório de trabalho, no diretório raiz da unidade c e no diretório da unidade c novos Assemblies de referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="8f309-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f309-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f309-132">See Also</span></span>  
 <span data-ttu-id="8f309-133">[Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="8f309-133">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="8f309-134"> [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="8f309-134"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="8f309-135"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="8f309-135"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
