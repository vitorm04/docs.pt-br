---
title: Convenções de nomenclatura
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
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347316"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="80d92-102">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80d92-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="80d92-103">Quando você nomear um elemento em seu aplicativo Visual Basic, o primeiro caractere desse nome deverá ser um caractere alfabético ou um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="80d92-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="80d92-104">Observe, no entanto, que os nomes que começam com um sublinhado não são compatíveis com a [independência de idioma e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="80d92-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="80d92-105">As sugestões a seguir se aplicam à nomenclatura.</span><span class="sxs-lookup"><span data-stu-id="80d92-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="80d92-106">Comece cada palavra separada em um nome com uma letra maiúscula, como em `FindLastRecord` e `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="80d92-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="80d92-107">Inicie os nomes de função e método com um verbo, como em `InitNameArray` ou `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="80d92-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="80d92-108">Comece os nomes de classe, estrutura, módulo e propriedade com um substantivo, como em `EmployeeName` ou `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="80d92-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="80d92-109">Comece os nomes de interface com o prefixo "I", seguido por um substantivo ou uma frase substantivo, como `IComponent`, ou com um adjetivo que descreve o comportamento da interface, como `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="80d92-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="80d92-110">Não use o sublinhado e use abreviações com moderação, pois as abreviações podem causar confusão.</span><span class="sxs-lookup"><span data-stu-id="80d92-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="80d92-111">Inicie os nomes do manipulador de eventos com um substantivo que descreve o tipo de evento seguido pelo sufixo "`EventHandler`", como em "`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="80d92-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="80d92-112">Em nomes de classes de argumento de evento, inclua o sufixo "`EventArgs`".</span><span class="sxs-lookup"><span data-stu-id="80d92-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="80d92-113">Se um evento tiver um conceito de "antes" ou "depois", use um sufixo no conjugação presente ou anterior, como em "`ControlAdd`" ou "`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="80d92-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="80d92-114">Para termos longos ou usados com frequência, use abreviações para manter os comprimentos de nome razoáveis, por exemplo, "HTML", em vez de "linguagem HTML".</span><span class="sxs-lookup"><span data-stu-id="80d92-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="80d92-115">Em geral, é difícil ler nomes de variáveis com mais de 32 caracteres em um monitor definido como uma baixa resolução.</span><span class="sxs-lookup"><span data-stu-id="80d92-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="80d92-116">Além disso, verifique se suas abreviações são consistentes em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80d92-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="80d92-117">Alternar aleatoriamente em um projeto entre "HTML" e "linguagem HTML" pode levar à confusão.</span><span class="sxs-lookup"><span data-stu-id="80d92-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="80d92-118">Evite usar nomes em um escopo interno que sejam iguais aos nomes em um escopo externo.</span><span class="sxs-lookup"><span data-stu-id="80d92-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="80d92-119">Os erros poderão ocorrer se a variável incorreta for acessada.</span><span class="sxs-lookup"><span data-stu-id="80d92-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="80d92-120">Se ocorrer um conflito entre uma variável e a palavra-chave de mesmo nome, você deverá identificar a palavra-chave precedendo-a à biblioteca de tipos apropriada.</span><span class="sxs-lookup"><span data-stu-id="80d92-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="80d92-121">Por exemplo, se você tiver uma variável chamada `Date`, poderá usar a função intrínseca `Date` apenas chamando <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80d92-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d92-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80d92-122">See also</span></span>

- [<span data-ttu-id="80d92-123">Palavras-chave como Nomes de Elemento em Código</span><span class="sxs-lookup"><span data-stu-id="80d92-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="80d92-124">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="80d92-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="80d92-125">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="80d92-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="80d92-126">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="80d92-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="80d92-127">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80d92-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
