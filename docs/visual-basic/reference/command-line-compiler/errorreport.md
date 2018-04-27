---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dc321f7f927d68a9f270076640cbc6d31d2f6d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="-errorreport"></a><span data-ttu-id="5bf31-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="5bf31-102">-errorreport</span></span>
<span data-ttu-id="5bf31-103">Especifica como o compilador do Visual Basic deve relatar erros do compilador interno.</span><span class="sxs-lookup"><span data-stu-id="5bf31-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bf31-104">Syntax</span></span>  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="5bf31-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bf31-105">Remarks</span></span>  
 <span data-ttu-id="5bf31-106">Essa opção fornece uma maneira conveniente para relatar um erro interno do compilador do Visual Basic (ICE) para a equipe do Visual Basic na Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="5bf31-107">Por padrão, o compilador não envia nenhuma informação à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="5bf31-108">No entanto, se você encontrar um erro interno do compilador, esta opção permite que você relate o erro à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="5bf31-109">Essas informações ajudam os engenheiros da Microsoft a identificar a causa e podem ajudar a melhorar a próxima versão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5bf31-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>  
  
 <span data-ttu-id="5bf31-110">Capacidade de um usuário para enviar relatórios depende de permissões de política de computador e de usuário.</span><span class="sxs-lookup"><span data-stu-id="5bf31-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="5bf31-111">A tabela a seguir resume o efeito do `-errorreport` opção.</span><span class="sxs-lookup"><span data-stu-id="5bf31-111">The following table summarizes the effect of the `-errorreport` option.</span></span>  
  
|<span data-ttu-id="5bf31-112">Opção</span><span class="sxs-lookup"><span data-stu-id="5bf31-112">Option</span></span>|<span data-ttu-id="5bf31-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="5bf31-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="5bf31-114">Se ocorrer um erro interno do compilador, uma caixa de diálogo aparece para que você pode exibir os dados exatos que o compilador coletado.</span><span class="sxs-lookup"><span data-stu-id="5bf31-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="5bf31-115">Você pode determinar se não houver nenhuma informação confidencial no relatório de erros e tomar uma decisão sobre se deseja enviá-lo à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="5bf31-116">Se você optar por enviá-lo, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="5bf31-117">Enfileira o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="5bf31-117">Queues the error report.</span></span> <span data-ttu-id="5bf31-118">Quando você faz logon com privilégios de administrador, você pode relatar falhas desde a última vez em que você estava logado (você não precisará enviar relatórios de falhas mais de uma vez a cada três dias).</span><span class="sxs-lookup"><span data-stu-id="5bf31-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="5bf31-119">Esse é o comportamento padrão quando o `-errorreport` opção não for especificada.</span><span class="sxs-lookup"><span data-stu-id="5bf31-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="5bf31-120">Se ocorrer um erro interno do compilador, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="5bf31-121">A opção `-errorreport:send` tenta enviar automaticamente informações de erro à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="5bf31-122">Essa opção depende do registro.</span><span class="sxs-lookup"><span data-stu-id="5bf31-122">This option depends on the registry.</span></span> <span data-ttu-id="5bf31-123">Para obter mais informações sobre como definir os valores apropriados no registro, consulte [como ativar o relatório de erros automático em ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).</span><span class="sxs-lookup"><span data-stu-id="5bf31-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="5bf31-124">Se ocorrer um erro interno do compilador, ele não será coletado ou enviado à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="5bf31-125">O compilador envia os dados que incluem a pilha no momento do erro, que geralmente inclui alguns código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5bf31-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="5bf31-126">Se `-errorreport` é usado com o [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, em seguida, o arquivo de origem inteiro é enviado.</span><span class="sxs-lookup"><span data-stu-id="5bf31-126">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="5bf31-127">Essa opção é melhor usada com a [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, pois ela permite que os engenheiros da Microsoft mais facilmente reproduza o erro.</span><span class="sxs-lookup"><span data-stu-id="5bf31-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bf31-128">O `-errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5bf31-128">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bf31-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5bf31-129">Example</span></span>  
 <span data-ttu-id="5bf31-130">O código a seguir tenta compilar `T2.vb`, e se o compilador encontra um erro interno do compilador, ele solicitará a enviar o relatório de erros à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bf31-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bf31-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bf31-131">See Also</span></span>  
 [<span data-ttu-id="5bf31-132">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bf31-132">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5bf31-133">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="5bf31-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="5bf31-134">-bugreport</span><span class="sxs-lookup"><span data-stu-id="5bf31-134">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
