---
title: Resolução de associação tardia; poderiam ocorrer erros de tempo de execução
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d01164914b484ef689654f048a8743f3c2eb669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="40eda-102">Resolução de associação tardia; poderiam ocorrer erros de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="40eda-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="40eda-103">Um objeto é atribuído a uma variável declarada com o [tipo de dados do objeto](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="40eda-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="40eda-104">Quando você declara uma variável como `Object`, o compilador deve executar *associação tardia*, que faz com que operações extras em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="40eda-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="40eda-105">Ele também expõe seu aplicativo para possíveis erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="40eda-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="40eda-106">Por exemplo, se você atribuir um <xref:System.Windows.Forms.Form> para o `Object` variável e, em seguida, tente acessar o <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> propriedade, o tempo de execução lança uma <xref:System.MemberAccessException> porque o <xref:System.Windows.Forms.Form> classe expõe um `NameTable` propriedade.</span><span class="sxs-lookup"><span data-stu-id="40eda-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="40eda-107">Se você declarar a variável para ser de um tipo específico, o compilador pode executar *associação inicial* em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="40eda-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="40eda-108">Isso resulta em melhor desempenho, acesso controlado para os membros do tipo específico e melhor legibilidade do seu código.</span><span class="sxs-lookup"><span data-stu-id="40eda-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="40eda-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="40eda-109">By default, this message is a warning.</span></span> <span data-ttu-id="40eda-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="40eda-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="40eda-111">**ID do erro:** BC42017</span><span class="sxs-lookup"><span data-stu-id="40eda-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40eda-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="40eda-112">To correct this error</span></span>  
  
-   <span data-ttu-id="40eda-113">Se possível, declare a variável para ser de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="40eda-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40eda-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40eda-114">See Also</span></span>  
 [<span data-ttu-id="40eda-115">Associação Antecipada e Tardia</span><span class="sxs-lookup"><span data-stu-id="40eda-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="40eda-116">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="40eda-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
