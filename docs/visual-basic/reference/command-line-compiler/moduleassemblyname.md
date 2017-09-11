---
title: /moduleassemblyname | Documentos do Microsoft
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
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
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
ms.openlocfilehash: 6852b8a0d9874fd65e93cdd9507fe9b7119ce5b3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="moduleassemblyname"></a><span data-ttu-id="bb25c-102">/moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="bb25c-102">/moduleassemblyname</span></span>
<span data-ttu-id="bb25c-103">Especifica o nome do assembly do qual esse módulo fará parte.</span><span class="sxs-lookup"><span data-stu-id="bb25c-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb25c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb25c-104">Syntax</span></span>  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb25c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bb25c-105">Arguments</span></span>  
  
|<span data-ttu-id="bb25c-106">Termo</span><span class="sxs-lookup"><span data-stu-id="bb25c-106">Term</span></span>|<span data-ttu-id="bb25c-107">Definição</span><span class="sxs-lookup"><span data-stu-id="bb25c-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="bb25c-108">O nome do assembly que este módulo será uma parte.</span><span class="sxs-lookup"><span data-stu-id="bb25c-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb25c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb25c-109">Remarks</span></span>  
 <span data-ttu-id="bb25c-110">O compilador processa o `/moduleassemblyname` somente se opção o `/target:module` opção foi especificada.</span><span class="sxs-lookup"><span data-stu-id="bb25c-110">The compiler processes the `/moduleassemblyname` option only if the `/target:module` option has been specified.</span></span> <span data-ttu-id="bb25c-111">Isso faz com que o compilador crie um módulo.</span><span class="sxs-lookup"><span data-stu-id="bb25c-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="bb25c-112">O módulo criado pelo compilador é válido somente para o conjunto especificado com o `/moduleassemblyname` opção.</span><span class="sxs-lookup"><span data-stu-id="bb25c-112">The module created by the compiler is valid only for the assembly specified with the `/moduleassemblyname` option.</span></span> <span data-ttu-id="bb25c-113">Se você colocar o módulo em um conjunto diferente, ocorrerão erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bb25c-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="bb25c-114">O `/moduleassemblyname` opção é necessária somente quando as seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="bb25c-114">The `/moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="bb25c-115">Um tipo de dados no módulo precisa acessar um `Friend` tipo em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="bb25c-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="bb25c-116">O assembly referenciado concedeu acesso assembly autorizado ao assembly no qual o módulo será criado.</span><span class="sxs-lookup"><span data-stu-id="bb25c-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="bb25c-117">Para obter mais informações sobre como criar um módulo, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="bb25c-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="bb25c-118">Para obter mais informações sobre assemblies amigáveis, consulte [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="bb25c-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb25c-119">O `/moduleassemblyname` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando você compila a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="bb25c-119">The `/moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb25c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb25c-120">See Also</span></span>  
 <span data-ttu-id="bb25c-121">[Como: criar um Assembly de vários arquivos](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span><span class="sxs-lookup"><span data-stu-id="bb25c-121">[How to: Build a Multifile Assembly](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span></span>  
<span data-ttu-id="bb25c-122"> [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="bb25c-122"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="bb25c-123"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="bb25c-123"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="bb25c-124"> [/Main](../../../visual-basic/reference/command-line-compiler/main.md) </span><span class="sxs-lookup"><span data-stu-id="bb25c-124"> [/main](../../../visual-basic/reference/command-line-compiler/main.md) </span></span>  
<span data-ttu-id="bb25c-125"> [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="bb25c-125"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="bb25c-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span><span class="sxs-lookup"><span data-stu-id="bb25c-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span></span>  
<span data-ttu-id="bb25c-127"> [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="bb25c-127"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="bb25c-128"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="bb25c-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="bb25c-129"> [Assemblies Amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span><span class="sxs-lookup"><span data-stu-id="bb25c-129"> [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span></span>
