---
title: /noconfig | Documentos do Microsoft
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
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
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
ms.openlocfilehash: fe3271e4a119e0c40370a7351bb39188f4d1c8ef
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="noconfig"></a><span data-ttu-id="b2dbf-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="b2dbf-102">/noconfig</span></span>
<span data-ttu-id="b2dbf-103">Especifica que o compilador não deve automaticamente referenciar comumente usados [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies ou importar a `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2dbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2dbf-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2dbf-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2dbf-105">Remarks</span></span>  
 <span data-ttu-id="b2dbf-106">O `/noconfig` opção informa o compilador não deve compilar com o arquivo Vbc. exe, que está localizado no mesmo diretório que o arquivo Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="b2dbf-107">O arquivo Vbc. rsp faz referência comumente usados [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies e importa o `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="b2dbf-108">O compilador implicitamente referencia o assembly System. dll, a menos que o `/nostdlib` opção é especificada.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="b2dbf-109">O `/nostdlib` opção informa o compilador não deve compilar com Vbc ou referenciar automaticamente o assembly System. dll.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2dbf-110">Os assemblies mscorlib. dll e Microsoft.VisualBasic.dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="b2dbf-111">Você pode modificar o arquivo Vbc. rsp para especificar opções adicionais do compilador que devem ser incluídas em cada compilação Vbc.exe (exceto quando o `/noconfig` opção).</span><span class="sxs-lookup"><span data-stu-id="b2dbf-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="b2dbf-112">Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="b2dbf-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="b2dbf-113">O compilador processa as opções passadas para o `vbc` último comando.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="b2dbf-114">Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2dbf-115">O `/noconfig` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b2dbf-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2dbf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2dbf-116">See Also</span></span>  
 <span data-ttu-id="b2dbf-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span><span class="sxs-lookup"><span data-stu-id="b2dbf-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span></span>  
<span data-ttu-id="b2dbf-118"> [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2dbf-118"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b2dbf-119"> [@ (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span><span class="sxs-lookup"><span data-stu-id="b2dbf-119"> [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span></span>  
<span data-ttu-id="b2dbf-120"> [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span><span class="sxs-lookup"><span data-stu-id="b2dbf-120"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span></span>
