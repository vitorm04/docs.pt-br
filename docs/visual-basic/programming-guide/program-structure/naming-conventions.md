---
title: "Convenções de nomenclatura do Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- names, Visual Basic rules
- naming conventions
- naming conventions, Visual Basic
- Visual Basic code, naming conventions
- conventions, Visual Basic coding
- names, naming conventions
- naming conventions, classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
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
ms.openlocfilehash: 638779fa507ed8e3b0aa0956426365833313b920
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="c0af2-102">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0af2-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="c0af2-103">Quando você nomeia um elemento em seu aplicativo Visual Basic, o primeiro caractere do nome deve ser um caractere alfabético ou um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="c0af2-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="c0af2-104">Observe, entretanto, que nomes que começam com um sublinhado não são compatíveis com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span><span class="sxs-lookup"><span data-stu-id="c0af2-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span>  
  
 <span data-ttu-id="c0af2-105">As sugestões a seguir se aplicam à nomeação.</span><span class="sxs-lookup"><span data-stu-id="c0af2-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="c0af2-106">Inicie cada palavra separada um nome com uma letra maiuscula, como em `FindLastRecord` e `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="c0af2-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="c0af2-107">Comece nomes de função e método com um verbo, como em `InitNameArray` ou `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="c0af2-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="c0af2-108">Comece a classe, estrutura, módulo e nomes de propriedade com um substantivo, como em `EmployeeName` ou `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="c0af2-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="c0af2-109">Inicie nomes de interfaces com o prefixo "I", seguido por um substantivo ou uma frase substantiva, como `IComponent`, ou com um adjetivo que descreve o comportamento da interface, como `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="c0af2-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="c0af2-110">Não use o sublinhado e use abreviações com parcimônia, porque as abreviações podem causar confusão.</span><span class="sxs-lookup"><span data-stu-id="c0af2-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="c0af2-111">Comece nomes de manipuladores de eventos com um substantivo que descreve o tipo de evento seguido de "`EventHandler`"sufixo, como em"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="c0af2-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="c0af2-112">Em nomes de classes de argumento de evento, inclua o "`EventArgs`" sufixo.</span><span class="sxs-lookup"><span data-stu-id="c0af2-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="c0af2-113">Se um evento possui um conceito de "antes" ou "depois", use um sufixo no presente ou no passado, como em "`ControlAdd`"ou"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="c0af2-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="c0af2-114">Para termos longos ou usados com frequência, use abreviações para manter comprimentos de nome razoáveis, por exemplo, "HTML", em vez de "Hypertext Markup Language".</span><span class="sxs-lookup"><span data-stu-id="c0af2-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="c0af2-115">Em geral, nomes de variáveis com mais de 32 caracteres são difíceis de ler em um monitor definido para uma resolução baixa.</span><span class="sxs-lookup"><span data-stu-id="c0af2-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="c0af2-116">Além disso, certifique-se de que suas abreviações são consistentes em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0af2-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="c0af2-117">Alternar aleatoriamente em um projeto entre "HTML" e "Hypertext Markup Language" pode levar a confusão.</span><span class="sxs-lookup"><span data-stu-id="c0af2-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="c0af2-118">Evite usar nomes em um escopo interno que sejam os mesmos nomes em um escopo externo.</span><span class="sxs-lookup"><span data-stu-id="c0af2-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="c0af2-119">Erros podem ocorrer se a variável errada é acessada.</span><span class="sxs-lookup"><span data-stu-id="c0af2-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="c0af2-120">Se ocorrer um conflito entre uma variável e a palavra-chave de mesmo nome, você deve identificar a palavra-chave precedendo-o com a biblioteca de tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="c0af2-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="c0af2-121">Por exemplo, se você tiver uma variável chamada `Date`, você pode usar o intrínseco `Date` função chamando <xref:System.DateTime.Date%2A?displayProperty=fullName>.</xref:System.DateTime.Date%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c0af2-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=fullName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0af2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0af2-122">See Also</span></span>  
 <span data-ttu-id="c0af2-123">[Palavras-chave como nomes de elementos em código](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md) </span><span class="sxs-lookup"><span data-stu-id="c0af2-123">[Keywords as Element Names in Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md) </span></span>  
<span data-ttu-id="c0af2-124"> [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span><span class="sxs-lookup"><span data-stu-id="c0af2-124"> [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span></span>  
<span data-ttu-id="c0af2-125"> [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="c0af2-125"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="c0af2-126"> [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="c0af2-126"> [Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="c0af2-127"> [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)</span><span class="sxs-lookup"><span data-stu-id="c0af2-127"> [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)</span></span>
