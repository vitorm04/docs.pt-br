---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 917977d8e5e12c231370ab3c956aca9d96e8a8a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="5d0e9-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="5d0e9-102">/removeintchecks</span></span>
<span data-ttu-id="5d0e9-103">Ativa para operações de inteiro ou desativar a verificação de erro de estouro.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d0e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d0e9-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d0e9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5d0e9-105">Arguments</span></span>  
  
|<span data-ttu-id="5d0e9-106">Termo</span><span class="sxs-lookup"><span data-stu-id="5d0e9-106">Term</span></span>|<span data-ttu-id="5d0e9-107">Definição</span><span class="sxs-lookup"><span data-stu-id="5d0e9-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="5d0e9-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5d0e9-108">`+` &#124; `-`</span></span>|<span data-ttu-id="5d0e9-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-109">Optional.</span></span> <span data-ttu-id="5d0e9-110">O `/removeintchecks-` opção faz com que o compilador verificar se todos os cálculos de inteiros para erros de estouro.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="5d0e9-111">O padrão é `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="5d0e9-112">Especificando `/removeintchecks` ou `/removeintchecks+` impede a verificação de erro e pode fazer os cálculos de inteiros mais rápidos.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="5d0e9-113">No entanto, sem a verificação de erros, e se as capacidades de tipo de dados são estourou, resultados incorretos podem ser armazenados sem gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="5d0e9-114">Para definir /removeintchecks no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="5d0e9-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="5d0e9-115">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5d0e9-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="5d0e9-117">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="5d0e9-118">3.  Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="5d0e9-119">4.  Modificar o valor da **remover verificações de estouro de inteiro** caixa.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5d0e9-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d0e9-120">Example</span></span>  
 <span data-ttu-id="5d0e9-121">O código a seguir compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.</span><span class="sxs-lookup"><span data-stu-id="5d0e9-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d0e9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d0e9-122">See Also</span></span>  
 [<span data-ttu-id="5d0e9-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d0e9-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5d0e9-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d0e9-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
