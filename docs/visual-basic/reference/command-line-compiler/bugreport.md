---
title: -bugreport
ms.date: 03/08/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 766a4252fd77be95e2641239cba53a4d90e0cb1d
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-bugreport"></a><span data-ttu-id="e743c-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="e743c-102">-bugreport</span></span>
<span data-ttu-id="e743c-103">Cria um arquivo que você pode usar ao arquivo um relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="e743c-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e743c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e743c-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e743c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e743c-105">Arguments</span></span>  
  
|<span data-ttu-id="e743c-106">Termo</span><span class="sxs-lookup"><span data-stu-id="e743c-106">Term</span></span>|<span data-ttu-id="e743c-107">Definição</span><span class="sxs-lookup"><span data-stu-id="e743c-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="e743c-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e743c-108">Required.</span></span> <span data-ttu-id="e743c-109">O nome do arquivo que conterá o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="e743c-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="e743c-110">Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="e743c-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e743c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e743c-111">Remarks</span></span>  
 <span data-ttu-id="e743c-112">As informações a seguir são adicionadas ao `file`:</span><span class="sxs-lookup"><span data-stu-id="e743c-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="e743c-113">Uma cópia de todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="e743c-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="e743c-114">Uma lista das opções de compilador usado na compilação.</span><span class="sxs-lookup"><span data-stu-id="e743c-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="e743c-115">Informações de versão sobre o compilador, o common language runtime e o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e743c-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="e743c-116">Saída do compilador, se houver.</span><span class="sxs-lookup"><span data-stu-id="e743c-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="e743c-117">Uma descrição do problema para o qual você será solicitado.</span><span class="sxs-lookup"><span data-stu-id="e743c-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="e743c-118">Uma descrição de como você acha que o problema deve ser corrigida, o que é solicitada.</span><span class="sxs-lookup"><span data-stu-id="e743c-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="e743c-119">Como uma cópia de todos os arquivos de código-fonte está incluída no `file`, talvez você queira reproduzir o defeito de código (suspeita) no programa mais curto possível.</span><span class="sxs-lookup"><span data-stu-id="e743c-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e743c-120">O `-bugreport` opção produz um arquivo que contém informações potencialmente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="e743c-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="e743c-121">Isso inclui a hora atual, a versão do compilador [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] versão, versão do sistema operacional, nome de usuário, os argumentos de linha de comando com a qual o compilador foi executado, todo o código fonte, e o formato binário de qualquer um de assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="e743c-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="e743c-122">Essa opção pode ser acessada, especificando opções de linha de comando no arquivo Web. config para uma compilação do servidor de um [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e743c-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="e743c-123">Para evitar isso, modifique o arquivo Machine. config para impedir os usuários de compilação no servidor.</span><span class="sxs-lookup"><span data-stu-id="e743c-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="e743c-124">Se essa opção é usada com `-errorreport:prompt`, `-errorreport:queue`, ou `-errorreport:send`, e o aplicativo encontra um erro interno do compilador, as informações no `file` é enviada à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="e743c-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="e743c-125">Essas informações ajudam os engenheiros da Microsoft a identificar a causa do erro e pode ajudar a melhorar a próxima versão do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e743c-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="e743c-126">Por padrão, nenhuma informação é enviada à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e743c-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="e743c-127">No entanto, quando você compila um aplicativo usando `-errorreport:queue`, que é habilitado por padrão, o aplicativo obtém seus relatórios de erro.</span><span class="sxs-lookup"><span data-stu-id="e743c-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="e743c-128">Em seguida, quando o administrador do computador fizer logon, o sistema de relatórios de erro exibe uma janela pop-up que permite que o administrador encaminhar à Microsoft relatórios de quaisquer erros que ocorreram desde o logon.</span><span class="sxs-lookup"><span data-stu-id="e743c-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e743c-129">O `/bugreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível apenas quando você compila na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e743c-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e743c-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e743c-130">Example</span></span>  
 <span data-ttu-id="e743c-131">O exemplo a seguir compila `T2.vb` e coloca todas as informações do serviço de relato de erros no arquivo `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="e743c-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e743c-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e743c-132">See Also</span></span>  
 [<span data-ttu-id="e743c-133">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e743c-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e743c-134">-a depuração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e743c-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="e743c-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="e743c-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="e743c-136">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="e743c-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e743c-137">trustLevel elemento para securityPolicy (ASP.NET Settings Schema)</span><span class="sxs-lookup"><span data-stu-id="e743c-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
