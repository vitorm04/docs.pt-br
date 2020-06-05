---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401934"
---
# <a name="-noconfig"></a><span data-ttu-id="6791a-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="6791a-102">-noconfig</span></span>
<span data-ttu-id="6791a-103">Especifica que o compilador não deve referenciar automaticamente os assemblies de .NET Framework usados com frequência ou importar os `System` `Microsoft.VisualBasic` namespaces e.</span><span class="sxs-lookup"><span data-stu-id="6791a-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6791a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6791a-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="6791a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="6791a-105">Remarks</span></span>  
 <span data-ttu-id="6791a-106">A `-noconfig` opção informa o compilador para não compilar com o arquivo Vbc. rsp, que está localizado no mesmo diretório que o arquivo Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="6791a-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="6791a-107">O arquivo Vbc. rsp faz referência aos assemblies de .NET Framework usados com frequência e importa os `System` `Microsoft.VisualBasic` namespaces e.</span><span class="sxs-lookup"><span data-stu-id="6791a-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="6791a-108">O compilador referencia implicitamente o assembly System. dll, a menos que a `-nostdlib` opção seja especificada.</span><span class="sxs-lookup"><span data-stu-id="6791a-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="6791a-109">A `-nostdlib` opção informa o compilador para não compilar com Vbc. rsp ou referenciar automaticamente o assembly System. dll.</span><span class="sxs-lookup"><span data-stu-id="6791a-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6791a-110">Os assemblies mscorlib. dll e Microsoft. VisualBasic. dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="6791a-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="6791a-111">Você pode modificar o arquivo Vbc. rsp para especificar opções adicionais do compilador que devem ser incluídas em cada compilação do Vbc. exe (exceto ao especificar a `-noconfig` opção).</span><span class="sxs-lookup"><span data-stu-id="6791a-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="6791a-112">Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="6791a-112">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="6791a-113">O compilador processa as opções passadas para o `vbc` comando por último.</span><span class="sxs-lookup"><span data-stu-id="6791a-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="6791a-114">Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="6791a-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6791a-115">A `-noconfig` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6791a-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6791a-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6791a-116">See also</span></span>

- [<span data-ttu-id="6791a-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6791a-117">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="6791a-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6791a-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6791a-119">@ (especificar arquivo de resposta)</span><span class="sxs-lookup"><span data-stu-id="6791a-119">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="6791a-120">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6791a-120">-reference (Visual Basic)</span></span>](reference.md)
