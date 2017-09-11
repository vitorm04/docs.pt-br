---
title: "Convenções de codificação do Visual Basic | Documentos do Microsoft"
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
- coding conventions, Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
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
ms.openlocfilehash: 16d4ddccd3a16c48e58f297faf8909148899013f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="b99fc-102">Convenções de codificação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b99fc-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="b99fc-103">A Microsoft desenvolve amostras e documentação que siga as diretrizes neste tópico.</span><span class="sxs-lookup"><span data-stu-id="b99fc-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="b99fc-104">Se você seguir as mesmas convenções de codificação, você pode obter os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="b99fc-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="b99fc-105">Seu código terá uma aparência consistente, para que os leitores melhor podem se concentrar no conteúdo, não o layout.</span><span class="sxs-lookup"><span data-stu-id="b99fc-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="b99fc-106">Leitores de compreendam o código mais rapidamente porque elas podem fazer suposições com base nas experiências anteriores.</span><span class="sxs-lookup"><span data-stu-id="b99fc-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="b99fc-107">Você pode copiar, alterar e manter o código mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="b99fc-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="b99fc-108">Você ajuda a garantir que seu código demonstra "práticas recomendadas" para o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b99fc-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="b99fc-109">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="b99fc-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="b99fc-110">Para obter informações sobre as diretrizes de nomenclatura, consulte [diretrizes de nomenclatura](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) tópico.</span><span class="sxs-lookup"><span data-stu-id="b99fc-110">For information about naming guidelines, see [Naming Guidelines](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) topic.</span></span>  
  
