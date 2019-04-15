---
title: 'Como: Conectar um delegado usando a reflexão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7c2956a222a47cea36abbc2f21da2d7e2061e09
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314523"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="fac76-102">Como: Conectar um delegado usando a reflexão</span><span class="sxs-lookup"><span data-stu-id="fac76-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="fac76-103">Quando você usa a reflexão para carregar e executar assemblies, não pode usar recursos de linguagem como o operador `+=` do C# ou a [instrução AddHandler](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) do Visual Basic para conectar eventos.</span><span class="sxs-lookup"><span data-stu-id="fac76-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="fac76-104">Os procedimentos a seguir mostram como conectar um método existente a um evento obtendo todos os tipos necessários por meio de reflexão e como criar um método dinâmico usando a emissão de reflexão e conectá-lo a um evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fac76-105">Para encontrar outra maneira de conectar um delegado manipulador de evento, consulte o exemplo de código para o método <xref:System.Reflection.EventInfo.AddEventHandler%2A> da classe <xref:System.Reflection.EventInfo>.</span><span class="sxs-lookup"><span data-stu-id="fac76-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="fac76-106">Para conectar um delegado usando reflexão</span><span class="sxs-lookup"><span data-stu-id="fac76-106">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="fac76-107">Carregue um assembly que contém o tipo que gera eventos.</span><span class="sxs-lookup"><span data-stu-id="fac76-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="fac76-108">Os assemblies normalmente são carregados com o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fac76-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fac76-109">Para manter esse exemplo simples, um formulário derivado no assembly atual é usado, portanto, o método <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> é usado para carregar o assembly atual.</span><span class="sxs-lookup"><span data-stu-id="fac76-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="fac76-110">Obtenha um objeto <xref:System.Type> que representa o tipo e crie uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="fac76-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="fac76-111">O método <xref:System.Activator.CreateInstance%28System.Type%29> é usado no código a seguir porque o formulário tem um construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="fac76-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="fac76-112">Há várias outras sobrecargas do método <xref:System.Activator.CreateInstance%2A> que poderão ser usadas se o tipo sendo criado não tiver um construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="fac76-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="fac76-113">A nova instância é armazenada como o tipo <xref:System.Object> para manter a ficção de que nada é conhecido sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="fac76-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="fac76-114">(A reflexão permite que você obtenha os tipos em um assembly sem saber seus nomes com antecedência.)</span><span class="sxs-lookup"><span data-stu-id="fac76-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="fac76-115">Obtenha um objeto <xref:System.Reflection.EventInfo> que representa o evento e use a propriedade <xref:System.Reflection.EventInfo.EventHandlerType%2A> para obter o tipo de delegado usado para manipular o evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="fac76-116">No código a seguir, é obtido um <xref:System.Reflection.EventInfo> para o evento <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="fac76-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="fac76-117">Obtenha um objeto <xref:System.Reflection.MethodInfo> que representa o método que manipula o evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="fac76-118">O código de programa completo na seção Exemplo posteriormente neste tópico contém um método que corresponde à assinatura do delegado <xref:System.EventHandler>, que manipula o evento <xref:System.Windows.Forms.Control.Click>, mas você também pode gerar métodos dinâmicos no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fac76-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="fac76-119">Para obter detalhes, consulte o procedimento que acompanha esse artigo para gerar um manipulador de eventos em tempo de execução usando um método dinâmico.</span><span class="sxs-lookup"><span data-stu-id="fac76-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="fac76-120">Crie uma instância do delegado usando o método <xref:System.Delegate.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="fac76-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="fac76-121">Esse método é estático (`Shared` no Visual Basic), portanto, o tipo de delegado deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="fac76-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="fac76-122">O uso das sobrecargas de <xref:System.Delegate.CreateDelegate%2A> que utilizam um <xref:System.Reflection.MethodInfo> é recomendado.</span><span class="sxs-lookup"><span data-stu-id="fac76-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="fac76-123">Obtenha o método do acessador `add` e invoque-o para conectar o evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="fac76-124">Todos os eventos têm um acessador `add` e um acessador `remove`, que estão ocultos pela sintaxe de linguagens de alto nível.</span><span class="sxs-lookup"><span data-stu-id="fac76-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="fac76-125">Por exemplo, o C# usa o operador `+=` para conectar eventos e o Visual Basic usa a [instrução AddHandler](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fac76-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="fac76-126">O código a seguir obtém o acessador `add` do evento <xref:System.Windows.Forms.Control.Click> e o invoca com associação tardia, passando a instância do delegado.</span><span class="sxs-lookup"><span data-stu-id="fac76-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="fac76-127">Os argumentos devem ser passados como uma matriz.</span><span class="sxs-lookup"><span data-stu-id="fac76-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="fac76-128">Teste o evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-128">Test the event.</span></span> <span data-ttu-id="fac76-129">O código a seguir mostra o formulário definido no exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="fac76-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="fac76-130">Clicar no formulário invoca o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="fac76-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="fac76-131">Para gerar um manipulador de eventos em tempo de execução usando um método dinâmico</span><span class="sxs-lookup"><span data-stu-id="fac76-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="fac76-132">Os métodos do manipulador de eventos podem ser gerados em tempo de execução, usando métodos dinâmicos leves e a emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="fac76-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="fac76-133">Para criar um manipulador de eventos, são necessários o tipo de retorno e os tipos de parâmetro do delegado.</span><span class="sxs-lookup"><span data-stu-id="fac76-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="fac76-134">Eles podem ser obtidos examinando o método `Invoke` do delegado.</span><span class="sxs-lookup"><span data-stu-id="fac76-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="fac76-135">O código a seguir usa os métodos `GetDelegateReturnType` e `GetDelegateParameterTypes` para obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="fac76-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="fac76-136">O código para esses métodos pode ser encontrado na seção Exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="fac76-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="fac76-137">Não é necessário nomear um <xref:System.Reflection.Emit.DynamicMethod>, portanto, a cadeia de caracteres vazia pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="fac76-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="fac76-138">No código a seguir, o último argumento associa o método dinâmico ao tipo atual, concedendo ao delegado o acesso a todos os membros públicos e privados da classe `Example`.</span><span class="sxs-lookup"><span data-stu-id="fac76-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="fac76-139">Gere um corpo de método.</span><span class="sxs-lookup"><span data-stu-id="fac76-139">Generate a method body.</span></span> <span data-ttu-id="fac76-140">Esse método carrega uma cadeia de caracteres, chama a sobrecarga do método <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> que usa uma cadeia de caracteres, exibe o valor retornado da pilha (porque o manipulador não tem nenhum tipo de retorno) e retorna.</span><span class="sxs-lookup"><span data-stu-id="fac76-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="fac76-141">Para saber mais sobre como emitir métodos dinâmicos, confira [Como: Definir e executar métodos dinâmicos](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="fac76-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="fac76-142">Conclua o método dinâmico chamando seu método <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="fac76-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="fac76-143">Use o acessador `add` para adicionar o delegado à lista de invocação para o evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="fac76-144">Teste o evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-144">Test the event.</span></span> <span data-ttu-id="fac76-145">O código a seguir carrega o formulário definido no exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="fac76-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="fac76-146">Clicar no formulário invoca o manipulador de eventos predefinido e o manipulador de eventos emitido.</span><span class="sxs-lookup"><span data-stu-id="fac76-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="fac76-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fac76-147">Example</span></span>  
 <span data-ttu-id="fac76-148">O exemplo de código a seguir mostra como conectar um método existente a um evento usando a reflexão e também como usar a classe <xref:System.Reflection.Emit.DynamicMethod> para emitir um método em tempo de execução e conectá-lo a um evento.</span><span class="sxs-lookup"><span data-stu-id="fac76-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fac76-149">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fac76-149">Compiling the Code</span></span>  
  
-   <span data-ttu-id="fac76-150">O código contém as instruções `using` C# (`Imports` no Visual Basic) necessárias para a compilação.</span><span class="sxs-lookup"><span data-stu-id="fac76-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="fac76-151">Não é necessária nenhuma referência de assembly adicional para compilar da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="fac76-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="fac76-152">No Visual Studio, você deve adicionar uma referência System.Windows.Forms.dll porque esse exemplo é um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="fac76-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
-   <span data-ttu-id="fac76-153">Compile o código na linha de comando usando csc.exe, vbc.exe ou cl.exe.</span><span class="sxs-lookup"><span data-stu-id="fac76-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="fac76-154">Para compilar o código no Visual Studio, coloque-o em um modelo de projeto de aplicativo do console.</span><span class="sxs-lookup"><span data-stu-id="fac76-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac76-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fac76-155">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="fac76-156">Como: Definir e executar métodos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="fac76-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="fac76-157">Reflexão</span><span class="sxs-lookup"><span data-stu-id="fac76-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
