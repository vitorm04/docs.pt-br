---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 880fdf4931dadea547d64d0506bd3e978956468e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005404"
---
# <a name="-nowarn"></a><span data-ttu-id="7d6bf-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="7d6bf-102">-nowarn</span></span>
<span data-ttu-id="7d6bf-103">Suprime a capacidade do compilador de gerar avisos.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d6bf-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d6bf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d6bf-105">Arguments</span></span>  
  
|<span data-ttu-id="7d6bf-106">Termo</span><span class="sxs-lookup"><span data-stu-id="7d6bf-106">Term</span></span>|<span data-ttu-id="7d6bf-107">Definição</span><span class="sxs-lookup"><span data-stu-id="7d6bf-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="7d6bf-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-108">Optional.</span></span> <span data-ttu-id="7d6bf-109">Lista delimitada por vírgulas dos números de ID de aviso que o compilador deve suprimir.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="7d6bf-110">Se as IDs de aviso não forem especificadas, todos os avisos serão suprimidos.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d6bf-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d6bf-111">Remarks</span></span>  
 <span data-ttu-id="7d6bf-112">A opção `-nowarn` faz com que o compilador não gere avisos.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="7d6bf-113">Para suprimir um aviso individual, forneça a ID de aviso à opção `-nowarn` após os dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="7d6bf-114">Separe vários números de aviso com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="7d6bf-115">Você precisa especificar apenas a parte numérica do identificador de aviso.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="7d6bf-116">Por exemplo, se você quiser suprimir BC42024, o aviso para variáveis locais não usadas, especifique `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="7d6bf-117">Para obter mais informações sobre os números de identificação de aviso, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7d6bf-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="7d6bf-118">Para definir-nowarn no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d6bf-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="7d6bf-119">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7d6bf-120">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7d6bf-121">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7d6bf-122">3.  Marque a caixa de seleção **desabilitar todos os avisos** para desabilitar todos os avisos.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="7d6bf-123">- ou -</span><span class="sxs-lookup"><span data-stu-id="7d6bf-123">- or -</span></span><br />     <span data-ttu-id="7d6bf-124">Para desabilitar um aviso específico, clique em **nenhum** na lista suspensa adjacente ao aviso.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d6bf-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d6bf-125">Example</span></span>  
 <span data-ttu-id="7d6bf-126">O código a seguir compila `T2.vb` e não exibe nenhum aviso.</span><span class="sxs-lookup"><span data-stu-id="7d6bf-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="7d6bf-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d6bf-127">Example</span></span>  
 <span data-ttu-id="7d6bf-128">O código a seguir compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).</span><span class="sxs-lookup"><span data-stu-id="7d6bf-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d6bf-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d6bf-129">See also</span></span>

- [<span data-ttu-id="7d6bf-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d6bf-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7d6bf-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d6bf-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="7d6bf-132">Configurando avisos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d6bf-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
