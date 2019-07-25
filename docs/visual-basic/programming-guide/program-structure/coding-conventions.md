---
title: Convenções de codificação do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 580a6e1caa78ea981b6d2be68a6e7c61e2ad55d7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433818"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="eca70-102">Convenções de codificação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eca70-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="eca70-103">A Microsoft desenvolve exemplos e documentação que seguem as diretrizes neste tópico.</span><span class="sxs-lookup"><span data-stu-id="eca70-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="eca70-104">Se você seguir as mesmas convenções de codificação, poderá obter os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="eca70-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="eca70-105">Seu código terá uma aparência consistente, para que os leitores possam se concentrar melhor no conteúdo, não no layout.</span><span class="sxs-lookup"><span data-stu-id="eca70-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="eca70-106">Os leitores entendem seu código mais rapidamente, pois eles podem fazer suposições com base na experiência anterior.</span><span class="sxs-lookup"><span data-stu-id="eca70-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="eca70-107">Você pode copiar, alterar e manter o código mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="eca70-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="eca70-108">Você ajuda a garantir que seu código demonstre "práticas recomendadas" para Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eca70-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="eca70-109">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="eca70-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="eca70-110">Para obter informações sobre as diretrizes de nomenclatura, consulte o tópico [diretrizes de nomenclatura](../../../standard/design-guidelines/naming-guidelines.md) .</span><span class="sxs-lookup"><span data-stu-id="eca70-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="eca70-111">Não use "My" ou "My" como parte de um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="eca70-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="eca70-112">Essa prática cria confusão com os `My` objetos.</span><span class="sxs-lookup"><span data-stu-id="eca70-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="eca70-113">Você não precisa alterar os nomes dos objetos no código gerado automaticamente para que eles se adaptem às diretrizes.</span><span class="sxs-lookup"><span data-stu-id="eca70-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="eca70-114">Convenções de Layout</span><span class="sxs-lookup"><span data-stu-id="eca70-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="eca70-115">Inserir tabulações como espaços e usar recuo inteligente com recuos de quatro espaços.</span><span class="sxs-lookup"><span data-stu-id="eca70-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="eca70-116">Use a forma **bonita (reformatação) de código** para reformatar seu código no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="eca70-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="eca70-117">Para obter mais informações, consulte [Opções, editor de texto, básico (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="eca70-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="eca70-118">Use apenas uma instrução por linha.</span><span class="sxs-lookup"><span data-stu-id="eca70-118">Use only one statement per line.</span></span> <span data-ttu-id="eca70-119">Não use o caractere separador de linha Visual Basic (:).</span><span class="sxs-lookup"><span data-stu-id="eca70-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="eca70-120">Evite usar o caractere de continuação de linha explícito "_" em favor da continuação de linha implícita onde quer que o idioma o permita.</span><span class="sxs-lookup"><span data-stu-id="eca70-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="eca70-121">Use apenas uma declaração por linha.</span><span class="sxs-lookup"><span data-stu-id="eca70-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="eca70-122">Se a **listagem completa (reformatação) do código** não Formatar linhas de continuação automaticamente, recue manualmente as linhas de continuação uma parada de tabulação.</span><span class="sxs-lookup"><span data-stu-id="eca70-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="eca70-123">No entanto, sempre os itens são alinhados à esquerda em uma lista.</span><span class="sxs-lookup"><span data-stu-id="eca70-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="eca70-124">Adicione pelo menos uma linha em branco entre as definições de método e propriedade.</span><span class="sxs-lookup"><span data-stu-id="eca70-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="eca70-125">Comentando Convenções</span><span class="sxs-lookup"><span data-stu-id="eca70-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="eca70-126">Coloque comentários em uma linha separada, em vez de no final de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="eca70-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="eca70-127">Inicie o texto de comentário com uma letra maiúscula e o texto de comentário final com um ponto.</span><span class="sxs-lookup"><span data-stu-id="eca70-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="eca70-128">Insira um espaço entre o delimitador de comentário (') e o texto do comentário.</span><span class="sxs-lookup"><span data-stu-id="eca70-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="eca70-129">Não coloque comentários com blocos formatados de asteriscos.</span><span class="sxs-lookup"><span data-stu-id="eca70-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="eca70-130">Estrutura do programa</span><span class="sxs-lookup"><span data-stu-id="eca70-130">Program Structure</span></span>  
  
- <span data-ttu-id="eca70-131">Ao usar o `Main` método, use a construção padrão para novos aplicativos de console e use `My` para argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="eca70-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="eca70-132">Diretrizes de Linguagem</span><span class="sxs-lookup"><span data-stu-id="eca70-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="eca70-133">Tipo de dados da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="eca70-133">String Data Type</span></span>  
  
- <span data-ttu-id="eca70-134">Use a [interpolação de cadeia de caracteres](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) para concatenar cadeias de caracteres curtas, como é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="eca70-134">Use [string interpolation](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="eca70-135">Para acrescentar cadeias de caracteres em loops <xref:System.Text.StringBuilder> , use o objeto.</span><span class="sxs-lookup"><span data-stu-id="eca70-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="eca70-136">Delegados relaxados em manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="eca70-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="eca70-137">Não qualifique explicitamente os argumentos (Object e EventArgs) para manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="eca70-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="eca70-138">Se você não estiver usando os argumentos do evento que são passados para um evento (por exemplo, Sender As Object, e como EventArgs), use delegados relaxados e deixe os argumentos do evento em seu código:</span><span class="sxs-lookup"><span data-stu-id="eca70-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="eca70-139">Tipo de Dados Sem Sinal</span><span class="sxs-lookup"><span data-stu-id="eca70-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="eca70-140">Use `Integer` tipos não assinados, exceto onde forem necessários.</span><span class="sxs-lookup"><span data-stu-id="eca70-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="eca70-141">Matrizes</span><span class="sxs-lookup"><span data-stu-id="eca70-141">Arrays</span></span>  
  
- <span data-ttu-id="eca70-142">Use a sintaxe curta ao inicializar matrizes na linha da declaração.</span><span class="sxs-lookup"><span data-stu-id="eca70-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="eca70-143">Por exemplo, use a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="eca70-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="eca70-144">Não use a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="eca70-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="eca70-145">Coloque o designador de matriz no tipo, não na variável.</span><span class="sxs-lookup"><span data-stu-id="eca70-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="eca70-146">Por exemplo, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="eca70-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="eca70-147">Não use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="eca70-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="eca70-148">Use a sintaxe {} ao declarar e inicializar matrizes de tipos de dados básicos.</span><span class="sxs-lookup"><span data-stu-id="eca70-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="eca70-149">Por exemplo, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="eca70-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="eca70-150">Não use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="eca70-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="eca70-151">Usar a palavra-chave with</span><span class="sxs-lookup"><span data-stu-id="eca70-151">Use the With Keyword</span></span>  
 <span data-ttu-id="eca70-152">Quando você faz uma série de chamadas para um objeto, considere usar a `With` palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="eca70-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="eca70-153">Use a tentativa... Capturar e usar instruções ao usar a manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="eca70-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="eca70-154">Não use `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="eca70-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="eca70-155">Usar a palavra-chave IsNot</span><span class="sxs-lookup"><span data-stu-id="eca70-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="eca70-156">Use a `IsNot` palavra-chave `Not...Is Nothing`em vez de.</span><span class="sxs-lookup"><span data-stu-id="eca70-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="eca70-157">Nova palavra-chave</span><span class="sxs-lookup"><span data-stu-id="eca70-157">New Keyword</span></span>  
  
- <span data-ttu-id="eca70-158">Use a instanciação curta.</span><span class="sxs-lookup"><span data-stu-id="eca70-158">Use short instantiation.</span></span> <span data-ttu-id="eca70-159">Por exemplo, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="eca70-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="eca70-160">A linha anterior é equivalente a esta:</span><span class="sxs-lookup"><span data-stu-id="eca70-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="eca70-161">Use inicializadores de objeto para novos objetos em vez do construtor sem parâmetros:</span><span class="sxs-lookup"><span data-stu-id="eca70-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="eca70-162">Tratamento de Evento</span><span class="sxs-lookup"><span data-stu-id="eca70-162">Event Handling</span></span>  
  
- <span data-ttu-id="eca70-163">Use `Handles` em vez `AddHandler`de:</span><span class="sxs-lookup"><span data-stu-id="eca70-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="eca70-164">Use `AddressOf`e não instancie explicitamente o delegado:</span><span class="sxs-lookup"><span data-stu-id="eca70-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="eca70-165">Quando você define um evento, usa a sintaxe curta e permite que o compilador defina o delegado:</span><span class="sxs-lookup"><span data-stu-id="eca70-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="eca70-166">Não verifique se um evento é `Nothing` (nulo) antes de chamar o `RaiseEvent` método.</span><span class="sxs-lookup"><span data-stu-id="eca70-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="eca70-167">`RaiseEvent``Nothing` verifica antes de gerar o evento.</span><span class="sxs-lookup"><span data-stu-id="eca70-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="eca70-168">Usando membros compartilhados</span><span class="sxs-lookup"><span data-stu-id="eca70-168">Using Shared Members</span></span>  
 <span data-ttu-id="eca70-169">Chame `Shared` membros usando o nome da classe, não de uma variável de instância.</span><span class="sxs-lookup"><span data-stu-id="eca70-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="eca70-170">Usar literais XML</span><span class="sxs-lookup"><span data-stu-id="eca70-170">Use XML Literals</span></span>  
 <span data-ttu-id="eca70-171">Os literais XML simplificam as tarefas mais comuns que você encontrar ao trabalhar com XML (por exemplo, carregar, consultar e transformar).</span><span class="sxs-lookup"><span data-stu-id="eca70-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="eca70-172">Ao desenvolver com XML, siga estas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="eca70-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="eca70-173">Use literais XML para criar documentos e fragmentos XML em vez de chamar APIs XML diretamente.</span><span class="sxs-lookup"><span data-stu-id="eca70-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="eca70-174">Importe namespaces XML no nível de arquivo ou projeto para aproveitar as otimizações de desempenho para literais XML.</span><span class="sxs-lookup"><span data-stu-id="eca70-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="eca70-175">Use as propriedades do eixo XML para acessar elementos e atributos em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="eca70-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="eca70-176">Use expressões inseridas para incluir valores e para criar XML a partir de valores existentes em vez de usar chamadas `Add` de API, como o método:</span><span class="sxs-lookup"><span data-stu-id="eca70-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="eca70-177">Consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="eca70-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="eca70-178">Use nomes significativos para variáveis de consulta:</span><span class="sxs-lookup"><span data-stu-id="eca70-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="eca70-179">Forneça nomes para elementos em uma consulta para garantir que os nomes de propriedade de tipos anônimos sejam colocados em maiúsculas corretamente usando a embalagem do Pascal:</span><span class="sxs-lookup"><span data-stu-id="eca70-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="eca70-180">Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos.</span><span class="sxs-lookup"><span data-stu-id="eca70-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="eca70-181">Por exemplo, se sua consulta retornar um nome de cliente e uma ID de pedido, renomeie-os `Name` em `ID` vez de deixá-los como e no resultado:</span><span class="sxs-lookup"><span data-stu-id="eca70-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="eca70-182">Use a inferência de tipos na declaração de variáveis de consulta e variáveis de intervalo:</span><span class="sxs-lookup"><span data-stu-id="eca70-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="eca70-183">Alinhar cláusulas de `From` consulta na instrução:</span><span class="sxs-lookup"><span data-stu-id="eca70-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="eca70-184">Use `Where` cláusulas antes de outras cláusulas de consulta para que as cláusulas de consulta posteriores operem no conjunto de dados filtrado:</span><span class="sxs-lookup"><span data-stu-id="eca70-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="eca70-185">Use a `Join` cláusula para definir explicitamente uma operação JOIN em vez de usar `Where` a cláusula para definir implicitamente uma operação JOIN:</span><span class="sxs-lookup"><span data-stu-id="eca70-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="eca70-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eca70-186">See also</span></span>

- [<span data-ttu-id="eca70-187">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="eca70-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
