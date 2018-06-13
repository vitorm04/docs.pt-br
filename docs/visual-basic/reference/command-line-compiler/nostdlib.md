---
title: -/nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764409f13a00f6d8a050bfbdd0f59e537a5ded3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652712"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="e3334-102">-/nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3334-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="e3334-103">Faz com que o compilador não referencie automaticamente as bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="e3334-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3334-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3334-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="e3334-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3334-105">Remarks</span></span>  
 <span data-ttu-id="e3334-106">O `-nostdlib` opção remove a referência automática para o assembly System. dll e impede que o compilador ler o arquivo Vbc.</span><span class="sxs-lookup"><span data-stu-id="e3334-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="e3334-107">O arquivo Vbc.rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe, faz referência a usadas [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies e importa o `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="e3334-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3334-108">Os assemblies mscorlib. dll e Microsoft.VisualBasic.dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="e3334-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3334-109">O `-nostdlib` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e3334-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3334-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3334-110">Example</span></span>  
 <span data-ttu-id="e3334-111">O código a seguir compila `T2.vb` sem fazer referência às bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="e3334-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="e3334-112">Você deve definir o `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Vazio" para remover o `My` objeto.</span><span class="sxs-lookup"><span data-stu-id="e3334-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3334-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3334-113">See Also</span></span>  
 [<span data-ttu-id="e3334-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="e3334-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="e3334-115">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3334-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e3334-116">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3334-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e3334-117">Personalizando quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="e3334-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
