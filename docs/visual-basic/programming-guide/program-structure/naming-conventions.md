---
title: Convenções de nomenclatura do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 46f59403feced4baafef4662065cb7daedbeaa7b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837072"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="2b002-102">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b002-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="2b002-103">Quando você nomeia um elemento em seu aplicativo Visual Basic, o primeiro caractere do nome deve ser um caractere alfabético ou sublinhado.</span><span class="sxs-lookup"><span data-stu-id="2b002-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="2b002-104">No entanto, observe que os nomes que começam com um sublinhado não são compatíveis com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="2b002-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="2b002-105">As sugestões a seguir se aplicam a nomenclatura.</span><span class="sxs-lookup"><span data-stu-id="2b002-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="2b002-106">Inicie cada palavra separada um nome com uma letra maiuscula, como em `FindLastRecord` e `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="2b002-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="2b002-107">Comece nomes de função e método com um verbo, como em `InitNameArray` ou `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="2b002-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="2b002-108">Comece a classe, estrutura, módulo e nomes de propriedade com um substantivo, como em `EmployeeName` ou `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="2b002-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="2b002-109">Comece nomes de interface com o prefixo "I", seguido por um substantivo ou uma frase substantiva, como `IComponent`, ou com um adjetivo que descreve o comportamento da interface, como `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="2b002-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="2b002-110">Não use o sublinhado e use abreviações com moderação, pois abreviações podem causar confusão.</span><span class="sxs-lookup"><span data-stu-id="2b002-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="2b002-111">Comece nomes de manipulador de eventos com um substantivo que descreve o tipo de evento seguido de "`EventHandler`"sufixo, como em"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="2b002-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="2b002-112">Em nomes de classes de argumento de evento, inclua o "`EventArgs`" sufixo.</span><span class="sxs-lookup"><span data-stu-id="2b002-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="2b002-113">Se um evento tem um conceito de "antes" ou "after", use um sufixo no presente ou no passado, como em "`ControlAdd`"ou"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="2b002-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="2b002-114">Para termos longos ou usados com frequência, use abreviações para manter os tamanhos de nome razoável, por exemplo, "HTML", em vez de "Hypertext Markup Language".</span><span class="sxs-lookup"><span data-stu-id="2b002-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="2b002-115">Em geral, nomes de variáveis maiores do que 32 caracteres são difíceis de ler em um monitor definido para uma baixa resolução.</span><span class="sxs-lookup"><span data-stu-id="2b002-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="2b002-116">Além disso, certifique-se de que suas abreviações são consistentes em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2b002-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="2b002-117">Alternar aleatoriamente em um projeto entre "HTML" e "Hypertext Markup Language" pode causar confusão.</span><span class="sxs-lookup"><span data-stu-id="2b002-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="2b002-118">Evite usar nomes em um escopo interno que são os mesmos nomes em um escopo externo.</span><span class="sxs-lookup"><span data-stu-id="2b002-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="2b002-119">Erros podem ocorrer se a variável errada é acessada.</span><span class="sxs-lookup"><span data-stu-id="2b002-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="2b002-120">Se ocorrer um conflito entre uma variável e a palavra-chave do mesmo nome, você deve identificar a palavra-chave, precedendo-o com a biblioteca de tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="2b002-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="2b002-121">Por exemplo, se você tiver uma variável chamada `Date`, você pode usar o intrínseco `Date` função apenas chamando <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2b002-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b002-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b002-122">See also</span></span>

- [<span data-ttu-id="2b002-123">Palavras-chave como Nomes de Elemento em Código</span><span class="sxs-lookup"><span data-stu-id="2b002-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="2b002-124">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="2b002-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="2b002-125">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="2b002-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="2b002-126">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="2b002-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="2b002-127">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b002-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
