---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: 5471f0783eee5e2c14cf0f140094d5c292a73756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663252"
---
# <a name="-errorreport"></a><span data-ttu-id="10b95-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="10b95-102">-errorreport</span></span>

<span data-ttu-id="10b95-103">Especifica como o compilador do Visual Basic deve relatar erros internos do compilador.</span><span class="sxs-lookup"><span data-stu-id="10b95-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="10b95-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10b95-104">Syntax</span></span>

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="10b95-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="10b95-105">Remarks</span></span>

<span data-ttu-id="10b95-106">Essa opção fornece uma maneira conveniente de relatar um erro interno do compilador do Visual Basic (ICE) para a equipe do Visual Basic na Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="10b95-107">Por padrão, o compilador não envia informações à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="10b95-108">No entanto, se você encontrar um erro interno do compilador, esta opção permite que você relate o erro à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="10b95-109">Essas informações ajudam os engenheiros da Microsoft a identificar a causa e podem ajudar a melhorar a próxima versão do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="10b95-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="10b95-110">Capacidade de um usuário de enviar relatórios depende de permissões de política de computador e de usuário.</span><span class="sxs-lookup"><span data-stu-id="10b95-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="10b95-111">A tabela a seguir resume o efeito do `-errorreport` opção.</span><span class="sxs-lookup"><span data-stu-id="10b95-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="10b95-112">Opção</span><span class="sxs-lookup"><span data-stu-id="10b95-112">Option</span></span>|<span data-ttu-id="10b95-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="10b95-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="10b95-114">Se ocorrer um erro interno do compilador, uma caixa de diálogo aparece para que você possa exibir os dados exatos que o compilador coletado.</span><span class="sxs-lookup"><span data-stu-id="10b95-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="10b95-115">Você pode determinar se há informações confidenciais no relatório de erros e tomar uma decisão sobre se deseja enviá-lo à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="10b95-116">Se você optar por enviá-lo, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="10b95-117">Enfileira o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="10b95-117">Queues the error report.</span></span> <span data-ttu-id="10b95-118">Ao fazer logon com privilégios de administrador, você pode relatar quaisquer falhas desde a última vez em que você estava conectado (você não precisará enviar relatórios de falhas mais de uma vez a cada três dias).</span><span class="sxs-lookup"><span data-stu-id="10b95-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="10b95-119">Esse é o comportamento padrão quando o `-errorreport` opção não for especificada.</span><span class="sxs-lookup"><span data-stu-id="10b95-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="10b95-120">Se ocorrer um erro interno do compilador, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="10b95-121">A opção `-errorreport:send` tenta enviar informações de erro à Microsoft automaticamente se o relatório está habilitado pela [relatório de erros do Windows](/windows/desktop/wer/windows-error-reporting) configurações do sistema.</span><span class="sxs-lookup"><span data-stu-id="10b95-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="10b95-122">Se ocorrer um erro interno do compilador, ele será não ser coletado ou enviado à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="10b95-123">O compilador envia os dados que incluem a pilha no momento do erro, que geralmente inclui algum código-fonte.</span><span class="sxs-lookup"><span data-stu-id="10b95-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="10b95-124">Se `-errorreport` é usado com o [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, em seguida, o arquivo de origem inteiro é enviado.</span><span class="sxs-lookup"><span data-stu-id="10b95-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="10b95-125">Essa opção é melhor usada com o [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, pois permite que os engenheiros da Microsoft mais facilmente reproduzir o erro.</span><span class="sxs-lookup"><span data-stu-id="10b95-125">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="10b95-126">O `-errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="10b95-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="10b95-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10b95-127">Example</span></span>

<span data-ttu-id="10b95-128">O código a seguir tenta compilar `T2.vb`, e se o compilador encontra um erro interno do compilador, ele solicitará que você enviar o relatório de erros à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10b95-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="10b95-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10b95-129">See also</span></span>

- [<span data-ttu-id="10b95-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10b95-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="10b95-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="10b95-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="10b95-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="10b95-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
