---
title: -/noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650836"
---
# <a name="-noconfig"></a><span data-ttu-id="bbde0-102">-/noconfig</span><span class="sxs-lookup"><span data-stu-id="bbde0-102">-noconfig</span></span>
<span data-ttu-id="bbde0-103">Especifica que o compilador não deve automaticamente referenciar comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies ou importação de `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="bbde0-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbde0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbde0-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="bbde0-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbde0-105">Remarks</span></span>  
 <span data-ttu-id="bbde0-106">O `-noconfig` opção informa ao compilador para não compilar com o arquivo Vbc.rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="bbde0-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="bbde0-107">O arquivo Vbc.rsp referencia comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies e importa o `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="bbde0-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="bbde0-108">O compilador implicitamente referencia o assembly System. dll, a menos que o `-nostdlib` opção é especificada.</span><span class="sxs-lookup"><span data-stu-id="bbde0-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="bbde0-109">O `-nostdlib` opção informa ao compilador para não compilar com Vbc ou referenciar automaticamente o assembly System. dll.</span><span class="sxs-lookup"><span data-stu-id="bbde0-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbde0-110">Os assemblies mscorlib. dll e Microsoft.VisualBasic.dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="bbde0-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="bbde0-111">Você pode modificar o arquivo Vbc.rsp para especificar opções adicionais do compilador que devem ser incluídas em cada compilação Vbc.exe (exceto quando o `-noconfig` opção).</span><span class="sxs-lookup"><span data-stu-id="bbde0-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="bbde0-112">Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="bbde0-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="bbde0-113">O compilador processa as opções passadas para o `vbc` último comando.</span><span class="sxs-lookup"><span data-stu-id="bbde0-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="bbde0-114">Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc.</span><span class="sxs-lookup"><span data-stu-id="bbde0-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbde0-115">O `-noconfig` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bbde0-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbde0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbde0-116">See Also</span></span>  
 [<span data-ttu-id="bbde0-117">-/nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbde0-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [<span data-ttu-id="bbde0-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bbde0-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bbde0-119">Em (Especificar arquivo de resposta)</span><span class="sxs-lookup"><span data-stu-id="bbde0-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [<span data-ttu-id="bbde0-120">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbde0-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
