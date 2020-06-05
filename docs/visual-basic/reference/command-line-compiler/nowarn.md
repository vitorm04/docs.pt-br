---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 37851f99eb88543e939ce48995ded41958e57cc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397482"
---
# <a name="-nowarn"></a><span data-ttu-id="d88f9-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="d88f9-102">-nowarn</span></span>
<span data-ttu-id="d88f9-103">Suprime a capacidade do compilador de gerar avisos.</span><span class="sxs-lookup"><span data-stu-id="d88f9-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d88f9-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d88f9-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d88f9-105">Arguments</span></span>  
  
|<span data-ttu-id="d88f9-106">Termo</span><span class="sxs-lookup"><span data-stu-id="d88f9-106">Term</span></span>|<span data-ttu-id="d88f9-107">Definição</span><span class="sxs-lookup"><span data-stu-id="d88f9-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="d88f9-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d88f9-108">Optional.</span></span> <span data-ttu-id="d88f9-109">Lista delimitada por vírgulas dos números de ID de aviso que o compilador deve suprimir.</span><span class="sxs-lookup"><span data-stu-id="d88f9-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="d88f9-110">Se as IDs de aviso não forem especificadas, todos os avisos serão suprimidos.</span><span class="sxs-lookup"><span data-stu-id="d88f9-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d88f9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d88f9-111">Remarks</span></span>  
 <span data-ttu-id="d88f9-112">A `-nowarn` opção faz com que o compilador não gere avisos.</span><span class="sxs-lookup"><span data-stu-id="d88f9-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="d88f9-113">Para suprimir um aviso individual, forneça a ID de aviso à `-nowarn` opção após os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="d88f9-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="d88f9-114">Separe vários números de aviso com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d88f9-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="d88f9-115">Você precisa especificar apenas a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="d88f9-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="d88f9-116">Por exemplo, se você quiser suprimir BC42024, o aviso para variáveis locais não utilizadas, especifique `-nowarn:42024` .</span><span class="sxs-lookup"><span data-stu-id="d88f9-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="d88f9-117">Para obter mais informações sobre os números de identificação de aviso, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d88f9-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="d88f9-118">Para definir-nowarn no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d88f9-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d88f9-119">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="d88f9-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d88f9-120">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d88f9-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d88f9-121">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="d88f9-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d88f9-122">3. Marque a caixa de seleção **desabilitar todos os avisos** para desabilitar todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="d88f9-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="d88f9-123">- ou -</span><span class="sxs-lookup"><span data-stu-id="d88f9-123">- or -</span></span><br />     <span data-ttu-id="d88f9-124">Para desabilitar um aviso específico, clique em **nenhum** na lista suspensa adjacente ao aviso.</span><span class="sxs-lookup"><span data-stu-id="d88f9-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d88f9-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d88f9-125">Example</span></span>  
 <span data-ttu-id="d88f9-126">O código a seguir compila `T2.vb` e não exibe nenhum aviso.</span><span class="sxs-lookup"><span data-stu-id="d88f9-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="d88f9-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d88f9-127">Example</span></span>  
 <span data-ttu-id="d88f9-128">O código a seguir compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).</span><span class="sxs-lookup"><span data-stu-id="d88f9-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d88f9-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="d88f9-129">See also</span></span>

- [<span data-ttu-id="d88f9-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d88f9-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d88f9-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d88f9-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="d88f9-132">Configurando avisos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d88f9-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