-   <span data-ttu-id="b99fc-111">Não use "Meu" ou "Meu" como parte de um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="b99fc-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="b99fc-112">Essa prática cria confusão com o `My` objetos.</span><span class="sxs-lookup"><span data-stu-id="b99fc-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="b99fc-113">Você não precisa alterar os nomes de objetos no código gerado automaticamente para ajustar as diretrizes.</span><span class="sxs-lookup"><span data-stu-id="b99fc-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="b99fc-114">Convenções de Layout</span><span class="sxs-lookup"><span data-stu-id="b99fc-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="b99fc-115">Inserir tabulações como espaços e use o recuo inteligente com recuos de quatro espaço.</span><span class="sxs-lookup"><span data-stu-id="b99fc-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="b99fc-116">Use **bastante listando (reformatação) do código** reformatar o código no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="b99fc-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="b99fc-117">Para obter mais informações, consulte [opções, Editor de texto, básico (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b99fc-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="b99fc-118">Use apenas uma instrução por linha.</span><span class="sxs-lookup"><span data-stu-id="b99fc-118">Use only one statement per line.</span></span> <span data-ttu-id="b99fc-119">Não use o caractere de separador de linha (:) do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b99fc-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="b99fc-120">Evite usar o caractere de continuação de linha explícita "_" em favor de continuação implícita de linha sempre que o idioma permite a ele.</span><span class="sxs-lookup"><span data-stu-id="b99fc-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="b99fc-121">Use apenas uma declaração por linha.</span><span class="sxs-lookup"><span data-stu-id="b99fc-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="b99fc-122">Se **bastante listando (reformatação) do código** não formatar linhas de continuação automaticamente, manualmente Recuar continuação linhas uma parada de tabulação.</span><span class="sxs-lookup"><span data-stu-id="b99fc-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="b99fc-123">No entanto, sempre alinhado à esquerda itens em uma lista.</span><span class="sxs-lookup"><span data-stu-id="b99fc-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="b99fc-124">Adicione pelo menos uma linha em branco entre as definições de método e propriedade.</span><span class="sxs-lookup"><span data-stu-id="b99fc-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="b99fc-125">Comentando Convenções</span><span class="sxs-lookup"><span data-stu-id="b99fc-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="b99fc-126">Inserir comentários em uma linha separada em vez de no final de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="b99fc-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="b99fc-127">Inicie o texto do comentário com uma letra maiuscula e texto de comentário final com um ponto.</span><span class="sxs-lookup"><span data-stu-id="b99fc-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="b99fc-128">Insira um espaço entre o delimitador de comentário (') e o texto do comentário.</span><span class="sxs-lookup"><span data-stu-id="b99fc-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     <span data-ttu-id="b99fc-129">[!code-vb[VbVbalrGuidelines n º&2;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-129">[!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-130">Não coloque comentários com blocos de asteriscos formatados.</span><span class="sxs-lookup"><span data-stu-id="b99fc-130">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="b99fc-131">Estrutura do programa</span><span class="sxs-lookup"><span data-stu-id="b99fc-131">Program Structure</span></span>  
  
-   <span data-ttu-id="b99fc-132">Quando você usa o `Main` método, use o construtor padrão para novos aplicativos de console e usar `My` para argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b99fc-132">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     <span data-ttu-id="b99fc-133">[!code-vb[VbVbalrGuidelines n º&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-133">[!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="b99fc-134">Diretrizes de Linguagem</span><span class="sxs-lookup"><span data-stu-id="b99fc-134">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="b99fc-135">Tipo de dados da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b99fc-135">String Data Type</span></span>  
  
-   <span data-ttu-id="b99fc-136">Para concatenar cadeias de caracteres, use um e comercial (&).</span><span class="sxs-lookup"><span data-stu-id="b99fc-136">To concatenate strings, use an ampersand (&).</span></span>  
  
     <span data-ttu-id="b99fc-137">[!code-vb[VbVbalrGuidelines n º&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-137">[!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-138">Para acrescentar cadeias de caracteres em loops, use o <xref:System.Text.StringBuilder>objeto.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="b99fc-138">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     <span data-ttu-id="b99fc-139">[!code-vb[VbVbalrGuidelines n º&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-139">[!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]</span></span>  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="b99fc-140">Delegados relaxados nos manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="b99fc-140">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="b99fc-141">Não qualifique explicitamente os argumentos (Object e EventArgs) para manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="b99fc-141">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="b99fc-142">Se você não estiver usando os argumentos do evento são passados para um evento (por exemplo, o remetente como objeto, e como EventArgs), usar delegados relaxados e omitir os argumentos do evento no seu código:</span><span class="sxs-lookup"><span data-stu-id="b99fc-142">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 <span data-ttu-id="b99fc-143">[!code-vb[VbVbalrGuidelines&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-143">[!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]</span></span>  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="b99fc-144">Tipo de Dados Sem Sinal</span><span class="sxs-lookup"><span data-stu-id="b99fc-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="b99fc-145">Use `Integer` em vez de tipos não assinados, exceto onde eles são necessários.</span><span class="sxs-lookup"><span data-stu-id="b99fc-145">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="b99fc-146">Matrizes</span><span class="sxs-lookup"><span data-stu-id="b99fc-146">Arrays</span></span>  
  
-   <span data-ttu-id="b99fc-147">Use a sintaxe abreviada ao inicializar matrizes na linha da declaração.</span><span class="sxs-lookup"><span data-stu-id="b99fc-147">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="b99fc-148">Por exemplo, use a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="b99fc-148">For example, use the following syntax.</span></span>  
  
     <span data-ttu-id="b99fc-149">[!code-vb[VbVbalrGuidelines n º&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-149">[!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]</span></span>  
  
     <span data-ttu-id="b99fc-150">Não use a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="b99fc-150">Do not use the following syntax.</span></span>  
  
     <span data-ttu-id="b99fc-151">[!code-vb[VbVbalrGuidelines n º&9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-151">[!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-152">Coloque o designador de matriz do tipo, e não na variável.</span><span class="sxs-lookup"><span data-stu-id="b99fc-152">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="b99fc-153">Por exemplo, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="b99fc-153">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="b99fc-154">[!code-vb[VbVbalrGuidelines n º&11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-154">[!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]</span></span>  
  
     <span data-ttu-id="b99fc-155">Não use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="b99fc-155">Do not use the following syntax:</span></span>  
  
     <span data-ttu-id="b99fc-156">[!code-vb[VbVbalrGuidelines n º&10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-156">[!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-157">Use a sintaxe {} quando você declara e inicializar matrizes de tipos de dados básicos.</span><span class="sxs-lookup"><span data-stu-id="b99fc-157">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="b99fc-158">Por exemplo, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="b99fc-158">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="b99fc-159">[!code-vb[VbVbalrGuidelines&#12;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-159">[!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]</span></span>  
  
     <span data-ttu-id="b99fc-160">Não use a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="b99fc-160">Do not use the following syntax:</span></span>  
  
     <span data-ttu-id="b99fc-161">[!code-vb[VbVbalrGuidelines&13;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-161">[!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]</span></span>  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="b99fc-162">Use a palavra-chave With</span><span class="sxs-lookup"><span data-stu-id="b99fc-162">Use the With Keyword</span></span>  
 <span data-ttu-id="b99fc-163">Quando você faz uma série de chamadas a um objeto, considere o uso de `With` palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="b99fc-163">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 <span data-ttu-id="b99fc-164">[!code-vb[VbVbalrGuidelines&#15;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-164">[!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]</span></span>  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="b99fc-165">Use a instrução Try... Catch e instruções Using ao usar tratamento de exceções</span><span class="sxs-lookup"><span data-stu-id="b99fc-165">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="b99fc-166">Não use `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="b99fc-166">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="b99fc-167">Use a palavra-chave IsNot</span><span class="sxs-lookup"><span data-stu-id="b99fc-167">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="b99fc-168">Use o `IsNot` palavra-chave em vez de `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b99fc-168">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="b99fc-169">Palavra-chave New</span><span class="sxs-lookup"><span data-stu-id="b99fc-169">New Keyword</span></span>  
  
-   <span data-ttu-id="b99fc-170">Use instanciação curta.</span><span class="sxs-lookup"><span data-stu-id="b99fc-170">Use short instantiation.</span></span> <span data-ttu-id="b99fc-171">Por exemplo, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="b99fc-171">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="b99fc-172">[!code-vb[VbVbalrGuidelines&#21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-172">[!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]</span></span>  
  
     <span data-ttu-id="b99fc-173">A linha anterior é equivalente a esta:</span><span class="sxs-lookup"><span data-stu-id="b99fc-173">The preceding line is equivalent to this:</span></span>  
  
     <span data-ttu-id="b99fc-174">[!code-vb[VbVbalrGuidelines&#22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-174">[!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-175">Use inicializadores de objeto para novos objetos em vez do construtor sem parâmetros:</span><span class="sxs-lookup"><span data-stu-id="b99fc-175">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     <span data-ttu-id="b99fc-176">[!code-vb[VbVbalrGuidelines&#23;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-176">[!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]</span></span>  
  
### <a name="event-handling"></a><span data-ttu-id="b99fc-177">Tratamento de Evento</span><span class="sxs-lookup"><span data-stu-id="b99fc-177">Event Handling</span></span>  
  
-   <span data-ttu-id="b99fc-178">Use `Handles` em vez de `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="b99fc-178">Use `Handles` rather than `AddHandler`:</span></span>  
  
     <span data-ttu-id="b99fc-179">[!code-vb[VbVbalrGuidelines&#24;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-179">[!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-180">Use `AddressOf`e não instanciar o delegado explicitamente:</span><span class="sxs-lookup"><span data-stu-id="b99fc-180">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     <span data-ttu-id="b99fc-181">[!code-vb[25 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-181">[!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-182">Quando você define um evento, use a sintaxe abreviada e permitem que o compilador defina o delegado:</span><span class="sxs-lookup"><span data-stu-id="b99fc-182">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     <span data-ttu-id="b99fc-183">[!code-vb[VbVbalrGuidelines&#26;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-183">[!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-184">Não verificar se um evento é `Nothing` (null) antes de chamar o `RaiseEvent` método.</span><span class="sxs-lookup"><span data-stu-id="b99fc-184">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="b99fc-185">`RaiseEvent`verifica se há `Nothing` antes de gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="b99fc-185">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="b99fc-186">Usando membros compartilhados</span><span class="sxs-lookup"><span data-stu-id="b99fc-186">Using Shared Members</span></span>  
 <span data-ttu-id="b99fc-187">Chamar `Shared` membros usando o nome de classe, não a partir de uma variável de instância.</span><span class="sxs-lookup"><span data-stu-id="b99fc-187">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="b99fc-188">Usar literais XML</span><span class="sxs-lookup"><span data-stu-id="b99fc-188">Use XML Literals</span></span>  
 <span data-ttu-id="b99fc-189">Literais XML simplificam as tarefas mais comuns encontrados ao trabalhar com XML (por exemplo, carga, consulta e transformação).</span><span class="sxs-lookup"><span data-stu-id="b99fc-189">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="b99fc-190">Ao desenvolver com XML, siga estas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="b99fc-190">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="b99fc-191">Use literais XML para criar documentos XML e fragmentos em vez de chamar APIs XML diretamente.</span><span class="sxs-lookup"><span data-stu-id="b99fc-191">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="b99fc-192">Importe namespaces XML no nível do arquivo ou projeto para aproveitar as otimizações de desempenho para literais XML.</span><span class="sxs-lookup"><span data-stu-id="b99fc-192">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="b99fc-193">Use as propriedades do eixo XML para acessar elementos e atributos em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b99fc-193">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="b99fc-194">Usar expressões inseridas para incluir valores e criar o XML de valores existentes em vez de usar chamadas de API, como o `Add` método:</span><span class="sxs-lookup"><span data-stu-id="b99fc-194">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     <span data-ttu-id="b99fc-195">[!code-vb[VbVbalrGuidelines&#27;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-195">[!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="b99fc-196">Consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="b99fc-196">LINQ Queries</span></span>  
  
-   <span data-ttu-id="b99fc-197">Use nomes significativos para variáveis de consulta:</span><span class="sxs-lookup"><span data-stu-id="b99fc-197">Use meaningful names for query variables:</span></span>  
  
     <span data-ttu-id="b99fc-198">[!code-vb[VbVbalrGuidelines&#28;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-198">[!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-199">Fornecer nomes de elementos em uma consulta para certificar-se de que os nomes de propriedades de tipos anônimos são corretamente em maiusculas usando Pascal casing:</span><span class="sxs-lookup"><span data-stu-id="b99fc-199">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     <span data-ttu-id="b99fc-200">[!code-vb[29 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-200">[!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-201">Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos.</span><span class="sxs-lookup"><span data-stu-id="b99fc-201">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="b99fc-202">Por exemplo, se a consulta retorna um cliente, nome e uma ID de ordem, renomeá-los o em vez de deixá-los como `Name` e `ID` no resultado:</span><span class="sxs-lookup"><span data-stu-id="b99fc-202">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     <span data-ttu-id="b99fc-203">[!code-vb[30 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-203">[!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-204">Use a inferência de tipo na declaração de variáveis de consulta e intervalo:</span><span class="sxs-lookup"><span data-stu-id="b99fc-204">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     <span data-ttu-id="b99fc-205">[!code-vb[VbVbalrGuidelines&#31;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-205">[!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-206">Alinhe cláusulas de consulta sob o `From` instrução:</span><span class="sxs-lookup"><span data-stu-id="b99fc-206">Align query clauses under the `From` statement:</span></span>  
  
     <span data-ttu-id="b99fc-207">[!code-vb[32 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-207">[!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-208">Use `Where` cláusulas antes de outras cláusulas de consulta para que as cláusulas de consulta posteriores operam em conjunto filtrado de dados:</span><span class="sxs-lookup"><span data-stu-id="b99fc-208">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     <span data-ttu-id="b99fc-209">[!code-vb[33 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-209">[!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]</span></span>  
  
-   <span data-ttu-id="b99fc-210">Use o `Join` cláusula definir explicitamente uma operação de junção em vez de usar o `Where` cláusula implicitamente definir uma operação de junção:</span><span class="sxs-lookup"><span data-stu-id="b99fc-210">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     <span data-ttu-id="b99fc-211">[!code-vb[VbVbalrGuidelines&#34;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99fc-211">[!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99fc-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b99fc-212">See Also</span></span>  
 [<span data-ttu-id="b99fc-213">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="b99fc-213">Secure Coding Guidelines</span></span>](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
