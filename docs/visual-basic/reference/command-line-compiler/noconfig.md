---
title: /noconfig
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d13ccf0168027f4560b980c41e2a001ff503fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig"></a><span data-ttu-id="aed1f-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="aed1f-102">/noconfig</span></span>
<span data-ttu-id="aed1f-103">Especifica que o compilador não deve automaticamente referenciar comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies ou importação de `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="aed1f-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed1f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aed1f-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="aed1f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="aed1f-105">Remarks</span></span>  
 <span data-ttu-id="aed1f-106">O `/noconfig` opção informa ao compilador para não compilar com o arquivo Vbc.rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="aed1f-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="aed1f-107">O arquivo Vbc.rsp referencia comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies e importa o `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="aed1f-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="aed1f-108">O compilador implicitamente referencia o assembly System. dll, a menos que o `/nostdlib` opção é especificada.</span><span class="sxs-lookup"><span data-stu-id="aed1f-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="aed1f-109">O `/nostdlib` opção informa ao compilador para não compilar com Vbc ou referenciar automaticamente o assembly System. dll.</span><span class="sxs-lookup"><span data-stu-id="aed1f-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aed1f-110">Os assemblies mscorlib. dll e Microsoft.VisualBasic.dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="aed1f-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="aed1f-111">Você pode modificar o arquivo Vbc.rsp para especificar opções adicionais do compilador que devem ser incluídas em cada compilação Vbc.exe (exceto quando o `/noconfig` opção).</span><span class="sxs-lookup"><span data-stu-id="aed1f-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="aed1f-112">Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="aed1f-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="aed1f-113">O compilador processa as opções passadas para o `vbc` último comando.</span><span class="sxs-lookup"><span data-stu-id="aed1f-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="aed1f-114">Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc.</span><span class="sxs-lookup"><span data-stu-id="aed1f-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aed1f-115">O `/noconfig` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="aed1f-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed1f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aed1f-116">See Also</span></span>  
 [<span data-ttu-id="aed1f-117">/nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aed1f-117">/nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [<span data-ttu-id="aed1f-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aed1f-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="aed1f-119">Em (Especificar arquivo de resposta)</span><span class="sxs-lookup"><span data-stu-id="aed1f-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [<span data-ttu-id="aed1f-120">/Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aed1f-120">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
