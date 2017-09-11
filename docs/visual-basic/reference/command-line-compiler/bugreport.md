---
title: /bugreport | Documentos do Microsoft
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
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
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
ms.openlocfilehash: b959ef7958cffbbb31f3907eaf8749ca93ac538d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="bugreport"></a><span data-ttu-id="89a99-102">/bugreport</span><span class="sxs-lookup"><span data-stu-id="89a99-102">/bugreport</span></span>
<span data-ttu-id="89a99-103">Cria um arquivo que você pode usar quando o arquivo de um relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="89a99-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89a99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89a99-104">Syntax</span></span>  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="89a99-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="89a99-105">Arguments</span></span>  
  
|<span data-ttu-id="89a99-106">Termo</span><span class="sxs-lookup"><span data-stu-id="89a99-106">Term</span></span>|<span data-ttu-id="89a99-107">Definição</span><span class="sxs-lookup"><span data-stu-id="89a99-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="89a99-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="89a99-108">Required.</span></span> <span data-ttu-id="89a99-109">O nome do arquivo que conterá o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="89a99-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="89a99-110">Coloque o nome do arquivo entre aspas ("") se o nome contém um espaço.</span><span class="sxs-lookup"><span data-stu-id="89a99-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89a99-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="89a99-111">Remarks</span></span>  
 <span data-ttu-id="89a99-112">As informações a seguir são adicionadas ao `file`:</span><span class="sxs-lookup"><span data-stu-id="89a99-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="89a99-113">Uma cópia de todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="89a99-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="89a99-114">Uma lista das opções de compilador usado na compilação.</span><span class="sxs-lookup"><span data-stu-id="89a99-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="89a99-115">Informações de versão sobre o compilador, o common language runtime e o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="89a99-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="89a99-116">Compilador de saída, se houver.</span><span class="sxs-lookup"><span data-stu-id="89a99-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="89a99-117">Uma descrição do problema, qual é solicitada.</span><span class="sxs-lookup"><span data-stu-id="89a99-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="89a99-118">Uma descrição de como você acha que o problema deve ser corrigida, o que é solicitada.</span><span class="sxs-lookup"><span data-stu-id="89a99-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="89a99-119">Como uma cópia de todos os arquivos de código-fonte está incluída no `file`, talvez você queira reproduzir o defeito do código (suspeito) no programa mais curto possível.</span><span class="sxs-lookup"><span data-stu-id="89a99-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89a99-120">O `/bugreport` opção produz um arquivo que contém informações potencialmente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="89a99-120">The `/bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="89a99-121">Isso inclui a hora atual, a versão do compilador, [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] versão, versão do sistema operacional, nome de usuário, os argumentos de linha de comando com que o compilador foi executado, todo o código fonte, e o formulário binário de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="89a99-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="89a99-122">Essa opção pode ser acessada, especificando opções de linha de comando no arquivo Web. config para uma compilação do servidor de um [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89a99-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] application.</span></span> <span data-ttu-id="89a99-123">Para evitar isso, modifique o arquivo Machine. config para impedir os usuários de compilação no servidor.</span><span class="sxs-lookup"><span data-stu-id="89a99-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="89a99-124">Se essa opção for usada com `/errorreport:prompt`, `/errorreport:queue`, ou `/errorreport:send`, e o aplicativo encontra um erro interno do compilador, as informações no `file` é enviada à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="89a99-124">If this option is used with `/errorreport:prompt`, `/errorreport:queue`, or `/errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="89a99-125">Essas informações ajudarão os engenheiros da Microsoft identificar a causa do erro e podem ajudar a melhorar a próxima versão do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="89a99-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="89a99-126">Por padrão, nenhuma informação é enviada à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="89a99-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="89a99-127">No entanto, quando você compila um aplicativo usando `/errorreport:queue`, que é ativado por padrão, o aplicativo obtém seus relatórios de erros.</span><span class="sxs-lookup"><span data-stu-id="89a99-127">However, when you compile an application by using `/errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="89a99-128">Em seguida, quando o administrador do computador faz logon, o sistema de relatórios de erro exibe uma janela pop-up que permite que o administrador encaminhar à Microsoft relatórios de quaisquer erros que ocorreram desde o logon.</span><span class="sxs-lookup"><span data-stu-id="89a99-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89a99-129">O `/bugreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente quando você compilar na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="89a99-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89a99-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89a99-130">Example</span></span>  
 <span data-ttu-id="89a99-131">O exemplo a seguir compila `T2.vb` e coloca todas as informações de relatório de bugs no arquivo `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="89a99-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="89a99-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89a99-132">See Also</span></span>  
 <span data-ttu-id="89a99-133">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="89a99-133">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="89a99-134"> [/Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span><span class="sxs-lookup"><span data-stu-id="89a99-134"> [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span></span>  
<span data-ttu-id="89a99-135"> [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md) </span><span class="sxs-lookup"><span data-stu-id="89a99-135"> [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md) </span></span>  
<span data-ttu-id="89a99-136"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="89a99-136"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="89a99-137"> [trustLevel elemento para securityPolicy (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)</span><span class="sxs-lookup"><span data-stu-id="89a99-137"> [trustLevel Element for securityPolicy (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)</span></span>
