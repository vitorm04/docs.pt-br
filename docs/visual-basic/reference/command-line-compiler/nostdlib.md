---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 19a70e500f6b75fd003bdb798f242cddb3926935
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964359"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="ec51f-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec51f-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="ec51f-103">Faz com que o compilador não referencie automaticamente as bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="ec51f-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec51f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec51f-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="ec51f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec51f-105">Remarks</span></span>  
 <span data-ttu-id="ec51f-106">A `-nostdlib` opção remove a referência automática para o assembly System. dll e impede que o compilador Leia o arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="ec51f-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="ec51f-107">O arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc. exe, faz referência aos assemblies de .NET Framework usados com frequência e importa os `System` namespaces e `Microsoft.VisualBasic` .</span><span class="sxs-lookup"><span data-stu-id="ec51f-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec51f-108">Os assemblies mscorlib. dll e Microsoft. VisualBasic. dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="ec51f-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec51f-109">A `-nostdlib` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ec51f-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec51f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec51f-110">Example</span></span>  
 <span data-ttu-id="ec51f-111">O código a seguir é compilado `T2.vb` sem referenciar as bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="ec51f-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="ec51f-112">Você deve definir a `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Empty" para `My` remover o objeto.</span><span class="sxs-lookup"><span data-stu-id="ec51f-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec51f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec51f-113">See also</span></span>

- [<span data-ttu-id="ec51f-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="ec51f-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="ec51f-115">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec51f-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ec51f-116">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec51f-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ec51f-117">Personalizando quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="ec51f-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
