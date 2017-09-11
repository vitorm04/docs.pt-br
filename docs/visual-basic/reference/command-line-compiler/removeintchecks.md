---
title: /removeintchecks | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
dev_langs:
- VB
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
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
ms.openlocfilehash: 25f67774238c6e9a6b3a2c50b3702e43d5a6374c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="removeintchecks"></a><span data-ttu-id="1a7b0-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="1a7b0-102">/removeintchecks</span></span>
<span data-ttu-id="1a7b0-103">Ativa para operações de inteiros ou desativar a verificação de erro de estouro.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a7b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a7b0-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a7b0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1a7b0-105">Arguments</span></span>  
  
|<span data-ttu-id="1a7b0-106">Termo</span><span class="sxs-lookup"><span data-stu-id="1a7b0-106">Term</span></span>|<span data-ttu-id="1a7b0-107">Definição</span><span class="sxs-lookup"><span data-stu-id="1a7b0-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1a7b0-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1a7b0-108">`+` &#124; `-`</span></span>|<span data-ttu-id="1a7b0-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-109">Optional.</span></span> <span data-ttu-id="1a7b0-110">O `/removeintchecks-` opção faz com que o compilador verifique todos os cálculos de número inteiro para erros de estouro.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="1a7b0-111">O padrão é `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="1a7b0-112">Especificando `/removeintchecks` ou `/removeintchecks+` impede a verificação de erros e pode fazer cálculos de número inteiro mais rápidos.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="1a7b0-113">No entanto, sem a verificação de erros, e se estão estourou capacidades de tipo de dados, os resultados incorretos podem ser armazenados sem gerar um erro.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="1a7b0-114">Para definir /removeintchecks no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="1a7b0-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1a7b0-115">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1a7b0-116">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1a7b0-117">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1a7b0-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1a7b0-118">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1a7b0-119">3.  Clique o **avançado** botão.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="1a7b0-120">4.  Modificar o valor da **remover verificação de estouro de inteiro** caixa.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1a7b0-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a7b0-121">Example</span></span>  
 <span data-ttu-id="1a7b0-122">O seguinte código compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.</span><span class="sxs-lookup"><span data-stu-id="1a7b0-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a7b0-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a7b0-123">See Also</span></span>  
 <span data-ttu-id="1a7b0-124">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="1a7b0-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="1a7b0-125"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="1a7b0-125"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
