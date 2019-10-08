---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 46d726332806f7d1f6e80dd7df31867051276b45
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002356"
---
# <a name="-bugreport"></a><span data-ttu-id="52d12-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="52d12-102">-bugreport</span></span>
<span data-ttu-id="52d12-103">Cria um arquivo que você pode usar ao arquivar um relatório de bug.</span><span class="sxs-lookup"><span data-stu-id="52d12-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52d12-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="52d12-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="52d12-105">Arguments</span></span>  
  
|<span data-ttu-id="52d12-106">Termo</span><span class="sxs-lookup"><span data-stu-id="52d12-106">Term</span></span>|<span data-ttu-id="52d12-107">Definição</span><span class="sxs-lookup"><span data-stu-id="52d12-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="52d12-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="52d12-108">Required.</span></span> <span data-ttu-id="52d12-109">O nome do arquivo que conterá seu relatório de bugs.</span><span class="sxs-lookup"><span data-stu-id="52d12-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="52d12-110">Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="52d12-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52d12-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="52d12-111">Remarks</span></span>  
 <span data-ttu-id="52d12-112">As informações a seguir são adicionadas a `file`:</span><span class="sxs-lookup"><span data-stu-id="52d12-112">The following information is added to `file`:</span></span>  
  
- <span data-ttu-id="52d12-113">Uma cópia de todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="52d12-113">A copy of all source-code files in the compilation.</span></span>  
  
- <span data-ttu-id="52d12-114">Uma lista das opções de compilador usadas na compilação.</span><span class="sxs-lookup"><span data-stu-id="52d12-114">A list of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="52d12-115">Informações de versão sobre seu compilador, Common Language Runtime e sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="52d12-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
- <span data-ttu-id="52d12-116">Saída do compilador, se houver.</span><span class="sxs-lookup"><span data-stu-id="52d12-116">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="52d12-117">Uma descrição do problema, para o qual você será solicitado.</span><span class="sxs-lookup"><span data-stu-id="52d12-117">A description of the problem, for which you are prompted.</span></span>  
  
- <span data-ttu-id="52d12-118">Uma descrição de como você acredita que o problema deve ser corrigido, para o qual você será solicitado.</span><span class="sxs-lookup"><span data-stu-id="52d12-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="52d12-119">Como uma cópia de todos os arquivos de código-fonte está incluída no `file`, talvez você queira reproduzir o defeito do código (suspeito) no programa mais curto possível.</span><span class="sxs-lookup"><span data-stu-id="52d12-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="52d12-120">A opção `-bugreport` produz um arquivo que contém informações potencialmente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="52d12-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="52d12-121">Isso inclui a hora atual, a versão do compilador, a versão .NET Framework, a versão do sistema operacional, o nome de usuário, os argumentos de linha de comando com os quais o compilador foi executado, todo o código-fonte e a forma binária de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="52d12-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="52d12-122">Essa opção pode ser acessada especificando opções de linha de comando no arquivo Web. config para uma compilação do lado do servidor de um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="52d12-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="52d12-123">Para evitar isso, modifique o arquivo Machine. config para impedir que os usuários sejam compilados no servidor.</span><span class="sxs-lookup"><span data-stu-id="52d12-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="52d12-124">Se essa opção for usada com `-errorreport:prompt`, `-errorreport:queue` ou `-errorreport:send` e o aplicativo encontrar um erro de compilador interno, as informações em `file` serão enviadas para a Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="52d12-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="52d12-125">Essas informações ajudarão os engenheiros da Microsoft a identificar a causa do erro e poderão ajudar a melhorar a próxima versão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="52d12-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="52d12-126">Por padrão, nenhuma informação é enviada à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="52d12-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="52d12-127">No entanto, quando você compila um aplicativo usando `-errorreport:queue`, que é habilitado por padrão, o aplicativo coleta seus relatórios de erros.</span><span class="sxs-lookup"><span data-stu-id="52d12-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="52d12-128">Em seguida, quando o administrador do computador fizer logon, o sistema de relatórios de erros exibirá uma janela pop-up que permite ao administrador encaminhar à Microsoft quaisquer relatórios de erros ocorridos desde o logon.</span><span class="sxs-lookup"><span data-stu-id="52d12-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52d12-129">A opção `/bugreport` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente quando você compila a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="52d12-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52d12-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52d12-130">Example</span></span>  
 <span data-ttu-id="52d12-131">O exemplo a seguir compila `T2.vb` e coloca todas as informações de relatório de bugs no arquivo `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="52d12-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```console  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="52d12-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52d12-132">See also</span></span>

- [<span data-ttu-id="52d12-133">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52d12-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="52d12-134">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52d12-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="52d12-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="52d12-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [<span data-ttu-id="52d12-136">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="52d12-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="52d12-137">[Elemento trustLevel para securityPolicy (esquema de configurações do ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="52d12-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
