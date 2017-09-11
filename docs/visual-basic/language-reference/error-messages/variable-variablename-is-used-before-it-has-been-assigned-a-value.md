---
title: "Variável &quot;&lt;variablename&gt;&quot; é usada antes de receber um valor | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
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
ms.openlocfilehash: dfc924ebbebb8b20654156b8871684dcfad6848a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="62654-102">Variável '&lt;variablename&gt;' é usada antes de receber um valor</span><span class="sxs-lookup"><span data-stu-id="62654-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="62654-103">Variável '\<NOMEDAVARIÁVEL >' é usada antes de receber um valor.</span><span class="sxs-lookup"><span data-stu-id="62654-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="62654-104">Uma exceção de referência nula pode ocorrer em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="62654-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="62654-105">Um aplicativo tem pelo menos um caminho possível pelo seu código que lê uma variável antes que qualquer valor seja atribuído a ele.</span><span class="sxs-lookup"><span data-stu-id="62654-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="62654-106">Se nunca tiver sido atribuída um valor uma variável, ela armazena o valor padrão para seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="62654-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="62654-107">Para um tipo de dados de referência, o valor padrão é [nada](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="62654-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="62654-108">Ler uma variável de referência que tem um valor de `Nothing` pode causar um <xref:System.NullReferenceException>em algumas circunstâncias.</xref:System.NullReferenceException></span><span class="sxs-lookup"><span data-stu-id="62654-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="62654-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="62654-109">By default, this message is a warning.</span></span> <span data-ttu-id="62654-110">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="62654-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="62654-111">**ID do erro:** BC42104</span><span class="sxs-lookup"><span data-stu-id="62654-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62654-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="62654-112">To correct this error</span></span>  
  
-   <span data-ttu-id="62654-113">Verifique sua lógica de fluxo de controle e verifique se que a variável tem um valor válido antes do controle passa para qualquer instrução que lê-lo.</span><span class="sxs-lookup"><span data-stu-id="62654-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="62654-114">Uma maneira de garantir que a variável sempre tem um valor válido é inicializá-la como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="62654-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="62654-115">Consulte "Inicialização" [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62654-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62654-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62654-116">See Also</span></span>  
 <span data-ttu-id="62654-117">[Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="62654-117">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="62654-118"> [Declaração de variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="62654-118"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="62654-119"> [Solução de problemas de Variáveis](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span><span class="sxs-lookup"><span data-stu-id="62654-119"> [Troubleshooting Variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span></span>
