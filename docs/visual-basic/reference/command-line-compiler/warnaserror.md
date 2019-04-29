---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: c06326a250fba0de2f63e13672b4fffbfa8a07f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796169"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="51bbb-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51bbb-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="51bbb-103">Faz com que o compilador trate a primeira ocorrência de um aviso como um erro.</span><span class="sxs-lookup"><span data-stu-id="51bbb-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51bbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51bbb-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="51bbb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="51bbb-105">Arguments</span></span>  
  
|<span data-ttu-id="51bbb-106">Termo</span><span class="sxs-lookup"><span data-stu-id="51bbb-106">Term</span></span>|<span data-ttu-id="51bbb-107">Definição</span><span class="sxs-lookup"><span data-stu-id="51bbb-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="51bbb-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="51bbb-108">+ &#124; -</span></span>|<span data-ttu-id="51bbb-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="51bbb-109">Optional.</span></span> <span data-ttu-id="51bbb-110">Por padrão, `-warnaserror-` está em vigor; os avisos não impedem que o compilador produza um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="51bbb-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="51bbb-111">A opção `-warnaserror`, que é o mesmo que `-warnaserror+`, faz com que os avisos sejam tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="51bbb-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="51bbb-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="51bbb-112">Optional.</span></span> <span data-ttu-id="51bbb-113">A lista delimitada por vírgulas dos números de identificação do aviso aos quais se aplica a opção `-warnaserror`.</span><span class="sxs-lookup"><span data-stu-id="51bbb-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="51bbb-114">Se nenhuma identificação de aviso for especificada, a opção `-warnaserror` se aplica a todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="51bbb-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51bbb-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="51bbb-115">Remarks</span></span>  
 <span data-ttu-id="51bbb-116">A opção `-warnaserror` trata todos os avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="51bbb-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="51bbb-117">Quaisquer mensagens que normalmente seriam relatadas como avisos são, em vez disso, relatadas como erros.</span><span class="sxs-lookup"><span data-stu-id="51bbb-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="51bbb-118">O compilador relatará as ocorrências subsequentes do mesmo aviso como avisos.</span><span class="sxs-lookup"><span data-stu-id="51bbb-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="51bbb-119">Por padrão, `-warnaserror-` está em vigor, o que faz com que os avisos sejam apenas informativos.</span><span class="sxs-lookup"><span data-stu-id="51bbb-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="51bbb-120">A opção `-warnaserror`, que é o mesmo que `-warnaserror+`, faz com que os avisos sejam tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="51bbb-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="51bbb-121">Se você deseja que apenas avisos específicos sejam tratados como erros, pode especificar uma lista separada por vírgulas de números de aviso para serem tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="51bbb-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51bbb-122">A opção `-warnaserror` não controla como os avisos são exibidos.</span><span class="sxs-lookup"><span data-stu-id="51bbb-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="51bbb-123">Use a opção [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) para desativar os avisos.</span><span class="sxs-lookup"><span data-stu-id="51bbb-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="51bbb-124">Para definir -warnaserror para tratar todos os avisos como erros no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51bbb-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="51bbb-125">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="51bbb-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51bbb-126">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="51bbb-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="51bbb-127">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="51bbb-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="51bbb-128">3.  Verifique se a caixa de seleção **Desabilitar todos os avisos** está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="51bbb-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="51bbb-129">4.  Marque a caixa de seleção **Tratar todos os avisos como erros**.</span><span class="sxs-lookup"><span data-stu-id="51bbb-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="51bbb-130">Para definir -warnaserror para tratar avisos específicos como erros no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51bbb-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="51bbb-131">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="51bbb-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51bbb-132">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="51bbb-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="51bbb-133">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="51bbb-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="51bbb-134">3.  Verifique se a caixa de seleção **Desabilitar todos os avisos** está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="51bbb-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="51bbb-135">4.  Verifique se a caixa de seleção **Tratar todos os avisos como erros** está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="51bbb-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="51bbb-136">5.  Selecione **Erro** na coluna **Notificação** adjacente ao aviso que deve ser tratado como um erro.</span><span class="sxs-lookup"><span data-stu-id="51bbb-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51bbb-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51bbb-137">Example</span></span>  
 <span data-ttu-id="51bbb-138">O código a seguir compila `In.vb` e direciona o compilador para exibir um erro para a primeira ocorrência de cada aviso que ele encontre.</span><span class="sxs-lookup"><span data-stu-id="51bbb-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="51bbb-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51bbb-139">Example</span></span>  
 <span data-ttu-id="51bbb-140">O código a seguir compila `T2.vb` e trata apenas o aviso de variáveis locais não utilizadas (42024) como um erro.</span><span class="sxs-lookup"><span data-stu-id="51bbb-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="51bbb-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51bbb-141">See also</span></span>

- [<span data-ttu-id="51bbb-142">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51bbb-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="51bbb-143">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="51bbb-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="51bbb-144">Configurando avisos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51bbb-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
