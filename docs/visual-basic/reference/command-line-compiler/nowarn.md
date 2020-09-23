---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: cde96fff975a65d6303ee62e6a811bfd83d5ff97
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097677"
---
# <a name="-nowarn"></a><span data-ttu-id="55049-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="55049-102">-nowarn</span></span>

<span data-ttu-id="55049-103">Suprime a capacidade do compilador de gerar avisos.</span><span class="sxs-lookup"><span data-stu-id="55049-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55049-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55049-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="55049-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="55049-105">Arguments</span></span>  
  
|<span data-ttu-id="55049-106">Termo</span><span class="sxs-lookup"><span data-stu-id="55049-106">Term</span></span>|<span data-ttu-id="55049-107">Definição</span><span class="sxs-lookup"><span data-stu-id="55049-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="55049-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="55049-108">Optional.</span></span> <span data-ttu-id="55049-109">Lista delimitada por vírgulas dos números de ID de aviso que o compilador deve suprimir.</span><span class="sxs-lookup"><span data-stu-id="55049-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="55049-110">Se as IDs de aviso não forem especificadas, todos os avisos serão suprimidos.</span><span class="sxs-lookup"><span data-stu-id="55049-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55049-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="55049-111">Remarks</span></span>  

 <span data-ttu-id="55049-112">A `-nowarn` opção faz com que o compilador não gere avisos.</span><span class="sxs-lookup"><span data-stu-id="55049-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="55049-113">Para suprimir um aviso individual, forneça a ID de aviso à `-nowarn` opção após os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="55049-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="55049-114">Separe vários números de aviso com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="55049-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="55049-115">Você precisa especificar apenas a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="55049-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="55049-116">Por exemplo, se você quiser suprimir BC42024, o aviso para variáveis locais não utilizadas, especifique `-nowarn:42024` .</span><span class="sxs-lookup"><span data-stu-id="55049-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="55049-117">Para obter mais informações sobre os números de identificação de aviso, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="55049-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="55049-118">Para definir-nowarn no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="55049-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="55049-119">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="55049-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="55049-120">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="55049-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="55049-121">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="55049-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="55049-122">3. Marque a caixa de seleção **desabilitar todos os avisos** para desabilitar todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="55049-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="55049-123">- ou -</span><span class="sxs-lookup"><span data-stu-id="55049-123">- or -</span></span><br />     <span data-ttu-id="55049-124">Para desabilitar um aviso específico, clique em **nenhum** na lista suspensa adjacente ao aviso.</span><span class="sxs-lookup"><span data-stu-id="55049-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="55049-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55049-125">Example</span></span>  

 <span data-ttu-id="55049-126">O código a seguir compila `T2.vb` e não exibe nenhum aviso.</span><span class="sxs-lookup"><span data-stu-id="55049-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="55049-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55049-127">Example</span></span>  

 <span data-ttu-id="55049-128">O código a seguir compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).</span><span class="sxs-lookup"><span data-stu-id="55049-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="55049-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="55049-129">See also</span></span>

- [<span data-ttu-id="55049-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55049-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="55049-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="55049-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="55049-132">Configurando avisos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55049-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
