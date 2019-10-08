---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005440"
---
# <a name="-noconfig"></a><span data-ttu-id="d5b0f-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="d5b0f-102">-noconfig</span></span>
<span data-ttu-id="d5b0f-103">Especifica que o compilador não deve referenciar automaticamente os assemblies de .NET Framework usados com frequência ou importar os namespaces `System` e `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5b0f-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="d5b0f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5b0f-105">Remarks</span></span>  
 <span data-ttu-id="d5b0f-106">A opção `-noconfig` informa o compilador para não compilar com o arquivo Vbc. rsp, que está localizado no mesmo diretório que o arquivo Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="d5b0f-107">O arquivo Vbc. rsp faz referência aos assemblies de .NET Framework usados com frequência e importa os namespaces `System` e `Microsoft.VisualBasic`.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="d5b0f-108">O compilador referencia implicitamente o assembly System. dll, a menos que a opção `-nostdlib` seja especificada.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="d5b0f-109">A opção `-nostdlib` informa ao compilador para não compilar com Vbc. rsp ou referenciar automaticamente o assembly System. dll.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5b0f-110">Os assemblies mscorlib. dll e Microsoft. VisualBasic. dll são sempre referenciados.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="d5b0f-111">Você pode modificar o arquivo Vbc. rsp para especificar opções adicionais do compilador que devem ser incluídas em cada compilação do Vbc. exe (exceto ao especificar a opção `-noconfig`).</span><span class="sxs-lookup"><span data-stu-id="d5b0f-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="d5b0f-112">Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="d5b0f-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="d5b0f-113">O compilador processa as opções passadas para o comando `vbc` por último.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="d5b0f-114">Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5b0f-115">A opção `-noconfig` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d5b0f-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b0f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5b0f-116">See also</span></span>

- [<span data-ttu-id="d5b0f-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5b0f-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="d5b0f-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5b0f-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d5b0f-119">Em (Especificar arquivo de resposta)</span><span class="sxs-lookup"><span data-stu-id="d5b0f-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="d5b0f-120">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5b0f-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
