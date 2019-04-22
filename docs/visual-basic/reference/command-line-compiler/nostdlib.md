---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4f3dc61a6e78b0fb2135d4132c53e7efc22447a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814958"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="4c022-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c022-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="4c022-103">Faz com que o compilador não referencie automaticamente as bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="4c022-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c022-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c022-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="4c022-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c022-105">Remarks</span></span>  
 <span data-ttu-id="4c022-106">O `-nostdlib` opção remove a referência automática para o assembly System. dll e impede que o compilador lendo o arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="4c022-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="4c022-107">O arquivo Vbc. rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe, faz referência os comumente usados [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies e importações a `System` e `Microsoft.VisualBasic` namespaces.</span><span class="sxs-lookup"><span data-stu-id="4c022-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c022-108">Os assemblies de mscorlib. dll e VisualBasic são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="4c022-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c022-109">O `-nostdlib` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="4c022-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c022-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c022-110">Example</span></span>  
 <span data-ttu-id="4c022-111">O seguinte código compila `T2.vb` sem fazer referência às bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="4c022-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="4c022-112">Você deve definir a `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Vazio" para remover o `My` objeto.</span><span class="sxs-lookup"><span data-stu-id="4c022-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c022-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c022-113">See also</span></span>

- [<span data-ttu-id="4c022-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="4c022-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="4c022-115">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c022-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4c022-116">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c022-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="4c022-117">Personalizando quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="4c022-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
