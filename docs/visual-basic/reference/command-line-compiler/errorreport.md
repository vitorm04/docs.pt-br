---
title: /errorreport | Documentos do Microsoft
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
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c2f9a9daf6aed6348baeb2c4de2fe5caef70f52b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="errorreport"></a><span data-ttu-id="a417c-102">/errorreport</span><span class="sxs-lookup"><span data-stu-id="a417c-102">/errorreport</span></span>
<span data-ttu-id="a417c-103">Especifica como o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve relatar erros do compilador interno.</span><span class="sxs-lookup"><span data-stu-id="a417c-103">Specifies how the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a417c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a417c-104">Syntax</span></span>  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="a417c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a417c-105">Remarks</span></span>  
 <span data-ttu-id="a417c-106">Essa opção fornece uma maneira conveniente para relatar um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] erro interno do compilador (ICE) para o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] equipe da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-106">This option provides a convenient way to report a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] internal compiler error (ICE) to the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] team at Microsoft.</span></span> <span data-ttu-id="a417c-107">Por padrão, o compilador não envia informações à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="a417c-108">No entanto, se você encontrar um erro interno do compilador, esta opção permite que você relate o erro à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="a417c-109">Essas informações ajudarão os engenheiros da Microsoft identificar a causa e podem ajudar a melhorar a próxima versão do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="a417c-109">That information will help Microsoft engineers identify the cause and may help improve the next release of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="a417c-110">A capacidade do usuário para enviar relatórios depende de permissões de política de máquina e usuário.</span><span class="sxs-lookup"><span data-stu-id="a417c-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="a417c-111">A tabela a seguir resume o efeito de `/errorreport` opção.</span><span class="sxs-lookup"><span data-stu-id="a417c-111">The following table summarizes the effect of the `/errorreport` option.</span></span>  
  
|<span data-ttu-id="a417c-112">Opção</span><span class="sxs-lookup"><span data-stu-id="a417c-112">Option</span></span>|<span data-ttu-id="a417c-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="a417c-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="a417c-114">Se ocorrer um erro interno do compilador, uma caixa de diálogo aparece para que você possa exibir os dados exatos que o compilador coletado.</span><span class="sxs-lookup"><span data-stu-id="a417c-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="a417c-115">Você pode determinar se há informações confidenciais no relatório de erro e tomar uma decisão sobre se deseja enviá-lo à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="a417c-116">Se você optar por enviá-lo, e as configurações de diretiva de computador e usuário permitirem, o compilador envia os dados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="a417c-117">Enfileira o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="a417c-117">Queues the error report.</span></span> <span data-ttu-id="a417c-118">Quando você efetuar logon com privilégios de administrador, você pode relatar falhas desde a última vez em que você estava conectado (você não precisará enviar relatórios de falhas mais de uma vez a cada três dias).</span><span class="sxs-lookup"><span data-stu-id="a417c-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="a417c-119">Esse é o comportamento padrão quando o `/errorreport` opção não for especificada.</span><span class="sxs-lookup"><span data-stu-id="a417c-119">This is the default behavior when the `/errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="a417c-120">Se ocorrer um erro interno do compilador, e as configurações de diretiva de computador e usuário permitirem, o compilador envia os dados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="a417c-121">A opção `/errorReport:send` tenta enviar automaticamente informações de erro à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-121">The option `/errorReport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="a417c-122">Essa opção depende do registro.</span><span class="sxs-lookup"><span data-stu-id="a417c-122">This option depends on the registry.</span></span> <span data-ttu-id="a417c-123">Para obter mais informações sobre como definir os valores apropriados no registro, consulte [como ativar o relatório de erros automático em ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).</span><span class="sxs-lookup"><span data-stu-id="a417c-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="a417c-124">Se ocorrer um erro interno do compilador, ele será não ser coletado ou enviado à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="a417c-125">O compilador envia os dados que incluem a pilha no momento do erro, que geralmente inclui algum código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a417c-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="a417c-126">Se `/errorreport` é usado com o [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, o arquivo de origem inteiro é enviado.</span><span class="sxs-lookup"><span data-stu-id="a417c-126">If `/errorreport` is used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="a417c-127">Essa opção é melhor usada com a [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, pois permite que os engenheiros da Microsoft mais facilmente reproduzir o erro.</span><span class="sxs-lookup"><span data-stu-id="a417c-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a417c-128">O `/errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="a417c-128">The `/errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a417c-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a417c-129">Example</span></span>  
 <span data-ttu-id="a417c-130">O código a seguir tenta compilar `T2.vb`, e se o compilador encontrar um erro interno do compilador, ele solicitará que você envie o relatório de erros à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a417c-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a417c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a417c-131">See Also</span></span>  
 <span data-ttu-id="a417c-132">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="a417c-132">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="a417c-133"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="a417c-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="a417c-134"> [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)</span><span class="sxs-lookup"><span data-stu-id="a417c-134"> [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)</span></span>
