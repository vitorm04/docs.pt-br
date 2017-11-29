---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a><span data-ttu-id="2cbd4-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="2cbd4-102">/nowarn</span></span>
<span data-ttu-id="2cbd4-103">Suprime a capacidade do compilador para gerar avisos.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cbd4-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cbd4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2cbd4-105">Arguments</span></span>  
  
|<span data-ttu-id="2cbd4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="2cbd4-106">Term</span></span>|<span data-ttu-id="2cbd4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="2cbd4-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="2cbd4-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-108">Optional.</span></span> <span data-ttu-id="2cbd4-109">Lista delimitada por vírgulas de números de ID de aviso que o compilador deve eliminar.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="2cbd4-110">Se o aviso identificações não for especificado, todos os avisos são suprimidos.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cbd4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cbd4-111">Remarks</span></span>  
 <span data-ttu-id="2cbd4-112">O `/nowarn` opção faz com que o compilador não gere avisos.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="2cbd4-113">Para suprimir um aviso individual, forneça a ID do aviso para o `/nowarn` opção após os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="2cbd4-114">Separe vários números de aviso com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="2cbd4-115">Você precisa especificar somente a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="2cbd4-116">Por exemplo, se você desejar suprimir BC42024, o aviso para variáveis locais não utilizados, especificar `/nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="2cbd4-117">Para obter mais informações sobre os números de ID de aviso, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2cbd4-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="2cbd4-118">Para definir /nowarn no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="2cbd4-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="2cbd4-119">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2cbd4-120">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="2cbd4-121">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="2cbd4-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="2cbd4-122">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="2cbd4-123">3.  Selecione o **desativar todos os avisos** caixa de seleção para desativar todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="2cbd4-124">- ou -</span><span class="sxs-lookup"><span data-stu-id="2cbd4-124">- or -</span></span><br />     <span data-ttu-id="2cbd4-125">Para desativar um aviso específico, clique em **nenhum** da lista suspensa adjacente ao aviso.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2cbd4-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cbd4-126">Example</span></span>  
 <span data-ttu-id="2cbd4-127">O código a seguir compila `T2.vb` e não exibe avisos.</span><span class="sxs-lookup"><span data-stu-id="2cbd4-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="2cbd4-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cbd4-128">Example</span></span>  
 <span data-ttu-id="2cbd4-129">O código a seguir compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).</span><span class="sxs-lookup"><span data-stu-id="2cbd4-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cbd4-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cbd4-130">See Also</span></span>  
 [<span data-ttu-id="2cbd4-131">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2cbd4-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2cbd4-132">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cbd4-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="2cbd4-133">Configurando avisos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2cbd4-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
