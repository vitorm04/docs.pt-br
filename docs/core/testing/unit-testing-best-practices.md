---
title: Melhores práticas para escrever testes de unidade
description: Conheça as melhores práticas para escrever testes de unidade que promovem a qualidade e a resiliência do código em projetos .NET Core e .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: b543ab2e200e8169a251db8ddfb1493c5583ed69
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360245"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="29170-103">Melhores práticas de teste de unidade com .NET Core e .NET Standard</span><span class="sxs-lookup"><span data-stu-id="29170-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="29170-104">Há diversas vantagens para escrever testes de unidade; eles ajudam com a regressão, fornecem a documentação e facilitam o bom design.</span><span class="sxs-lookup"><span data-stu-id="29170-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="29170-105">No entanto, testes de unidade difíceis de ler e frágeis podem causar estragos na sua base de código.</span><span class="sxs-lookup"><span data-stu-id="29170-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="29170-106">Este artigo descreve algumas melhores práticas com relação ao design de teste de unidade para projetos .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="29170-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="29170-107">Neste guia, você aprenderá algumas melhores práticas ao escrever testes de unidade para manter seus testes resilientes e fáceis de entender.</span><span class="sxs-lookup"><span data-stu-id="29170-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="29170-108">Por [John Reese](https://reese.dev) com agradecimentos especiais a [Roy Osherove](http://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="29170-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="29170-109">Por que o teste de unidade?</span><span class="sxs-lookup"><span data-stu-id="29170-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="29170-110">Menos tempo realizando testes funcionais</span><span class="sxs-lookup"><span data-stu-id="29170-110">Less time performing functional tests</span></span>
<span data-ttu-id="29170-111">Testes funcionais são caros.</span><span class="sxs-lookup"><span data-stu-id="29170-111">Functional tests are expensive.</span></span> <span data-ttu-id="29170-112">Normalmente, envolvem abrir o aplicativo e realizar uma série de etapas que você (ou outra pessoa) deve seguir a fim de validar o comportamento esperado.</span><span class="sxs-lookup"><span data-stu-id="29170-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="29170-113">Essas etapas nem sempre podem ser de conhecimento do testador, o que significa que ele terá que entrar em contato com alguém com maior conhecimento na área para executar o teste.</span><span class="sxs-lookup"><span data-stu-id="29170-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="29170-114">O teste em si pode levar segundos para alterações triviais ou minutos para alterações maiores.</span><span class="sxs-lookup"><span data-stu-id="29170-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="29170-115">Por fim, esse processo deve ser repetido para todas as alterações feitas no sistema.</span><span class="sxs-lookup"><span data-stu-id="29170-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="29170-116">Testes de unidade, por outro lado, demoram milissegundos, podem ser executados ao pressionar um botão e não exigem, necessariamente, nenhum conhecimento do sistema em geral.</span><span class="sxs-lookup"><span data-stu-id="29170-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="29170-117">A aprovação ou reprovação no teste cabe ao executor do teste, não ao indivíduo.</span><span class="sxs-lookup"><span data-stu-id="29170-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="29170-118">Proteção contra regressão</span><span class="sxs-lookup"><span data-stu-id="29170-118">Protection against regression</span></span>
<span data-ttu-id="29170-119">Defeitos de regressão são defeitos introduzidos quando uma alteração foi feita no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29170-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="29170-120">É comum os testadores não só testarem seu novo recurso, mas também recursos que existiam antes a fim de verificar se recursos previamente implementados ainda funcionam conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="29170-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="29170-121">Com o teste de unidade, é possível executar novamente todo o conjunto de testes após todo build ou até mesmo após a alteração de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="29170-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="29170-122">Você poderá confiar que o novo código não interromperá a funcionalidade existente.</span><span class="sxs-lookup"><span data-stu-id="29170-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="29170-123">Documentação executável</span><span class="sxs-lookup"><span data-stu-id="29170-123">Executable documentation</span></span>
<span data-ttu-id="29170-124">Nem sempre pode ser óbvio o que um método específico faz ou como ele se comporta diante de uma determinada entrada.</span><span class="sxs-lookup"><span data-stu-id="29170-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="29170-125">Você pode se perguntar: Como esse método se comportará se eu passar uma cadeia de caracteres em branco?</span><span class="sxs-lookup"><span data-stu-id="29170-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="29170-126">Nulo?</span><span class="sxs-lookup"><span data-stu-id="29170-126">Null?</span></span>

<span data-ttu-id="29170-127">Quando você tem um conjunto de testes de unidade bem nomeados, cada teste deve ser capaz de explicar claramente a saída esperada de uma determinada entrada.</span><span class="sxs-lookup"><span data-stu-id="29170-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="29170-128">Além disso, ele deve ser capaz de verificar se isso realmente funciona.</span><span class="sxs-lookup"><span data-stu-id="29170-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="29170-129">Código menos acoplado</span><span class="sxs-lookup"><span data-stu-id="29170-129">Less coupled code</span></span>
<span data-ttu-id="29170-130">Pode ser difícil para o teste de unidade quando o código está bem acoplado.</span><span class="sxs-lookup"><span data-stu-id="29170-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="29170-131">Sem criar testes de unidade para o código que você está escrevendo, o acoplamento pode ser menos aparente.</span><span class="sxs-lookup"><span data-stu-id="29170-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="29170-132">Escrever testes para seu código o desacoplará naturalmente, porque seria mais difícil testar, caso contrário.</span><span class="sxs-lookup"><span data-stu-id="29170-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="29170-133">Características de um bom teste de unidade</span><span class="sxs-lookup"><span data-stu-id="29170-133">Characteristics of a good unit test</span></span>
- <span data-ttu-id="29170-134">**Rápido**.</span><span class="sxs-lookup"><span data-stu-id="29170-134">**Fast**.</span></span> <span data-ttu-id="29170-135">Não é incomum para projetos maduros ter milhares de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="29170-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="29170-136">Os testes de unidade devem levar muito pouco tempo para serem executados.</span><span class="sxs-lookup"><span data-stu-id="29170-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="29170-137">Milissegundos.</span><span class="sxs-lookup"><span data-stu-id="29170-137">Milliseconds.</span></span>
- <span data-ttu-id="29170-138">**Isolado**.</span><span class="sxs-lookup"><span data-stu-id="29170-138">**Isolated**.</span></span> <span data-ttu-id="29170-139">Testes de unidade são autônomos, podem ser executados em isolamento e não têm dependências em nenhum fator externo, como um sistema de arquivos ou o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="29170-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="29170-140">**Repetível**.</span><span class="sxs-lookup"><span data-stu-id="29170-140">**Repeatable**.</span></span> <span data-ttu-id="29170-141">A execução de um teste de unidade deve ser consistente com seus resultados, ou seja, ele sempre retornará o mesmo resultado se você não alterar nada entre execuções.</span><span class="sxs-lookup"><span data-stu-id="29170-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="29170-142">**Verificação automática**.</span><span class="sxs-lookup"><span data-stu-id="29170-142">**Self-Checking**.</span></span> <span data-ttu-id="29170-143">O teste deve ser capaz de detectar automaticamente se ele foi aprovado ou reprovado sem nenhuma interação humana.</span><span class="sxs-lookup"><span data-stu-id="29170-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="29170-144">**Em tempo hábil**.</span><span class="sxs-lookup"><span data-stu-id="29170-144">**Timely**.</span></span> <span data-ttu-id="29170-145">Um teste de unidade não deve levar um tempo desproporcionalmente longo para ser escrito comparado com o código que está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="29170-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="29170-146">Se você achar que o teste do código está levando uma grande quantidade de tempo comparado com a escrita do código, considere um design mais testável.</span><span class="sxs-lookup"><span data-stu-id="29170-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="29170-147">Vamos falar a mesma língua</span><span class="sxs-lookup"><span data-stu-id="29170-147">Let's speak the same language</span></span>
<span data-ttu-id="29170-148">O termo *simular* infelizmente é usado incorretamente quando falamos sobre o teste.</span><span class="sxs-lookup"><span data-stu-id="29170-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="29170-149">Os itens a seguir definem os tipos mais comuns de *falsificações* ao escrever testes de unidade:</span><span class="sxs-lookup"><span data-stu-id="29170-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="29170-150">*Falsificação* – Uma falsificação é um termo genérico que pode ser usado para descrever um stub ou um objeto fictício.</span><span class="sxs-lookup"><span data-stu-id="29170-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="29170-151">Ser um stub ou uma simulação depende do contexto no qual ele é usado.</span><span class="sxs-lookup"><span data-stu-id="29170-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="29170-152">Então, em outras palavras, uma falsificação pode ser um stub ou uma simulação.</span><span class="sxs-lookup"><span data-stu-id="29170-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="29170-153">*Simulação* -um objeto fictício é um objeto falso no sistema que decide se um teste de unidade foi aprovado ou não.</span><span class="sxs-lookup"><span data-stu-id="29170-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="29170-154">Uma simulação começa como falsificação até ser incorrida.</span><span class="sxs-lookup"><span data-stu-id="29170-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="29170-155">*Stub* – Um stub é uma substituição controlável para uma dependência existente (ou colaborador) no sistema.</span><span class="sxs-lookup"><span data-stu-id="29170-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="29170-156">Ao usar um stub, é possível testar seu código sem lidar diretamente com a dependência.</span><span class="sxs-lookup"><span data-stu-id="29170-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="29170-157">Por padrão, uma falsificação começa como um stub.</span><span class="sxs-lookup"><span data-stu-id="29170-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="29170-158">Considere o snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="29170-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="29170-159">Este seria um exemplo de um stub sendo chamado de simulação.</span><span class="sxs-lookup"><span data-stu-id="29170-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="29170-160">Nesse caso, ele é um stub.</span><span class="sxs-lookup"><span data-stu-id="29170-160">In this case, it is a stub.</span></span> <span data-ttu-id="29170-161">Você está passando a ordem como um meio de poder instanciar `Purchase` (o sistema em teste).</span><span class="sxs-lookup"><span data-stu-id="29170-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="29170-162">O nome `MockOrder` também é muito enganoso, porque novamente, a ordem não é uma simulação.</span><span class="sxs-lookup"><span data-stu-id="29170-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="29170-163">Uma abordagem melhor seria</span><span class="sxs-lookup"><span data-stu-id="29170-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="29170-164">Renomeando a classe para `FakeOrder`, você tornou a classe muito mais genérica, a classe pode ser usada como uma simulação ou um stub.</span><span class="sxs-lookup"><span data-stu-id="29170-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="29170-165">O que for melhor para o caso de teste.</span><span class="sxs-lookup"><span data-stu-id="29170-165">Whichever is better for the test case.</span></span> <span data-ttu-id="29170-166">No exemplo acima, `FakeOrder` é usado como um stub.</span><span class="sxs-lookup"><span data-stu-id="29170-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="29170-167">Você não está usando o `FakeOrder` em qualquer forma durante a declaração.</span><span class="sxs-lookup"><span data-stu-id="29170-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="29170-168">`FakeOrder` apenas foi passado para a classe `Purchase` para satisfazer os requisitos do construtor.</span><span class="sxs-lookup"><span data-stu-id="29170-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="29170-169">Para usá-lo como uma Simulação, você poderia fazer algo como isto</span><span class="sxs-lookup"><span data-stu-id="29170-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="29170-170">Nesse caso, você está verificando uma propriedade na Falsificação (declarando em relação a ela), então no snippet de código acima, o `mockOrder` é uma Simulação.</span><span class="sxs-lookup"><span data-stu-id="29170-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29170-171">É importante usar esta terminologia corretamente.</span><span class="sxs-lookup"><span data-stu-id="29170-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="29170-172">Se você chamar seus stubs de "simulações", outros desenvolvedores farão suposições falsas sobre sua intenção.</span><span class="sxs-lookup"><span data-stu-id="29170-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="29170-173">O ponto principal a lembrar sobre simulações versus stub é que simulações são como stubs, mas você declara com relação ao objeto fictício, enquanto você não declara com relação a um stub.</span><span class="sxs-lookup"><span data-stu-id="29170-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="29170-174">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="29170-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="29170-175">Nomeando seus testes</span><span class="sxs-lookup"><span data-stu-id="29170-175">Naming your tests</span></span>
<span data-ttu-id="29170-176">O nome do seu teste deve ser composto por três partes:</span><span class="sxs-lookup"><span data-stu-id="29170-176">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="29170-177">O nome do método que está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="29170-177">The name of the method being tested.</span></span>
- <span data-ttu-id="29170-178">O cenário em que ele está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="29170-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="29170-179">O comportamento esperado quando o cenário é invocado.</span><span class="sxs-lookup"><span data-stu-id="29170-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="29170-180">Por quê?</span><span class="sxs-lookup"><span data-stu-id="29170-180">Why?</span></span>
- <span data-ttu-id="29170-181">Padrões de nomenclatura são importantes, porque eles expressam explicitamente a intenção do teste.</span><span class="sxs-lookup"><span data-stu-id="29170-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="29170-182">Testes são mais do que apenas verificar se seu código funciona; eles também fornecem documentação.</span><span class="sxs-lookup"><span data-stu-id="29170-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="29170-183">Apenas examinando o conjunto de testes de unidade, você deve poder inferir o comportamento do seu código sem mesmo examinar o código em si.</span><span class="sxs-lookup"><span data-stu-id="29170-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="29170-184">Além disso, quando os testes falharem, será possível ver exatamente quais cenários não atendem às suas expectativas.</span><span class="sxs-lookup"><span data-stu-id="29170-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="29170-185">Ruim:</span><span class="sxs-lookup"><span data-stu-id="29170-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="29170-186">Melhor:</span><span class="sxs-lookup"><span data-stu-id="29170-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="29170-187">Organizando seus testes</span><span class="sxs-lookup"><span data-stu-id="29170-187">Arranging your tests</span></span>
<span data-ttu-id="29170-188">**Organizar, Agir, Declarar** é um padrão comum ao testar unidades.</span><span class="sxs-lookup"><span data-stu-id="29170-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="29170-189">Como o nome implica, ele é composto por três ações principais:</span><span class="sxs-lookup"><span data-stu-id="29170-189">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="29170-190">*Organizar* seus objetos, criando e configurando-os conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="29170-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="29170-191">*Agir* sobre um objeto.</span><span class="sxs-lookup"><span data-stu-id="29170-191">*Act* on an object.</span></span>
- <span data-ttu-id="29170-192">*Declarar* que algo está conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="29170-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="29170-193">Por quê?</span><span class="sxs-lookup"><span data-stu-id="29170-193">Why?</span></span>
- <span data-ttu-id="29170-194">Isso separa claramente o que está sendo testado das etapas *organizar* e *declarar*.</span><span class="sxs-lookup"><span data-stu-id="29170-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="29170-195">Menos oportunidade de combinar declarações com o código "Agir".</span><span class="sxs-lookup"><span data-stu-id="29170-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="29170-196">A legibilidade é um dos aspectos mais importante ao escrever um teste.</span><span class="sxs-lookup"><span data-stu-id="29170-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="29170-197">A separação de cada uma dessas ações dentro do teste realça claramente as dependências necessárias para chamar seu código, a maneira como seu código está sendo chamado e o que você está tentando declarar.</span><span class="sxs-lookup"><span data-stu-id="29170-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="29170-198">Embora seja possível combinar algumas etapas e reduzir o tamanho do seu teste, a principal meta é tornar o teste o mais legível possível.</span><span class="sxs-lookup"><span data-stu-id="29170-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="29170-199">Ruim:</span><span class="sxs-lookup"><span data-stu-id="29170-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="29170-200">Melhor:</span><span class="sxs-lookup"><span data-stu-id="29170-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="29170-201">Escrever testes com o mínimo de aprovação</span><span class="sxs-lookup"><span data-stu-id="29170-201">Write minimally passing tests</span></span>
<span data-ttu-id="29170-202">A entrada a ser usada em um teste de unidade deve ser a mais simples possível a fim de verificar o comportamento que você está testando no momento.</span><span class="sxs-lookup"><span data-stu-id="29170-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="29170-203">Por quê?</span><span class="sxs-lookup"><span data-stu-id="29170-203">Why?</span></span>
- <span data-ttu-id="29170-204">Os testes se tornam mais resilientes a alterações futuras na base de código.</span><span class="sxs-lookup"><span data-stu-id="29170-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="29170-205">Mais próximo do comportamento do teste ao longo da implementação.</span><span class="sxs-lookup"><span data-stu-id="29170-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="29170-206">Testes que incluem mais informações do que as necessárias para serem aprovados têm maior chance de introduzir erros no teste e podem deixar a intenção dele menos clara.</span><span class="sxs-lookup"><span data-stu-id="29170-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="29170-207">Ao escrever testes, concentre-se no comportamento.</span><span class="sxs-lookup"><span data-stu-id="29170-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="29170-208">Definir propriedades extra em modelos ou usar valores diferentes de zero quando não for necessário só fará desviar do que você está tentando provar.</span><span class="sxs-lookup"><span data-stu-id="29170-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="29170-209">Ruim:</span><span class="sxs-lookup"><span data-stu-id="29170-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="29170-210">Melhor:</span><span class="sxs-lookup"><span data-stu-id="29170-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="29170-211">Evitar cadeias de caracteres mágicas</span><span class="sxs-lookup"><span data-stu-id="29170-211">Avoid magic strings</span></span>
<span data-ttu-id="29170-212">Nomear variáveis em testes de unidade é tão importante, se não mais importante, do que nomear variáveis no código de produção.</span><span class="sxs-lookup"><span data-stu-id="29170-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="29170-213">Os testes de unidade não devem conter cadeias de caracteres mágicas.</span><span class="sxs-lookup"><span data-stu-id="29170-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="29170-214">Por quê?</span><span class="sxs-lookup"><span data-stu-id="29170-214">Why?</span></span>
- <span data-ttu-id="29170-215">Evita a necessidade de o leitor do teste inspecionar o código de produção a fim de descobrir o que torna o valor especial.</span><span class="sxs-lookup"><span data-stu-id="29170-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="29170-216">Mostra explicitamente o que você está tentando *provar*, em vez de o que você está tentando *realizar*.</span><span class="sxs-lookup"><span data-stu-id="29170-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="29170-217">Cadeias de caracteres mágicas podem gerar confusão no leitor dos seus testes.</span><span class="sxs-lookup"><span data-stu-id="29170-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="29170-218">Se uma cadeia de caracteres parecer estar fora do comum, eles poderão ser perguntar por que um determinado valor foi escolhido para um parâmetro ou valor retornado.</span><span class="sxs-lookup"><span data-stu-id="29170-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="29170-219">Talvez isso os leve a examinar mais detalhadamente os detalhes da implementação, em vez de se concentrar no teste.</span><span class="sxs-lookup"><span data-stu-id="29170-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="29170-220">Ao escrever testes, seu objetivo deve ser expressar o máximo de intenção possível.</span><span class="sxs-lookup"><span data-stu-id="29170-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="29170-221">No caso de cadeias de caracteres mágicas, uma boa abordagem é atribuir esses valores a constantes.</span><span class="sxs-lookup"><span data-stu-id="29170-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="29170-222">Ruim:</span><span class="sxs-lookup"><span data-stu-id="29170-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="29170-223">Melhor:</span><span class="sxs-lookup"><span data-stu-id="29170-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="29170-224">Evitar a lógica em testes</span><span class="sxs-lookup"><span data-stu-id="29170-224">Avoid logic in tests</span></span>
<span data-ttu-id="29170-225">Ao escrever seus testes de unidade, evite a concatenação manual de cadeia de caracteres e condições lógicas como `if`, `while`, `for`, `switch`, etc.</span><span class="sxs-lookup"><span data-stu-id="29170-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="29170-226">Por quê?</span><span class="sxs-lookup"><span data-stu-id="29170-226">Why?</span></span>
- <span data-ttu-id="29170-227">Menor chance de introduzir um bug dentro dos seus testes.</span><span class="sxs-lookup"><span data-stu-id="29170-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="29170-228">Concentre-se no resultado final, em vez de nos detalhes da implementação.</span><span class="sxs-lookup"><span data-stu-id="29170-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="29170-229">Quando você introduz a lógica em seu conjunto de testes, a possibilidade de introduzir um bug nela aumenta drasticamente.</span><span class="sxs-lookup"><span data-stu-id="29170-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="29170-230">O último lugar que você deseja encontrar um bug é dentro do seu conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="29170-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="29170-231">Você deve ter um alto nível de confiança de que seus testes funcionam; caso contrário, você não confiará neles.</span><span class="sxs-lookup"><span data-stu-id="29170-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="29170-232">Testes nos quais você não confia não fornecem nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="29170-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="29170-233">Quando um teste falha, convém ter uma noção de que algo está realmente errado com o seu código e de que isso não pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="29170-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="29170-234">Se a lógica em seu teste parecer inevitável, considere dividir o teste em dois ou mais testes diferentes.</span><span class="sxs-lookup"><span data-stu-id="29170-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="29170-235">Ruim:</span><span class="sxs-lookup"><span data-stu-id="29170-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="29170-236">Melhor:</span><span class="sxs-lookup"><span data-stu-id="29170-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="29170-237">Preferir métodos auxiliares para instalação (setup) e desinstalação (teardown)</span><span class="sxs-lookup"><span data-stu-id="29170-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="29170-238">Se você precisar de um objeto ou estado semelhante para seus testes, prefira um método auxiliar do que usar atributos Setup e Teardown, se existirem.</span><span class="sxs-lookup"><span data-stu-id="29170-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="29170-239">Por quê?</span><span class="sxs-lookup"><span data-stu-id="29170-239">Why?</span></span>
- <span data-ttu-id="29170-240">Menos confusão ao ler os testes, uma vez que todo o código está visível de dentro de cada teste.</span><span class="sxs-lookup"><span data-stu-id="29170-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="29170-241">Menos chance de configurar demais ou de menos para o teste específico.</span><span class="sxs-lookup"><span data-stu-id="29170-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="29170-242">Menos chance de compartilhar estado entre testes, o que cria dependências indesejadas entre eles.</span><span class="sxs-lookup"><span data-stu-id="29170-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="29170-243">Nas estruturas de teste de unidade, `Setup` é chamado antes de cada teste de unidade dentro do seu conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="29170-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="29170-244">Embora alguns possam conceber isso como uma ferramenta útil, ela geralmente acaba levando a testes difíceis de ler e sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="29170-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="29170-245">Cada teste geralmente terá requisitos diferentes para fazer o teste entrar em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="29170-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="29170-246">Infelizmente, `Setup` força você a usar os mesmos requisitos exatos para cada teste.</span><span class="sxs-lookup"><span data-stu-id="29170-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="29170-247">O xUnit removeu SetUp e TearDown a partir da versão 2.x</span><span class="sxs-lookup"><span data-stu-id="29170-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="29170-248">Ruim:</span><span class="sxs-lookup"><span data-stu-id="29170-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="29170-249">Melhor:</span><span class="sxs-lookup"><span data-stu-id="29170-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="29170-250">Evitar várias declarações</span><span class="sxs-lookup"><span data-stu-id="29170-250">Avoid multiple asserts</span></span>
<span data-ttu-id="29170-251">Ao escrever seus testes, tente incluir apenas uma declaração por teste.</span><span class="sxs-lookup"><span data-stu-id="29170-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="29170-252">Abordagens comuns para usar apenas uma declaração incluem:</span><span class="sxs-lookup"><span data-stu-id="29170-252">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="29170-253">Criar um teste separado para cada declaração.</span><span class="sxs-lookup"><span data-stu-id="29170-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="29170-254">Usar testes parametrizados.</span><span class="sxs-lookup"><span data-stu-id="29170-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="29170-255">Por quê?</span><span class="sxs-lookup"><span data-stu-id="29170-255">Why?</span></span>
- <span data-ttu-id="29170-256">Se uma declaração falhar, as subsequentes não serão avaliadas.</span><span class="sxs-lookup"><span data-stu-id="29170-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="29170-257">Garante que você não está declarando vários casos em seus testes.</span><span class="sxs-lookup"><span data-stu-id="29170-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="29170-258">Oferece a você todo o panorama do porquê seus testes estão falhando.</span><span class="sxs-lookup"><span data-stu-id="29170-258">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="29170-259">Ao introduzir várias declarações em um caso de teste, não há garantida de que todas elas serão executadas.</span><span class="sxs-lookup"><span data-stu-id="29170-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="29170-260">Na maioria das estruturas de teste de unidade, após uma declaração falhar em um teste de unidade, os testes seguintes serão considerados reprovados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="29170-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="29170-261">Isso pode ser confuso, porque a funcionalidade que está realmente em funcionamento será mostrada como falha.</span><span class="sxs-lookup"><span data-stu-id="29170-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="29170-262">Uma exceção comum a essa regra é ao declarar em relação a um objeto.</span><span class="sxs-lookup"><span data-stu-id="29170-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="29170-263">Nesse caso, é geralmente aceitável ter várias declarações com relação a cada propriedade para garantir que o objeto está no estado em que você espera que ele esteja.</span><span class="sxs-lookup"><span data-stu-id="29170-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="29170-264">Ruim:</span><span class="sxs-lookup"><span data-stu-id="29170-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="29170-265">Melhor:</span><span class="sxs-lookup"><span data-stu-id="29170-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="29170-266">Validar métodos privados por métodos públicos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="29170-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="29170-267">Na maioria dos casos, não deve haver a necessidade de testar um método privado.</span><span class="sxs-lookup"><span data-stu-id="29170-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="29170-268">Métodos privados são um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="29170-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="29170-269">Você pode pensar dessa forma: métodos privados nunca existem isoladamente.</span><span class="sxs-lookup"><span data-stu-id="29170-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="29170-270">Em algum momento, haverá um método voltado para o público que chame o método privado como parte de sua implementação.</span><span class="sxs-lookup"><span data-stu-id="29170-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="29170-271">O que importa é o resultado final do método público que é chamado no privado.</span><span class="sxs-lookup"><span data-stu-id="29170-271">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="29170-272">Considere o seguinte caso</span><span class="sxs-lookup"><span data-stu-id="29170-272">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="29170-273">Sua primeira reação pode ser começar a escrever um teste para `trimInput` porque você deseja certificar-se de que o método está funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="29170-273">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="29170-274">No entanto, é totalmente possível que `ParseLogLine` manipule `sanitizedInput` de uma maneira inesperada, tornando um teste em relação a `trimInput` inútil.</span><span class="sxs-lookup"><span data-stu-id="29170-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="29170-275">O teste real deve ser feito em relação ao método voltado para o público `ParseLogLine`, porque esse é o que importa no fim das contas.</span><span class="sxs-lookup"><span data-stu-id="29170-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="29170-276">Com esse ponto de vista, se você vir um método privado, encontre o método público e escreva seus testes com relação a esse método.</span><span class="sxs-lookup"><span data-stu-id="29170-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="29170-277">Só porque um método privado retorna o resultado esperado não significa que o sistema que eventualmente chama o método privado usa o resultado corretamente.</span><span class="sxs-lookup"><span data-stu-id="29170-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="29170-278">Referências estáticas de stub</span><span class="sxs-lookup"><span data-stu-id="29170-278">Stub static references</span></span>
<span data-ttu-id="29170-279">Um dos princípios de um teste de unidade é que ele deve ter controle completo do sistema em teste.</span><span class="sxs-lookup"><span data-stu-id="29170-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="29170-280">Isso pode ser problemático quando o código de produção inclui chamadas às referências estáticas (por exemplo, `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="29170-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="29170-281">Considere o código a seguir</span><span class="sxs-lookup"><span data-stu-id="29170-281">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="29170-282">Como esse código pode possivelmente ter unidades testadas?</span><span class="sxs-lookup"><span data-stu-id="29170-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="29170-283">Você pode tentar uma abordagem como</span><span class="sxs-lookup"><span data-stu-id="29170-283">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="29170-284">Infelizmente, você perceberá rapidamente que há alguns problemas com seus testes.</span><span class="sxs-lookup"><span data-stu-id="29170-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="29170-285">Se o conjunto de testes for executado em uma terça-feira, o segundo teste será aprovado, mas o primeiro não.</span><span class="sxs-lookup"><span data-stu-id="29170-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="29170-286">Se o conjunto de testes for executado em qualquer outro dia, o primeiro teste será aprovado, mas o segundo não.</span><span class="sxs-lookup"><span data-stu-id="29170-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="29170-287">Para resolver esses problemas, será necessário introduzir uma *costura* em seu código de produção.</span><span class="sxs-lookup"><span data-stu-id="29170-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="29170-288">Uma abordagem é encapsular o código que você precisa controlar em uma interface e fazer o código de produção depender dessa interface.</span><span class="sxs-lookup"><span data-stu-id="29170-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="29170-289">Seu conjunto de testes agora se torna</span><span class="sxs-lookup"><span data-stu-id="29170-289">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="29170-290">Agora o conjunto de testes tem controle total sobre `DateTime.Now` e pode fazer stub de qualquer valor ao ser chamado no método.</span><span class="sxs-lookup"><span data-stu-id="29170-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
