---
title: /nowarn | Documentos do Microsoft
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
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 308bf24c2a397a75f36b97062dde7380b90c8994
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="nowarn"></a><span data-ttu-id="db467-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="db467-102">/nowarn</span></span>
<span data-ttu-id="db467-103">Suprime a capacidade do compilador para gerar avisos.</span><span class="sxs-lookup"><span data-stu-id="db467-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db467-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db467-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="db467-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="db467-105">Arguments</span></span>  
  
|<span data-ttu-id="db467-106">Termo</span><span class="sxs-lookup"><span data-stu-id="db467-106">Term</span></span>|<span data-ttu-id="db467-107">Definição</span><span class="sxs-lookup"><span data-stu-id="db467-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="db467-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="db467-108">Optional.</span></span> <span data-ttu-id="db467-109">Lista delimitada por vírgula dos números de identificação de aviso que o compilador deve eliminar.</span><span class="sxs-lookup"><span data-stu-id="db467-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="db467-110">Se o aviso identificações não for especificado, todos os avisos são suprimidos.</span><span class="sxs-lookup"><span data-stu-id="db467-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db467-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="db467-111">Remarks</span></span>  
 <span data-ttu-id="db467-112">O `/nowarn` opção faz com que o compilador não gere avisos.</span><span class="sxs-lookup"><span data-stu-id="db467-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="db467-113">Para suprimir um aviso individual, forneça a identificação de aviso para o `/nowarn` opção após os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="db467-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="db467-114">Separe vários números de aviso com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="db467-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="db467-115">Você precisa especificar somente a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="db467-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="db467-116">Por exemplo, se você desejar suprimir BC42024, o aviso para variáveis locais não utilizados, especificar `/nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="db467-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="db467-117">Para obter mais informações sobre os números de identificação de aviso, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="db467-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="db467-118">Para definir /nowarn no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="db467-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="db467-119">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="db467-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="db467-120">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="db467-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="db467-121">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="db467-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="db467-122">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="db467-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="db467-123">3.  Selecione o **desativar todos os avisos** caixa de seleção para desativar todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="db467-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="db467-124">- ou -</span><span class="sxs-lookup"><span data-stu-id="db467-124">- or -</span></span><br />     <span data-ttu-id="db467-125">Para desativar um aviso específico, clique em **nenhum** da lista suspensa adjacente para o aviso.</span><span class="sxs-lookup"><span data-stu-id="db467-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db467-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db467-126">Example</span></span>  
 <span data-ttu-id="db467-127">O seguinte código compila `T2.vb` e não exibe avisos.</span><span class="sxs-lookup"><span data-stu-id="db467-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="db467-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db467-128">Example</span></span>  
 <span data-ttu-id="db467-129">O seguinte código compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).</span><span class="sxs-lookup"><span data-stu-id="db467-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="db467-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db467-130">See Also</span></span>  
 <span data-ttu-id="db467-131">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="db467-131">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="db467-132"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="db467-132"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="db467-133"> [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="db467-133"> [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)</span></span>
