---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 02d84bceb0242988c70889ddd5d3dc7530f6e808
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793541"
---
# <a name="-bugreport"></a><span data-ttu-id="d72c1-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="d72c1-102">-bugreport</span></span>

<span data-ttu-id="d72c1-103">Cria um arquivo que você pode usar ao arquivar um relatório de bug.</span><span class="sxs-lookup"><span data-stu-id="d72c1-103">Creates a file that you can use when you file a bug report.</span></span>

## <a name="syntax"></a><span data-ttu-id="d72c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d72c1-104">Syntax</span></span>

```console
-bugreport:file
```

## <a name="arguments"></a><span data-ttu-id="d72c1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d72c1-105">Arguments</span></span>

|<span data-ttu-id="d72c1-106">Termo</span><span class="sxs-lookup"><span data-stu-id="d72c1-106">Term</span></span>|<span data-ttu-id="d72c1-107">Definição</span><span class="sxs-lookup"><span data-stu-id="d72c1-107">Definition</span></span>|
|---|---|
|`file`|<span data-ttu-id="d72c1-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d72c1-108">Required.</span></span> <span data-ttu-id="d72c1-109">O nome do arquivo que conterá seu relatório de bugs.</span><span class="sxs-lookup"><span data-stu-id="d72c1-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="d72c1-110">Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="d72c1-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d72c1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d72c1-111">Remarks</span></span>

<span data-ttu-id="d72c1-112">As informações a seguir são adicionadas ao `file`:</span><span class="sxs-lookup"><span data-stu-id="d72c1-112">The following information is added to `file`:</span></span>

- <span data-ttu-id="d72c1-113">Uma cópia de todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="d72c1-113">A copy of all source-code files in the compilation.</span></span>

- <span data-ttu-id="d72c1-114">Uma lista das opções de compilador usadas na compilação.</span><span class="sxs-lookup"><span data-stu-id="d72c1-114">A list of the compiler options used in the compilation.</span></span>

- <span data-ttu-id="d72c1-115">Informações de versão sobre seu compilador, Common Language Runtime e sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="d72c1-115">Version information about your compiler, common language runtime, and operating system.</span></span>

- <span data-ttu-id="d72c1-116">Saída do compilador, se houver.</span><span class="sxs-lookup"><span data-stu-id="d72c1-116">Compiler output, if any.</span></span>

- <span data-ttu-id="d72c1-117">Uma descrição do problema, para o qual você será solicitado.</span><span class="sxs-lookup"><span data-stu-id="d72c1-117">A description of the problem, for which you are prompted.</span></span>

- <span data-ttu-id="d72c1-118">Uma descrição de como você acredita que o problema deve ser corrigido, para o qual você será solicitado.</span><span class="sxs-lookup"><span data-stu-id="d72c1-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>

<span data-ttu-id="d72c1-119">Como uma cópia de todos os arquivos de código-fonte está incluída no `file`, talvez você queira reproduzir o defeito do código (suspeito) no programa mais curto possível.</span><span class="sxs-lookup"><span data-stu-id="d72c1-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d72c1-120">A opção `-bugreport` produz um arquivo que contém informações potencialmente confidenciais.</span><span class="sxs-lookup"><span data-stu-id="d72c1-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="d72c1-121">Isso inclui a hora atual, a versão do compilador, a versão .NET Framework, a versão do sistema operacional, o nome de usuário, os argumentos de linha de comando com os quais o compilador foi executado, todo o código-fonte e a forma binária de qualquer assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="d72c1-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="d72c1-122">Essa opção pode ser acessada especificando opções de linha de comando no arquivo Web. config para uma compilação do lado do servidor de um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d72c1-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="d72c1-123">Para evitar isso, modifique o arquivo Machine. config para impedir que os usuários sejam compilados no servidor.</span><span class="sxs-lookup"><span data-stu-id="d72c1-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>

<span data-ttu-id="d72c1-124">Se essa opção for usada com `-errorreport:prompt`, `-errorreport:queue`ou `-errorreport:send`e o aplicativo encontrar um erro de compilador interno, as informações em `file` serão enviadas para a Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="d72c1-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="d72c1-125">Essas informações ajudarão os engenheiros da Microsoft a identificar a causa do erro e poderão ajudar a melhorar a próxima versão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d72c1-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="d72c1-126">Por padrão, nenhuma informação é enviada à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d72c1-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="d72c1-127">No entanto, quando você compila um aplicativo usando `-errorreport:queue`, que é habilitado por padrão, o aplicativo coleta seus relatórios de erros.</span><span class="sxs-lookup"><span data-stu-id="d72c1-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="d72c1-128">Em seguida, quando o administrador do computador fizer logon, o sistema de relatórios de erros exibirá uma janela pop-up que permite ao administrador encaminhar à Microsoft quaisquer relatórios de erros ocorridos desde o logon.</span><span class="sxs-lookup"><span data-stu-id="d72c1-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>

> [!NOTE]
> <span data-ttu-id="d72c1-129">A opção `-bugreport` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente quando você compila a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d72c1-129">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="d72c1-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d72c1-130">Example</span></span>

<span data-ttu-id="d72c1-131">O exemplo a seguir compila *T2. vb* e coloca todas as informações de relatório de bugs no arquivo *problem. txt*.</span><span class="sxs-lookup"><span data-stu-id="d72c1-131">The following example compiles *T2.vb* and puts all bug-reporting information in the file *Problem.txt*.</span></span>

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="d72c1-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="d72c1-132">See also</span></span>

- [<span data-ttu-id="d72c1-133">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d72c1-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d72c1-134">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d72c1-134">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="d72c1-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="d72c1-135">-errorreport</span></span>](errorreport.md)
- [<span data-ttu-id="d72c1-136">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d72c1-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="d72c1-137">[Elemento trustLevel para securityPolicy (esquema de configurações do ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d72c1-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
