---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 0934799853323110e73087ba6d8975c30f84d8f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387706"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="61a85-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61a85-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="61a85-103">Faz com que o compilador não referencie automaticamente as bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="61a85-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61a85-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="61a85-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="61a85-105">Remarks</span></span>  
 <span data-ttu-id="61a85-106">A `-nostdlib` opção remove a referência automática para o assembly System. dll e impede que o compilador Leia o arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="61a85-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="61a85-107">O arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc. exe, faz referência aos assemblies de .NET Framework usados com frequência e importa os `System` `Microsoft.VisualBasic` namespaces e.</span><span class="sxs-lookup"><span data-stu-id="61a85-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61a85-108">Os assemblies mscorlib. dll e Microsoft. VisualBasic. dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="61a85-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61a85-109">A `-nostdlib` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="61a85-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61a85-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61a85-110">Example</span></span>  
 <span data-ttu-id="61a85-111">O código a seguir é compilado `T2.vb` sem referenciar as bibliotecas padrão.</span><span class="sxs-lookup"><span data-stu-id="61a85-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="61a85-112">Você deve definir a `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Empty" para remover o `My` objeto.</span><span class="sxs-lookup"><span data-stu-id="61a85-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="61a85-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="61a85-113">See also</span></span>

- [<span data-ttu-id="61a85-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="61a85-114">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="61a85-115">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61a85-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="61a85-116">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="61a85-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="61a85-117">Como personalizar quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="61a85-117">Customizing Which Objects are Available in My</span></span>](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
