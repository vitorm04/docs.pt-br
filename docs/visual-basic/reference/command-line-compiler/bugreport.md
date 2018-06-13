---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 0383a5e369ee4a8146764c13b2f12f48ebe52190
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653488"
---
# <a name="-bugreport"></a><span data-ttu-id="181b5-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="181b5-102">-bugreport</span></span>
<span data-ttu-id="181b5-103">Cria um arquivo que você pode usar ao arquivo um relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="181b5-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="181b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="181b5-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="181b5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="181b5-105">Arguments</span></span>  
  
|<span data-ttu-id="181b5-106">Termo</span><span class="sxs-lookup"><span data-stu-id="181b5-106">Term</span></span>|<span data-ttu-id="181b5-107">Definição</span><span class="sxs-lookup"><span data-stu-id="181b5-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="181b5-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="181b5-108">Required.</span></span> <span data-ttu-id="181b5-109">O nome do arquivo que conterá o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="181b5-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="181b5-110">Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="181b5-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="181b5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="181b5-111">Remarks</span></span>  
 <span data-ttu-id="181b5-112">As informações a seguir são adicionadas ao `file`:</span><span class="sxs-lookup"><span data-stu-id="181b5-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="181b5-113">Uma cópia de todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="181b5-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="181b5-114">Uma lista das opções de compilador usado na compilação.</span><span class="sxs-lookup"><span data-stu-id="181b5-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="181b5-115">Informações de versão sobre o compilador, o common language runtime e o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="181b5-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="181b5-116">Saída do compilador, se houver.</span><span class="sxs-lookup"><span data-stu-id="181b5-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="181b5-117">Uma descrição do problema para o qual você será solicitado.</span><span class="sxs-lookup"><span data-stu-id="181b5-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="181b5-118">Uma descrição de como você acha que o problema deve ser corrigida, o que é solicitada.</span><span class="sxs-lookup"><span data-stu-id="181b5-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="181b5-119">Como uma cópia de todos os arquivos de código-fonte está incluída no `file`, talvez você queira reproduzir o defeito de código (suspeita) no programa mais curto possível.</span><span class="sxs-lookup"><span data-stu-id="181b5-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="181b5-120">O `-bugreport` opção produz um arquivo que contém informações potencialmente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="181b5-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="181b5-121">Isso inclui a hora atual, a versão do compilador [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] versão, versão do sistema operacional, nome de usuário, os argumentos de linha de comando com a qual o compilador foi executado, todo o código fonte, e o formato binário de qualquer um de assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="181b5-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="181b5-122">Essa opção pode ser acessada, especificando opções de linha de comando no arquivo Web. config para uma compilação do servidor de um [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="181b5-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="181b5-123">Para evitar isso, modifique o arquivo Machine. config para impedir os usuários de compilação no servidor.</span><span class="sxs-lookup"><span data-stu-id="181b5-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="181b5-124">Se essa opção é usada com `-errorreport:prompt`, `-errorreport:queue`, ou `-errorreport:send`, e o aplicativo encontra um erro interno do compilador, as informações no `file` é enviada à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="181b5-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="181b5-125">Essas informações ajudam os engenheiros da Microsoft a identificar a causa do erro e podem ajudar a melhorar a próxima versão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="181b5-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="181b5-126">Por padrão, nenhuma informação é enviada à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="181b5-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="181b5-127">No entanto, quando você compila um aplicativo usando `-errorreport:queue`, que é habilitado por padrão, o aplicativo obtém seus relatórios de erro.</span><span class="sxs-lookup"><span data-stu-id="181b5-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="181b5-128">Em seguida, quando o administrador do computador fizer logon, o sistema de relatórios de erro exibe uma janela pop-up que permite que o administrador encaminhar à Microsoft relatórios de quaisquer erros que ocorreram desde o logon.</span><span class="sxs-lookup"><span data-stu-id="181b5-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="181b5-129">O `/bugreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível apenas quando você compila na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="181b5-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="181b5-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="181b5-130">Example</span></span>  
 <span data-ttu-id="181b5-131">O exemplo a seguir compila `T2.vb` e coloca todas as informações do serviço de relato de erros no arquivo `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="181b5-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="181b5-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="181b5-132">See Also</span></span>  
 [<span data-ttu-id="181b5-133">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="181b5-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="181b5-134">-a depuração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="181b5-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="181b5-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="181b5-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="181b5-136">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="181b5-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="181b5-137">trustLevel elemento para securityPolicy (ASP.NET Settings Schema)</span><span class="sxs-lookup"><span data-stu-id="181b5-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
