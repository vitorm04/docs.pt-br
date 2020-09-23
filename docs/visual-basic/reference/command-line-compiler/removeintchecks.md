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
ms.openlocfilehash: ce1f24f25ea58cb6ddc2f5c582b6103d8f18d922
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085159"
---
# <a name="-removeintchecks"></a><span data-ttu-id="72ac8-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="72ac8-102">-removeintchecks</span></span>

<span data-ttu-id="72ac8-103">Ativa a verificação de erros de estouro para operações de inteiros.</span><span class="sxs-lookup"><span data-stu-id="72ac8-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ac8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72ac8-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="72ac8-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="72ac8-105">Arguments</span></span>  
  
|<span data-ttu-id="72ac8-106">Termo</span><span class="sxs-lookup"><span data-stu-id="72ac8-106">Term</span></span>|<span data-ttu-id="72ac8-107">Definição</span><span class="sxs-lookup"><span data-stu-id="72ac8-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="72ac8-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="72ac8-108">`+` &#124; `-`</span></span>|<span data-ttu-id="72ac8-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="72ac8-109">Optional.</span></span> <span data-ttu-id="72ac8-110">A `-removeintchecks-` opção faz com que o compilador Verifique todos os cálculos de inteiro para erros de estouro.</span><span class="sxs-lookup"><span data-stu-id="72ac8-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="72ac8-111">O padrão é `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="72ac8-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="72ac8-112">Especificar `-removeintchecks` ou `-removeintchecks+` impedir a verificação de erros e pode fazer cálculos de números inteiros mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="72ac8-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="72ac8-113">No entanto, sem a verificação de erros e se as capacidades de tipo de dados estouram, os resultados incorretos podem ser armazenados sem gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="72ac8-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="72ac8-114">Para Set-removeintchecks no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72ac8-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="72ac8-115">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="72ac8-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="72ac8-116">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="72ac8-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="72ac8-117">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="72ac8-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="72ac8-118">3. Clique no botão **avançado** .</span><span class="sxs-lookup"><span data-stu-id="72ac8-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="72ac8-119">4. modifique o valor da caixa de **verificações remover estouro de inteiro** .</span><span class="sxs-lookup"><span data-stu-id="72ac8-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="72ac8-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72ac8-120">Example</span></span>  

 <span data-ttu-id="72ac8-121">O código a seguir compila `Test.vb` e desativa a verificação de erro de estouro de inteiros.</span><span class="sxs-lookup"><span data-stu-id="72ac8-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="72ac8-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="72ac8-122">See also</span></span>

- [<span data-ttu-id="72ac8-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72ac8-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="72ac8-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="72ac8-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
