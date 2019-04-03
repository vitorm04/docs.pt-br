---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822720"
---
# <a name="-removeintchecks"></a><span data-ttu-id="9062f-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="9062f-102">-removeintchecks</span></span>
<span data-ttu-id="9062f-103">Ativa o erro de estouro para operações de inteiros ou desativar a verificação.</span><span class="sxs-lookup"><span data-stu-id="9062f-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9062f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9062f-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9062f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9062f-105">Arguments</span></span>  
  
|<span data-ttu-id="9062f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="9062f-106">Term</span></span>|<span data-ttu-id="9062f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="9062f-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="9062f-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="9062f-108">`+` &#124; `-`</span></span>|<span data-ttu-id="9062f-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9062f-109">Optional.</span></span> <span data-ttu-id="9062f-110">O `-removeintchecks-` opção faz com que o compilador verifique todos os cálculos de inteiro para erros de estouro.</span><span class="sxs-lookup"><span data-stu-id="9062f-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="9062f-111">O padrão é `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="9062f-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="9062f-112">Especificando `-removeintchecks` ou `-removeintchecks+` impede a verificação de erros e pode fazer cálculos de inteiro mais rápidos.</span><span class="sxs-lookup"><span data-stu-id="9062f-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="9062f-113">No entanto, sem verificação de erro, e se as capacidades de tipo de dados são estouradas, resultados incorretos podem ser armazenados sem gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="9062f-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="9062f-114">Definir - removeintchecks no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9062f-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9062f-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="9062f-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9062f-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9062f-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9062f-117">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="9062f-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9062f-118">3.  Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="9062f-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="9062f-119">4.  Modificar o valor da **remover verificações de estouro de inteiro** caixa.</span><span class="sxs-lookup"><span data-stu-id="9062f-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9062f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9062f-120">Example</span></span>  
 <span data-ttu-id="9062f-121">O seguinte código compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.</span><span class="sxs-lookup"><span data-stu-id="9062f-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9062f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9062f-122">See also</span></span>

- [<span data-ttu-id="9062f-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9062f-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9062f-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="9062f-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
