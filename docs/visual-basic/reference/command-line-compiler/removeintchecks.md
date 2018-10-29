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
ms.openlocfilehash: f061497083dc23fd07f61108938a4129c0af5f3a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188515"
---
# <a name="-removeintchecks"></a><span data-ttu-id="21785-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="21785-102">-removeintchecks</span></span>
<span data-ttu-id="21785-103">Ativa o erro de estouro para operações de inteiros ou desativar a verificação.</span><span class="sxs-lookup"><span data-stu-id="21785-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21785-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21785-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="21785-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="21785-105">Arguments</span></span>  
  
|<span data-ttu-id="21785-106">Termo</span><span class="sxs-lookup"><span data-stu-id="21785-106">Term</span></span>|<span data-ttu-id="21785-107">Definição</span><span class="sxs-lookup"><span data-stu-id="21785-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="21785-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="21785-108">`+` &#124; `-`</span></span>|<span data-ttu-id="21785-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="21785-109">Optional.</span></span> <span data-ttu-id="21785-110">O `-removeintchecks-` opção faz com que o compilador verifique todos os cálculos de inteiro para erros de estouro.</span><span class="sxs-lookup"><span data-stu-id="21785-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="21785-111">O padrão é `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="21785-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="21785-112">Especificando `-removeintchecks` ou `-removeintchecks+` impede a verificação de erros e pode fazer cálculos de inteiro mais rápidos.</span><span class="sxs-lookup"><span data-stu-id="21785-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="21785-113">No entanto, sem verificação de erro, e se as capacidades de tipo de dados são estouradas, resultados incorretos podem ser armazenados sem gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="21785-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="21785-114">Definir - removeintchecks no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21785-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="21785-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="21785-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="21785-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="21785-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="21785-117">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="21785-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="21785-118">3.  Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="21785-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="21785-119">4.  Modificar o valor da **remover verificações de estouro de inteiro** caixa.</span><span class="sxs-lookup"><span data-stu-id="21785-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="21785-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21785-120">Example</span></span>  
 <span data-ttu-id="21785-121">O seguinte código compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.</span><span class="sxs-lookup"><span data-stu-id="21785-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="21785-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21785-122">See Also</span></span>  
 [<span data-ttu-id="21785-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21785-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="21785-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="21785-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
