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
ms.openlocfilehash: 21efca701eb16898dd291d73bf0431641ba75d12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788876"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="2ddd7-102">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ddd7-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="2ddd7-103">Faz com que o compilador disponibilizar informações de tipo nos assemblies especificados para o projeto que você está compilando.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ddd7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ddd7-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ddd7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ddd7-105">Arguments</span></span>  
  
|<span data-ttu-id="2ddd7-106">Termo</span><span class="sxs-lookup"><span data-stu-id="2ddd7-106">Term</span></span>|<span data-ttu-id="2ddd7-107">Definição</span><span class="sxs-lookup"><span data-stu-id="2ddd7-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="2ddd7-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-108">Required.</span></span> <span data-ttu-id="2ddd7-109">Lista delimitada por vírgulas de nomes de arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2ddd7-110">Se o nome do arquivo contém um espaço, coloque o nome entre aspas.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ddd7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ddd7-111">Remarks</span></span>  
 <span data-ttu-id="2ddd7-112">Os arquivos que você importa devem conter metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="2ddd7-113">Somente os tipos públicos são visíveis fora do assembly.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="2ddd7-114">O [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opção importa os metadados de um módulo.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="2ddd7-115">Se você fizer referência a um assembly (Assembly A) que se faz referência a outro assembly (Assembly B), você precisa referenciar o Assembly B se:</span><span class="sxs-lookup"><span data-stu-id="2ddd7-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="2ddd7-116">Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="2ddd7-117">Um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B é invocado.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2ddd7-118">Use [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório em que uma ou mais das suas referências do assembly estão localizado.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="2ddd7-119">Para o compilador reconheça um tipo em um assembly (não um módulo), ele deve ser forçado a resolver o tipo.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="2ddd7-120">Um exemplo de como você pode fazer isso é definir uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="2ddd7-121">Outras maneiras de estão disponíveis para resolver nomes de tipo em um assembly para o compilador.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="2ddd7-122">Por exemplo, se você herdar de um tipo em um assembly, o nome do tipo, em seguida, se tornam conhecido para o compilador.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="2ddd7-123">O arquivo de resposta Vbc, que as referências usadas comumente [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="2ddd7-124">Use `-noconfig` se você não quiser que o compilador use Vbc.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="2ddd7-125">A forma abreviada de `-reference` é `/r`.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ddd7-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ddd7-126">Example</span></span>  
 <span data-ttu-id="2ddd7-127">O comando a seguir compila o arquivo de origem `Input.vb` e fazer referência a assemblies `Metad1.dll` e `Metad2.dll` para produzir `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ddd7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ddd7-128">See also</span></span>

- [<span data-ttu-id="2ddd7-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ddd7-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2ddd7-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2ddd7-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="2ddd7-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ddd7-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="2ddd7-132">Público</span><span class="sxs-lookup"><span data-stu-id="2ddd7-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="2ddd7-133">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ddd7-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
