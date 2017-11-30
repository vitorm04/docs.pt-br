---
title: "Como definir e executar métodos dinâmicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52f6b425ae4df138a843c6a790f10f78dc5a2b40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="6defb-102">Como definir e executar métodos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="6defb-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="6defb-103">Os procedimentos a seguir mostram como definir e executar um método dinâmico simples e um método dinâmico ligado a uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="6defb-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="6defb-104">Para obter mais informações sobre métodos dinâmicos, consulte a classe <xref:System.Reflection.Emit.DynamicMethod> e [Cenários de métodos dinâmicos para a emissão de reflexão](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span><span class="sxs-lookup"><span data-stu-id="6defb-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="6defb-105">Para definir e executar um método dinâmico</span><span class="sxs-lookup"><span data-stu-id="6defb-105">To define and execute a dynamic method</span></span>  
  
1.  <span data-ttu-id="6defb-106">Declare um tipo de delegado para executar o método.</span><span class="sxs-lookup"><span data-stu-id="6defb-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="6defb-107">Considere usar um delegado genérico para minimizar o número de tipos de delegado que você precisa declarar.</span><span class="sxs-lookup"><span data-stu-id="6defb-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="6defb-108">O código a seguir declara dois tipos de delegado que podem ser usados para o método `SquareIt` e um deles é genérico.</span><span class="sxs-lookup"><span data-stu-id="6defb-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  <span data-ttu-id="6defb-109">Crie uma matriz que especifica os tipos de parâmetro para o método dinâmico.</span><span class="sxs-lookup"><span data-stu-id="6defb-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="6defb-110">Neste exemplo, o único parâmetro é um `int` (`Integer` no Visual Basic), portanto, a matriz tem apenas um elemento.</span><span class="sxs-lookup"><span data-stu-id="6defb-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <span data-ttu-id="6defb-111">Criará um <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="6defb-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="6defb-112">Neste exemplo, o método é chamado `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="6defb-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6defb-113">Não é necessário atribuir nomes aos métodos dinâmicos e eles não podem ser invocados por nome.</span><span class="sxs-lookup"><span data-stu-id="6defb-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="6defb-114">Vários métodos dinâmicos podem ter o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="6defb-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="6defb-115">No entanto, o nome aparece em pilhas de chamadas e pode ser útil para depuração.</span><span class="sxs-lookup"><span data-stu-id="6defb-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="6defb-116">O tipo do valor retornado é especificado como `long`.</span><span class="sxs-lookup"><span data-stu-id="6defb-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="6defb-117">O método está associado com o módulo que contém a classe `Example`, que contém o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="6defb-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="6defb-118">Qualquer módulo carregado pode ser especificado.</span><span class="sxs-lookup"><span data-stu-id="6defb-118">Any loaded module could be specified.</span></span> <span data-ttu-id="6defb-119">O método dinâmico age como um método `static` de nível de módulo (`Shared` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6defb-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  <span data-ttu-id="6defb-120">Emita o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="6defb-120">Emit the method body.</span></span> <span data-ttu-id="6defb-121">Neste exemplo, um objeto <xref:System.Reflection.Emit.ILGenerator> é usado para emitir o MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="6defb-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="6defb-122">Como alternativa, um objeto <xref:System.Reflection.Emit.DynamicILInfo> pode ser usado em conjunto com geradores de código não gerenciado para emitir o corpo do método para um <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="6defb-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="6defb-123">O MSIL neste exemplo carrega o argumento, que é um `int`, para a pilha, converte-o em um `long`, duplica o `long` e multiplica os dois números.</span><span class="sxs-lookup"><span data-stu-id="6defb-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="6defb-124">Isso deixa o resultado ao quadrado na pilha e tudo o que o método precisa fazer é retornar.</span><span class="sxs-lookup"><span data-stu-id="6defb-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <span data-ttu-id="6defb-125">Crie uma instância do delegado (declarado na etapa 1) que representa o método dinâmico chamando o método <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="6defb-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="6defb-126">Criar o delegado conclui o método e quaisquer tentativas adicionais de alterar o método — por exemplo, adicionando mais MSIL — são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="6defb-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="6defb-127">O código a seguir cria o delegado e o invoca, usando um delegado genérico.</span><span class="sxs-lookup"><span data-stu-id="6defb-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="6defb-128">Para definir e executar um método dinâmico associado a um objeto</span><span class="sxs-lookup"><span data-stu-id="6defb-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1.  <span data-ttu-id="6defb-129">Declare um tipo de delegado para executar o método.</span><span class="sxs-lookup"><span data-stu-id="6defb-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="6defb-130">Considere usar um delegado genérico para minimizar o número de tipos de delegado que você precisa declarar.</span><span class="sxs-lookup"><span data-stu-id="6defb-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="6defb-131">O código a seguir declara um tipo de delegado genérico que pode ser usado para executar qualquer método com um parâmetro e um valor retornado ou um método com dois parâmetros e um valor retornado se o delegado estiver associado a um objeto.</span><span class="sxs-lookup"><span data-stu-id="6defb-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  <span data-ttu-id="6defb-132">Crie uma matriz que especifica os tipos de parâmetro para o método dinâmico.</span><span class="sxs-lookup"><span data-stu-id="6defb-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="6defb-133">Se o delegado que representa o método deve ser associado a um objeto, o primeiro parâmetro deve corresponder ao tipo ao qual o delegado está associado.</span><span class="sxs-lookup"><span data-stu-id="6defb-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="6defb-134">Neste exemplo, há dois parâmetros, do tipo `Example` e do tipo `int` (`Integer` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6defb-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <span data-ttu-id="6defb-135">Criará um <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="6defb-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="6defb-136">Neste exemplo, o método não tem nenhum nome.</span><span class="sxs-lookup"><span data-stu-id="6defb-136">In this example the method has no name.</span></span> <span data-ttu-id="6defb-137">O tipo do valor retornado é especificado como `int` (`Integer` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6defb-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="6defb-138">O método tem acesso aos membros particulares e protegidos da classe `Example`.</span><span class="sxs-lookup"><span data-stu-id="6defb-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  <span data-ttu-id="6defb-139">Emita o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="6defb-139">Emit the method body.</span></span> <span data-ttu-id="6defb-140">Neste exemplo, um objeto <xref:System.Reflection.Emit.ILGenerator> é usado para emitir o MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="6defb-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="6defb-141">Como alternativa, um objeto <xref:System.Reflection.Emit.DynamicILInfo> pode ser usado em conjunto com geradores de código não gerenciado para emitir o corpo do método para um <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="6defb-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="6defb-142">O MSIL neste exemplo carrega o primeiro argumento, que é uma instância da classe `Example` e o usa para carregar o valor de um campo de instância privada do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="6defb-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="6defb-143">O segundo argumento é carregado e os dois números são multiplicados.</span><span class="sxs-lookup"><span data-stu-id="6defb-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="6defb-144">Se o resultado for maior do que `int`, o valor será truncado e os bits mais significativos serão descartados.</span><span class="sxs-lookup"><span data-stu-id="6defb-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="6defb-145">O método retorna, com o valor retornado na pilha.</span><span class="sxs-lookup"><span data-stu-id="6defb-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <span data-ttu-id="6defb-146">Crie uma instância do delegado (declarado na etapa 1) que representa o método dinâmico chamando a sobrecarga do método <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="6defb-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="6defb-147">Criar o delegado conclui o método e quaisquer tentativas adicionais de alterar o método — por exemplo, adicionando mais MSIL — são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="6defb-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6defb-148">Você pode chamar o método <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> várias vezes para criar delegados associados a outras instâncias do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="6defb-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="6defb-149">O código a seguir associa o método a uma nova instância da classe `Example` cujo campo de teste privado está definido como 42.</span><span class="sxs-lookup"><span data-stu-id="6defb-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="6defb-150">Isto é, cada vez que o delegado é invocado, a instância de `Example` é passada para o primeiro parâmetro do método.</span><span class="sxs-lookup"><span data-stu-id="6defb-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="6defb-151">O delegado `OneParameter` é usado porque o primeiro parâmetro do método sempre recebe a instância do `Example`.</span><span class="sxs-lookup"><span data-stu-id="6defb-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="6defb-152">Quando o delegado é invocado, apenas o segundo parâmetro é necessário.</span><span class="sxs-lookup"><span data-stu-id="6defb-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="6defb-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6defb-153">Example</span></span>  
 <span data-ttu-id="6defb-154">O exemplo de código a seguir demonstra um método dinâmico simples e um método dinâmico associado a uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="6defb-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="6defb-155">O método dinâmico simples tem um argumento, um inteiro de 32 bits e retorna o quadrado de 64 bits desse inteiro.</span><span class="sxs-lookup"><span data-stu-id="6defb-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="6defb-156">Um delegado genérico é usado para invocar o método.</span><span class="sxs-lookup"><span data-stu-id="6defb-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="6defb-157">O segundo método dinâmico tem dois parâmetros de tipo `Example` e de tipo `int` (`Integer` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6defb-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="6defb-158">Quando o método dinâmico tiver sido criado, ele será associado a uma instância de `Example`, usando um delegado genérico que tem um argumento do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="6defb-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="6defb-159">O delegado não tem um argumento do tipo `Example` porque o primeiro parâmetro do método sempre recebe a instância associada do `Example`.</span><span class="sxs-lookup"><span data-stu-id="6defb-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="6defb-160">Quando o delegado é invocado, somente o argumento `int` é fornecido.</span><span class="sxs-lookup"><span data-stu-id="6defb-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="6defb-161">Esse método dinâmico acessa um campo particular da classe `Example` e retorna o produto do campo particular e o argumento `int`.</span><span class="sxs-lookup"><span data-stu-id="6defb-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="6defb-162">O exemplo de código define delegados que podem ser usados para executar os métodos.</span><span class="sxs-lookup"><span data-stu-id="6defb-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6defb-163">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6defb-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6defb-164">O código contém as instruções `using` C# (`Imports` no Visual Basic) necessárias para a compilação.</span><span class="sxs-lookup"><span data-stu-id="6defb-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="6defb-165">Nenhuma referência de assembly adicional é necessária.</span><span class="sxs-lookup"><span data-stu-id="6defb-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="6defb-166">Compile o código na linha de comando usando csc.exe, vbc.exe ou cl.exe.</span><span class="sxs-lookup"><span data-stu-id="6defb-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="6defb-167">Para compilar o código no Visual Studio, coloque-o em um modelo de projeto de aplicativo do console.</span><span class="sxs-lookup"><span data-stu-id="6defb-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6defb-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6defb-168">See Also</span></span>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [<span data-ttu-id="6defb-169">Usando a reflexão de emissão</span><span class="sxs-lookup"><span data-stu-id="6defb-169">Using Reflection Emit</span></span>](http://msdn.microsoft.com/en-us/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [<span data-ttu-id="6defb-170">Cenários de métodos dinâmicos para a emissão de reflexão</span><span class="sxs-lookup"><span data-stu-id="6defb-170">Reflection Emit Dynamic Method Scenarios</span></span>](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
