---
title: Resolução de associação tardia; poderiam ocorrer erros de tempo de execução
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: af027b7752fdf13f1540010a8ddb681182c1b23c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588773"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="ebfe2-102">Resolução de associação tardia; poderiam ocorrer erros de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ebfe2-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="ebfe2-103">Um objeto é atribuído a uma variável declarada com o [tipo de dados do objeto](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ebfe2-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="ebfe2-104">Quando você declara uma variável como `Object`, o compilador deve executar *associação tardia*, que faz com que operações extras em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="ebfe2-105">Ele também expõe seu aplicativo para possíveis erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="ebfe2-106">Por exemplo, se você atribuir um <xref:System.Windows.Forms.Form> para o `Object` variável e, em seguida, tente acessar o <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> propriedade, o tempo de execução lança uma <xref:System.MemberAccessException> porque o <xref:System.Windows.Forms.Form> classe expõe um `NameTable` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="ebfe2-107">Se você declarar a variável para ser de um tipo específico, o compilador pode executar *associação inicial* em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="ebfe2-108">Isso resulta em melhor desempenho, acesso controlado para os membros do tipo específico e melhor legibilidade do seu código.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="ebfe2-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-109">By default, this message is a warning.</span></span> <span data-ttu-id="ebfe2-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ebfe2-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ebfe2-111">**ID do erro:** BC42017</span><span class="sxs-lookup"><span data-stu-id="ebfe2-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ebfe2-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ebfe2-112">To correct this error</span></span>  
  
-   <span data-ttu-id="ebfe2-113">Se possível, declare a variável para ser de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="ebfe2-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfe2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebfe2-114">See Also</span></span>  
 [<span data-ttu-id="ebfe2-115">Associação Antecipada e Tardia</span><span class="sxs-lookup"><span data-stu-id="ebfe2-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="ebfe2-116">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="ebfe2-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
