---
title: -referência (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb5d3b4c50a9c22880bdcc8406835cf51481e3cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654363"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="2af9b-102">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2af9b-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="2af9b-103">Faz com que o compilador disponibilizar informações de tipo no assembly especificado para o projeto que você está compilando atualmente.</span><span class="sxs-lookup"><span data-stu-id="2af9b-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2af9b-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2af9b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2af9b-105">Arguments</span></span>  
  
|<span data-ttu-id="2af9b-106">Termo</span><span class="sxs-lookup"><span data-stu-id="2af9b-106">Term</span></span>|<span data-ttu-id="2af9b-107">Definição</span><span class="sxs-lookup"><span data-stu-id="2af9b-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="2af9b-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2af9b-108">Required.</span></span> <span data-ttu-id="2af9b-109">Lista delimitada por vírgulas de nomes de arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="2af9b-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2af9b-110">Se o nome do arquivo contém um espaço, coloque o nome entre aspas.</span><span class="sxs-lookup"><span data-stu-id="2af9b-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2af9b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2af9b-111">Remarks</span></span>  
 <span data-ttu-id="2af9b-112">Os arquivos que você importa devem conter metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="2af9b-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="2af9b-113">Somente os tipos públicos são visíveis fora do assembly.</span><span class="sxs-lookup"><span data-stu-id="2af9b-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="2af9b-114">O [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opção importa os metadados de um módulo.</span><span class="sxs-lookup"><span data-stu-id="2af9b-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="2af9b-115">Se você fizer referência a um assembly (Assembly A) que se faz referência a outro assembly (Assembly B), você precisa referenciar o Assembly B se:</span><span class="sxs-lookup"><span data-stu-id="2af9b-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="2af9b-116">Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="2af9b-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="2af9b-117">Um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B é invocado.</span><span class="sxs-lookup"><span data-stu-id="2af9b-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2af9b-118">Use [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório em que uma ou mais das suas referências do assembly estão localizado.</span><span class="sxs-lookup"><span data-stu-id="2af9b-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="2af9b-119">Para o compilador reconheça um tipo em um assembly (não um módulo), ele deve ser forçado para resolver o tipo.</span><span class="sxs-lookup"><span data-stu-id="2af9b-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="2af9b-120">Um exemplo de como você pode fazer isso é definir uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="2af9b-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="2af9b-121">Outras maneiras estão disponíveis para resolver nomes de tipo em um assembly para o compilador.</span><span class="sxs-lookup"><span data-stu-id="2af9b-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="2af9b-122">Por exemplo, se você herdar de um tipo em um assembly, o nome do tipo, em seguida, torna-se conhecido para o compilador.</span><span class="sxs-lookup"><span data-stu-id="2af9b-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="2af9b-123">O arquivo de resposta de Vbc referências usadas [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="2af9b-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="2af9b-124">Use `-noconfig` se você não quiser que o compilador use o Vbc.</span><span class="sxs-lookup"><span data-stu-id="2af9b-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="2af9b-125">A forma abreviada de `-reference` é `/r`.</span><span class="sxs-lookup"><span data-stu-id="2af9b-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2af9b-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2af9b-126">Example</span></span>  
 <span data-ttu-id="2af9b-127">O comando a seguir compila o arquivo de origem `Input.vb` e fazer referência a assemblies de `Metad1.dll` e `Metad2.dll` para produzir `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="2af9b-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2af9b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2af9b-128">See Also</span></span>  
 [<span data-ttu-id="2af9b-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2af9b-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2af9b-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2af9b-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="2af9b-131">-alvo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2af9b-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="2af9b-132">Público</span><span class="sxs-lookup"><span data-stu-id="2af9b-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="2af9b-133">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="2af9b-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
