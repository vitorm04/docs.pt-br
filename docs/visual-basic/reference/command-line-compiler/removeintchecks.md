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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005234"
---
# <a name="-removeintchecks"></a><span data-ttu-id="b4f2e-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="b4f2e-102">-removeintchecks</span></span>
<span data-ttu-id="b4f2e-103">Ativa a verificação de erros de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4f2e-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4f2e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4f2e-105">Arguments</span></span>  
  
|<span data-ttu-id="b4f2e-106">Termo</span><span class="sxs-lookup"><span data-stu-id="b4f2e-106">Term</span></span>|<span data-ttu-id="b4f2e-107">Definição</span><span class="sxs-lookup"><span data-stu-id="b4f2e-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="b4f2e-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b4f2e-108">`+` &#124; `-`</span></span>|<span data-ttu-id="b4f2e-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-109">Optional.</span></span> <span data-ttu-id="b4f2e-110">A opção `-removeintchecks-` faz com que o compilador Verifique todos os cálculos de inteiro para erros de estouro.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="b4f2e-111">O padrão é `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="b4f2e-112">Especificar `-removeintchecks` ou `-removeintchecks+` impede a verificação de erros e pode fazer cálculos de números inteiros mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="b4f2e-113">No entanto, sem a verificação de erros e se as capacidades de tipo de dados estouram, os resultados incorretos podem ser armazenados sem gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="b4f2e-114">Para Set-removeintchecks no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4f2e-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="b4f2e-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b4f2e-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="b4f2e-117">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="b4f2e-118">3.  Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="b4f2e-119">4.  Modifique o valor da caixa de **verificações remover estouro de inteiro** .</span><span class="sxs-lookup"><span data-stu-id="b4f2e-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b4f2e-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4f2e-120">Example</span></span>  
 <span data-ttu-id="b4f2e-121">O código a seguir compila `Test.vb` e desativa a verificação de erro de estouro de inteiros.</span><span class="sxs-lookup"><span data-stu-id="b4f2e-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4f2e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4f2e-122">See also</span></span>

- [<span data-ttu-id="b4f2e-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4f2e-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b4f2e-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4f2e-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
