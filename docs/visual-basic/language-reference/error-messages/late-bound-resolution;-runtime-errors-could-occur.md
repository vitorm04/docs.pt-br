---
title: "Resolução de ligação tardia; poderão ocorrer erros de tempo de execução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
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
ms.openlocfilehash: 3baf28a17077d255b42f38ade21ce6153c24e862
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="4a5cc-102">Resolução de associação tardia; poderiam ocorrer erros de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4a5cc-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="4a5cc-103">Um objeto é atribuído a uma variável declarada com o [tipo de dados do objeto](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4a5cc-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="4a5cc-104">Ao declarar uma variável como `Object`, o compilador deve executar *ligação tardia*, que causa operações extras em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4a5cc-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="4a5cc-105">Ele também expõe sua aplicação a potenciais erros em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4a5cc-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="4a5cc-106">Por exemplo, se você atribuir um <xref:System.Windows.Forms.Form>para o `Object` variável e, em seguida, tente acessar o <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>propriedade, o tempo de execução gera um <xref:System.MemberAccessException>porque o <xref:System.Windows.Forms.Form>classe expõe um `NameTable` propriedade.</xref:System.Windows.Forms.Form> </xref:System.MemberAccessException> </xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> </xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="4a5cc-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="4a5cc-107">Se você declarar a variável para ser de um tipo específico, o compilador pode executar *vinculação inicial* em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="4a5cc-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="4a5cc-108">Isso resulta em melhor desempenho, acesso controlado aos membros do tipo específico e melhor legibilidade do seu código.</span><span class="sxs-lookup"><span data-stu-id="4a5cc-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="4a5cc-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="4a5cc-109">By default, this message is a warning.</span></span> <span data-ttu-id="4a5cc-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4a5cc-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4a5cc-111">**ID do erro:** BC42017</span><span class="sxs-lookup"><span data-stu-id="4a5cc-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a5cc-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4a5cc-112">To correct this error</span></span>  
  
-   <span data-ttu-id="4a5cc-113">Se possível, declare a variável para ser de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="4a5cc-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5cc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a5cc-114">See Also</span></span>  
 <span data-ttu-id="4a5cc-115">[Associação antecipada e tardia](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span><span class="sxs-lookup"><span data-stu-id="4a5cc-115">[Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span></span>  
<span data-ttu-id="4a5cc-116"> [Declaração de Variável do Objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span><span class="sxs-lookup"><span data-stu-id="4a5cc-116"> [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span></span>
