---
title: -errorreport (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: dcbb9467da87a82147176bb0feb00383aff2c77f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45609854"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="8cc6e-102">-errorreport (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="8cc6e-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="8cc6e-103">Esta opção fornece uma maneira conveniente de relatar um erro interno do compilador do C# à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cc6e-104">No Windows Vista e Windows Server 2008, as configurações de relatório de erros que você faz para o Visual Studio não substituem as configurações feitas pelo WER (Relatório de Erros do Windows).</span><span class="sxs-lookup"><span data-stu-id="8cc6e-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="8cc6e-105">As configurações do WER sempre têm precedência sobre as configurações de relatório de erros do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc6e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8cc6e-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="8cc6e-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="8cc6e-107">Arguments</span></span>  
 <span data-ttu-id="8cc6e-108">**none**</span><span class="sxs-lookup"><span data-stu-id="8cc6e-108">**none**</span></span>  
 <span data-ttu-id="8cc6e-109">Relatórios sobre erros internos do compilador não serão coletados ou enviados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="8cc6e-110">**prompt**</span><span class="sxs-lookup"><span data-stu-id="8cc6e-110">**prompt**</span></span>  
 <span data-ttu-id="8cc6e-111">Solicita que você envie um relatório quando um erro interno do compilador for recebido.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="8cc6e-112">**prompt** é o padrão quando você compila um aplicativo no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="8cc6e-113">**queue**</span><span class="sxs-lookup"><span data-stu-id="8cc6e-113">**queue**</span></span>  
 <span data-ttu-id="8cc6e-114">Enfileira o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-114">Queues the error report.</span></span> <span data-ttu-id="8cc6e-115">Quando você faz logon com credenciais administrativas, pode relatar falhas desde a última vez que você fez logon.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="8cc6e-116">Não será solicitado que você envie relatórios de falhas mais de uma vez a cada três dias.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="8cc6e-117">**queue** é o padrão quando você compila um aplicativo na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="8cc6e-118">**send**</span><span class="sxs-lookup"><span data-stu-id="8cc6e-118">**send**</span></span>  
 <span data-ttu-id="8cc6e-119">Envia automaticamente relatórios de erros internos do compilador para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="8cc6e-120">Para habilitar essa opção, primeiro você deve concordar com a política de coleta de dados da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="8cc6e-121">Na primeira vez que você especificar **-errorreport:send** em um computador, uma mensagem de compilador indicará um site que contém a política de coleta de dados da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="8cc6e-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="8cc6e-122">Remarks</span></span>  
 <span data-ttu-id="8cc6e-123">Um ICE (erro interno do compilador) ocorre quando o compilador não pode processar um arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="8cc6e-124">Quando um ICE ocorre, o compilador não produz um arquivo de saída ou qualquer diagnóstico útil que você pode usar para corrigir o código.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="8cc6e-125">Em versões anteriores, quando você recebia um ICE, era incentivado a entrar em contato com o Microsoft Product Support Services para relatar o problema.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="8cc6e-126">Usando **-errorreport**, você pode fornecer informações do ICE à equipe do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="8cc6e-127">Os relatórios de erro podem ajudar a melhorar versões futuras do compilador.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="8cc6e-128">A capacidade do usuário de enviar relatórios depende das permissões de política de usuário e de computador.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="8cc6e-129">Para obter mais informações sobre o depurador de erro, consulte [Descrição da ferramenta Dr. Watson para Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span><span class="sxs-lookup"><span data-stu-id="8cc6e-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8cc6e-130">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8cc6e-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="8cc6e-131">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="8cc6e-132">Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="8cc6e-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="8cc6e-133">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-133">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="8cc6e-134">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-134">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="8cc6e-135">Modifique a propriedade **Relatório de Erros do Compilador Interno**.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="8cc6e-136">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc6e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cc6e-137">See Also</span></span>  

- [<span data-ttu-id="8cc6e-138">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="8cc6e-138">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
