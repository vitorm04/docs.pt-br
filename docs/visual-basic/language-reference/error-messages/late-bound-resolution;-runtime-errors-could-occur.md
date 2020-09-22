---
title: Resolução de associação tardia; poderiam ocorrer erros de runtime
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 1c7b352c7bd61216ecce9901585945e740428ee3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873857"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="f98f9-102">Resolução de associação tardia; poderiam ocorrer erros de runtime</span><span class="sxs-lookup"><span data-stu-id="f98f9-102">Late bound resolution; runtime errors could occur</span></span>

<span data-ttu-id="f98f9-103">Um objeto é atribuído a uma variável declarada para ser do [tipo de dados Object](../data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="f98f9-103">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="f98f9-104">Quando você declara uma variável como `Object` , o compilador deve executar a *associação tardia*, o que causa operações extras em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f98f9-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="f98f9-105">Ele também expõe seu aplicativo a possíveis erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f98f9-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="f98f9-106">Por exemplo, se você atribuir um <xref:System.Windows.Forms.Form> à `Object` variável e, em seguida, tentar acessar a <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> propriedade, o tempo de execução lançará um <xref:System.MemberAccessException> porque a <xref:System.Windows.Forms.Form> classe não expõe uma `NameTable` propriedade.</span><span class="sxs-lookup"><span data-stu-id="f98f9-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="f98f9-107">Se você declarar a variável para ser de um tipo específico, o compilador poderá executar a *ligação antecipada* no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="f98f9-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="f98f9-108">Isso resulta em desempenho aprimorado, acesso controlado aos membros do tipo específico e melhor legibilidade do seu código.</span><span class="sxs-lookup"><span data-stu-id="f98f9-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="f98f9-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="f98f9-109">By default, this message is a warning.</span></span> <span data-ttu-id="f98f9-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f98f9-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f98f9-111">**ID do erro:** BC42017</span><span class="sxs-lookup"><span data-stu-id="f98f9-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f98f9-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f98f9-112">To correct this error</span></span>  
  
- <span data-ttu-id="f98f9-113">Se possível, declare a variável para ser de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="f98f9-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f98f9-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="f98f9-114">See also</span></span>

- [<span data-ttu-id="f98f9-115">Associação antecipada e tardia</span><span class="sxs-lookup"><span data-stu-id="f98f9-115">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="f98f9-116">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="f98f9-116">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
