---
title: "-errorreport (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /errorreport
dev_langs:
- CSharp
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: 35
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d32ec08da36509527b153166ae15019f129aad71
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="errorreport-c-compiler-options"></a><span data-ttu-id="29b18-102">/errorreport (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="29b18-102">/errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="29b18-103">Esta opção fornece uma maneira conveniente de relatar um erro interno do compilador do C# à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29b18-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29b18-104">No Windows Vista e Windows Server 2008, as configurações de relatório de erros que você faz para o Visual Studio não substituem as configurações feitas pelo WER (Relatório de Erros do Windows).</span><span class="sxs-lookup"><span data-stu-id="29b18-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="29b18-105">As configurações do WER sempre têm precedência sobre as configurações de relatório de erros do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29b18-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b18-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29b18-106">Syntax</span></span>  
  
```console  
/errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="29b18-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="29b18-107">Arguments</span></span>  
 <span data-ttu-id="29b18-108">**none**</span><span class="sxs-lookup"><span data-stu-id="29b18-108">**none**</span></span>  
 <span data-ttu-id="29b18-109">Relatórios sobre erros internos do compilador não serão coletados ou enviados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29b18-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="29b18-110">**prompt**</span><span class="sxs-lookup"><span data-stu-id="29b18-110">**prompt**</span></span>  
 <span data-ttu-id="29b18-111">Solicita que você envie um relatório quando um erro interno do compilador for recebido.</span><span class="sxs-lookup"><span data-stu-id="29b18-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="29b18-112">**prompt** é o padrão quando você compila um aplicativo no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="29b18-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="29b18-113">**queue**</span><span class="sxs-lookup"><span data-stu-id="29b18-113">**queue**</span></span>  
 <span data-ttu-id="29b18-114">Enfileira o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="29b18-114">Queues the error report.</span></span> <span data-ttu-id="29b18-115">Quando você faz logon com credenciais administrativas, pode relatar falhas desde a última vez que você fez logon.</span><span class="sxs-lookup"><span data-stu-id="29b18-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="29b18-116">Não será solicitado que você envie relatórios de falhas mais de uma vez a cada três dias.</span><span class="sxs-lookup"><span data-stu-id="29b18-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="29b18-117">**queue** é o padrão quando você compila um aplicativo na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="29b18-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="29b18-118">**send**</span><span class="sxs-lookup"><span data-stu-id="29b18-118">**send**</span></span>  
 <span data-ttu-id="29b18-119">Envia automaticamente relatórios de erros internos do compilador para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29b18-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="29b18-120">Para habilitar essa opção, primeiro você deve concordar com a política de coleta de dados da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29b18-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="29b18-121">Na primeira vez que você especificar **/errorreport:send** em um computador, uma mensagem de compilador indicará a um site que contém a política de coleta de dados da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29b18-121">The first time that you specify **/errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
  
 <span data-ttu-id="29b18-122">Essa opção depende das configurações do Registro.</span><span class="sxs-lookup"><span data-stu-id="29b18-122">This option depends on registry settings.</span></span> <span data-ttu-id="29b18-123">Para obter informações sobre como definir os valores apropriados no Registro, consulte [Como ativar o relatório de erros automático nas ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695) no site do MSDN.</span><span class="sxs-lookup"><span data-stu-id="29b18-123">For information about how to set the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695) on the MSDN Web site.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29b18-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="29b18-124">Remarks</span></span>  
 <span data-ttu-id="29b18-125">Um ICE (erro interno do compilador) ocorre quando o compilador não pode processar um arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="29b18-125">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="29b18-126">Quando um ICE ocorre, o compilador não produz um arquivo de saída ou qualquer diagnóstico útil que você pode usar para corrigir o código.</span><span class="sxs-lookup"><span data-stu-id="29b18-126">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="29b18-127">Em versões anteriores, quando você recebia um ICE, era incentivado a entrar em contato com o Microsoft Product Support Services para relatar o problema.</span><span class="sxs-lookup"><span data-stu-id="29b18-127">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="29b18-128">Usando **/errorreport**, você pode fornecer informações do ICE à equipe do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="29b18-128">By using **/errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="29b18-129">Os relatórios de erro podem ajudar a melhorar versões futuras do compilador.</span><span class="sxs-lookup"><span data-stu-id="29b18-129">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="29b18-130">A capacidade do usuário de enviar relatórios depende das permissões de política de usuário e de computador.</span><span class="sxs-lookup"><span data-stu-id="29b18-130">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="29b18-131">Para obter mais informações sobre o depurador de erro, consulte [Descrição da ferramenta Dr. Watson para Windows (Drwtsn32.exe)](http://go.microsoft.com/fwlink/?LinkId=147286).</span><span class="sxs-lookup"><span data-stu-id="29b18-131">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](http://go.microsoft.com/fwlink/?LinkId=147286).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="29b18-132">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="29b18-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="29b18-133">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="29b18-133">Open the project's **Properties** page.</span></span> <span data-ttu-id="29b18-134">Para obter mais informações, consulte [Página Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="29b18-134">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="29b18-135">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="29b18-135">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="29b18-136">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="29b18-136">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="29b18-137">Modifique a propriedade **Relatório de Erros do Compilador Interno**.</span><span class="sxs-lookup"><span data-stu-id="29b18-137">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="29b18-138">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="29b18-138">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b18-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29b18-139">See Also</span></span>  
 [<span data-ttu-id="29b18-140">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="29b18-140">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

