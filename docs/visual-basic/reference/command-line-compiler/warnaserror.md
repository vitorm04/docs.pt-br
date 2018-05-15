---
title: -/warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c04bff4070b0f1c288c8853e5045fbf670d8e9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="d79f8-102">-/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d79f8-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="d79f8-103">Faz com que o compilador trate a primeira ocorrência de um aviso como erro.</span><span class="sxs-lookup"><span data-stu-id="d79f8-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d79f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d79f8-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d79f8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d79f8-105">Arguments</span></span>  
  
|<span data-ttu-id="d79f8-106">Termo</span><span class="sxs-lookup"><span data-stu-id="d79f8-106">Term</span></span>|<span data-ttu-id="d79f8-107">Definição</span><span class="sxs-lookup"><span data-stu-id="d79f8-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d79f8-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="d79f8-108">+ &#124; -</span></span>|<span data-ttu-id="d79f8-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d79f8-109">Optional.</span></span> <span data-ttu-id="d79f8-110">Por padrão, `-warnaserror-` está em vigor; avisos não impedem que o compilador gera um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="d79f8-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="d79f8-111">O `-warnaserror` opção, que é o mesmo como `-warnaserror+`, faz com que avisos a serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="d79f8-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="d79f8-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d79f8-112">Optional.</span></span> <span data-ttu-id="d79f8-113">Lista delimitada por vírgulas da identificação do aviso numera a qual o `-warnaserror` opção se aplica.</span><span class="sxs-lookup"><span data-stu-id="d79f8-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="d79f8-114">Se nenhuma ID de aviso for especificada, o `-warnaserror` opção se aplica a todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="d79f8-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d79f8-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="d79f8-115">Remarks</span></span>  
 <span data-ttu-id="d79f8-116">O `-warnaserror` opção trata todos os avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="d79f8-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="d79f8-117">Quaisquer mensagens que seriam normalmente ser relatadas como avisos em vez disso, são relatados como erros.</span><span class="sxs-lookup"><span data-stu-id="d79f8-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="d79f8-118">O compilador relata ocorrências subsequentes do mesmo aviso como avisos.</span><span class="sxs-lookup"><span data-stu-id="d79f8-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="d79f8-119">Por padrão, `-warnaserror-` está em vigor, o que faz com que os avisos sejam apenas informativos.</span><span class="sxs-lookup"><span data-stu-id="d79f8-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="d79f8-120">O `-warnaserror` opção, que é o mesmo como `-warnaserror+`, faz com que avisos a serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="d79f8-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="d79f8-121">Se você quiser apenas alguns avisos específicos a serem tratados como erros, você pode especificar uma lista separada por vírgulas de números de avisos a serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="d79f8-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d79f8-122">O `-warnaserror` opção não controla como os avisos são exibidos.</span><span class="sxs-lookup"><span data-stu-id="d79f8-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="d79f8-123">Use o [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) opção para desativar avisos.</span><span class="sxs-lookup"><span data-stu-id="d79f8-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="d79f8-124">Para definir - /warnaserror para tratar todos os avisos como erros no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d79f8-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d79f8-125">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="d79f8-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d79f8-126">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d79f8-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d79f8-127">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="d79f8-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d79f8-128">3.  Verifique se o **desativar todos os avisos** caixa de seleção está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="d79f8-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d79f8-129">4.  Verifique o **trate todos os avisos como erros** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="d79f8-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="d79f8-130">Para definir - /warnaserror para tratar avisos específicos como erros no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d79f8-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d79f8-131">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="d79f8-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d79f8-132">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d79f8-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="d79f8-133">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="d79f8-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d79f8-134">3.  Verifique se o **desativar todos os avisos** caixa de seleção está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="d79f8-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d79f8-135">4.  Verifique se o **trate todos os avisos como erros** caixa de seleção está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="d79f8-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="d79f8-136">5.  Selecione **erro** do **notificação** coluna adjacente ao aviso que deve ser tratado como um erro.</span><span class="sxs-lookup"><span data-stu-id="d79f8-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d79f8-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d79f8-137">Example</span></span>  
 <span data-ttu-id="d79f8-138">O código a seguir compila `In.vb` e direciona o compilador para exibir um erro para a primeira ocorrência de cada aviso que ele encontra.</span><span class="sxs-lookup"><span data-stu-id="d79f8-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="d79f8-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d79f8-139">Example</span></span>  
 <span data-ttu-id="d79f8-140">O código a seguir compila `T2.vb` e trata apenas o aviso de variáveis locais não utilizadas (42024) como um erro.</span><span class="sxs-lookup"><span data-stu-id="d79f8-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d79f8-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d79f8-141">See Also</span></span>  
 [<span data-ttu-id="d79f8-142">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d79f8-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d79f8-143">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d79f8-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d79f8-144">Configurando avisos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d79f8-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
