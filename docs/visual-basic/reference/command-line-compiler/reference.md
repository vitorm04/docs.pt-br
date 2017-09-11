---
title: /Reference (Visual Basic) | Documentos do Microsoft
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
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
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
ms.openlocfilehash: 6870c0b6008124bad18f8eba9207d06e085f2307
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="reference-visual-basic"></a><span data-ttu-id="8cb3d-102">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cb3d-102">/reference (Visual Basic)</span></span>
<span data-ttu-id="8cb3d-103">Faz com que o compilador torne informações de tipo nas montagens especificadas disponíveis para o projeto que você está compilando atualmente.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb3d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8cb3d-104">Syntax</span></span>  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="8cb3d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8cb3d-105">Arguments</span></span>  
  
|<span data-ttu-id="8cb3d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="8cb3d-106">Term</span></span>|<span data-ttu-id="8cb3d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="8cb3d-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="8cb3d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-108">Required.</span></span> <span data-ttu-id="8cb3d-109">Lista delimitada por vírgulas de nomes de arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="8cb3d-110">Se o nome do arquivo contém um espaço, coloque o nome entre aspas.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cb3d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8cb3d-111">Remarks</span></span>  
 <span data-ttu-id="8cb3d-112">Os arquivos que você importar devem conter metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="8cb3d-113">Apenas tipos públicos são visíveis fora do assembly.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="8cb3d-114">O [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opção importa os metadados de um módulo.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="8cb3d-115">Se você referenciar um assembly (Assembly A) que se faz referência a outro assembly (Assembly B), você precisa referenciar o Assembly B se:</span><span class="sxs-lookup"><span data-stu-id="8cb3d-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="8cb3d-116">Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="8cb3d-117">Um campo, propriedade, evento ou método que possui um tipo de parâmetro ou tipo de retorno do Assembly B é chamado.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="8cb3d-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório no qual uma ou mais das suas referências do assembly estão localizado.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="8cb3d-119">Para o compilador reconhecer um tipo em um assembly (não um módulo), ele deve ser forçado a decidir o tipo.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="8cb3d-120">Um exemplo de como você pode fazer isso é definir uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="8cb3d-121">Outras maneiras estão disponíveis para resolver nomes de tipo em um assembly para o compilador.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="8cb3d-122">Por exemplo, se você herdar de um tipo em um assembly, o nome do tipo, em seguida, torna-se conhecido para o compilador.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="8cb3d-123">O arquivo de resposta Vbc, que normalmente usadas referências [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies, é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="8cb3d-124">Use `/noconfig` se não quiser que o compilador use Vbc.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-124">Use `/noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="8cb3d-125">A forma abreviada do `/reference` é `/r`.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-125">The short form of `/reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cb3d-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8cb3d-126">Example</span></span>  
 <span data-ttu-id="8cb3d-127">O seguinte código compila o arquivo fonte`nput.vb` e assemblies de referência de M`etad1.dll` e M`etad2.dll` para produzir O`ut.exe`.</span><span class="sxs-lookup"><span data-stu-id="8cb3d-127">The following code compiles source file I`nput.vb` and reference assemblies from M`etad1.dll` and M`etad2.dll` to produce O`ut.exe`.</span></span>  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cb3d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cb3d-128">See Also</span></span>  
 <span data-ttu-id="8cb3d-129">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="8cb3d-129">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="8cb3d-130"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="8cb3d-130"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="8cb3d-131"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="8cb3d-131"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="8cb3d-132"> [Público](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="8cb3d-132"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="8cb3d-133"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="8cb3d-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
