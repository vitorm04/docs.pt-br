---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 819505df2e7d5f93302f9ed601de856e36ed7124
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005408"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="3f217-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f217-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="3f217-103">Faz com que o compilador não referencie automaticamente as bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="3f217-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f217-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f217-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f217-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f217-105">Remarks</span></span>  
 <span data-ttu-id="3f217-106">A opção `-nostdlib` remove a referência automática para o assembly System. dll e impede que o compilador Leia o arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="3f217-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="3f217-107">O arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc. exe, faz referência aos assemblies de .NET Framework usados com frequência e importa os namespaces `System` e `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="3f217-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f217-108">Os assemblies mscorlib. dll e Microsoft. VisualBasic. dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="3f217-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f217-109">A opção `-nostdlib` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3f217-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f217-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f217-110">Example</span></span>  
 <span data-ttu-id="3f217-111">O código a seguir compila `T2.vb` sem fazer referência às bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="3f217-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="3f217-112">Você deve definir a constante de compilação condicional `_MYTYPE` para a cadeia de caracteres "Empty" para remover o objeto `My`.</span><span class="sxs-lookup"><span data-stu-id="3f217-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f217-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f217-113">See also</span></span>

- [<span data-ttu-id="3f217-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="3f217-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="3f217-115">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f217-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3f217-116">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f217-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="3f217-117">Personalizando quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="3f217-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
