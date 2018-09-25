---
title: Melhores práticas para escrever testes de unidade
description: Conheça as melhores práticas para escrever testes de unidade que promovem a qualidade e resiliência do código
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 69fe0cae141d1ed1e1281eecd78bf03e6e8be961
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527725"
---
# <a name="unit-testing-best-practices"></a><span data-ttu-id="fc4b6-103">Melhores práticas de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="fc4b6-103">Unit testing best practices</span></span>

<span data-ttu-id="fc4b6-104">Por [John Reese](http://reesespieces.io) com agradecimentos especiais a [Roy Osherove](http://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="fc4b6-104">By [John Reese](http://reesespieces.io) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

<span data-ttu-id="fc4b6-105">Há diversas vantagens para escrever testes de unidade; eles ajudam com a regressão, fornecem a documentação e facilitam o bom design.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-105">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="fc4b6-106">No entanto, testes de unidade difíceis de ler e frágeis podem causar estragos na sua base de código.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-106">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span>

<span data-ttu-id="fc4b6-107">Neste guia, você aprenderá algumas melhores práticas ao escrever testes de unidade para manter seus testes resilientes e fáceis de entender.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="fc4b6-108">Por que o teste de unidade?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-108">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="fc4b6-109">Menos tempo realizando testes funcionais</span><span class="sxs-lookup"><span data-stu-id="fc4b6-109">Less time performing functional tests</span></span>
<span data-ttu-id="fc4b6-110">Testes funcionais são caros.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-110">Functional tests are expensive.</span></span> <span data-ttu-id="fc4b6-111">Normalmente, envolvem abrir o aplicativo e realizar uma série de etapas que você (ou outra pessoa) deve seguir a fim de validar o comportamento esperado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-111">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="fc4b6-112">Essas etapas nem sempre podem ser de conhecimento do testador, o que significa que ele terá que entrar em contato com alguém com maior conhecimento na área para executar o teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-112">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="fc4b6-113">O teste em si pode levar segundos para alterações triviais ou minutos para alterações maiores.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-113">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="fc4b6-114">Por fim, esse processo deve ser repetido para todas as alterações feitas no sistema.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-114">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="fc4b6-115">Testes de unidade, por outro lado, demoram milissegundos, podem ser executados ao pressionar um botão e não exigem, necessariamente, nenhum conhecimento do sistema em geral.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-115">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="fc4b6-116">A aprovação ou reprovação no teste cabe ao executor do teste, não ao indivíduo.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-116">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="fc4b6-117">Proteção contra regressão</span><span class="sxs-lookup"><span data-stu-id="fc4b6-117">Protection against regression</span></span>
<span data-ttu-id="fc4b6-118">Defeitos de regressão são defeitos introduzidos quando uma alteração foi feita no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-118">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="fc4b6-119">É comum os testadores não só testarem seu novo recurso, mas também recursos que existiam antes a fim de verificar se recursos previamente implementados ainda funcionam conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-119">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="fc4b6-120">Com o teste de unidade, é possível executar novamente todo o conjunto de testes após todo build ou até mesmo após a alteração de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-120">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="fc4b6-121">Você poderá confiar que o novo código não interromperá a funcionalidade existente.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-121">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="fc4b6-122">Documentação executável</span><span class="sxs-lookup"><span data-stu-id="fc4b6-122">Executable documentation</span></span>
<span data-ttu-id="fc4b6-123">Nem sempre pode ser óbvio o que um método específico faz ou como ele se comporta diante de uma determinada entrada.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-123">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="fc4b6-124">Você pode se perguntar: como este método se comportará se eu passar uma cadeia de caracteres em branco?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-124">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="fc4b6-125">Nulo?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-125">Null?</span></span>

<span data-ttu-id="fc4b6-126">Quando você tem um conjunto de testes de unidade bem nomeados, cada teste deve ser capaz de explicar claramente a saída esperada de uma determinada entrada.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-126">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="fc4b6-127">Além disso, ele deve ser capaz de verificar se isso realmente funciona.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-127">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="fc4b6-128">Código menos acoplado</span><span class="sxs-lookup"><span data-stu-id="fc4b6-128">Less coupled code</span></span>
<span data-ttu-id="fc4b6-129">Pode ser difícil para o teste de unidade quando o código está bem acoplado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-129">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="fc4b6-130">Sem criar testes de unidade para o código que você está escrevendo, o acoplamento pode ser menos aparente.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-130">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="fc4b6-131">Escrever testes para seu código o desacoplará naturalmente, porque seria mais difícil testar, caso contrário.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-131">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="fc4b6-132">Características de um bom teste de unidade</span><span class="sxs-lookup"><span data-stu-id="fc4b6-132">Characteristics of a good unit test</span></span>
- <span data-ttu-id="fc4b6-133">**Rápido**.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-133">**Fast**.</span></span> <span data-ttu-id="fc4b6-134">Não é incomum para projetos maduros ter milhares de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-134">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="fc4b6-135">Os testes de unidade devem levar muito pouco tempo para serem executados.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-135">Unit tests should take very little time to run.</span></span> <span data-ttu-id="fc4b6-136">Milissegundos.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-136">Milliseconds.</span></span>
- <span data-ttu-id="fc4b6-137">**Isolado**.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-137">**Isolated**.</span></span> <span data-ttu-id="fc4b6-138">Testes de unidade são autônomos, podem ser executados em isolamento e não têm dependências em nenhum fator externo, como um sistema de arquivos ou o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-138">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="fc4b6-139">**Repetível**.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-139">**Repeatable**.</span></span> <span data-ttu-id="fc4b6-140">A execução de um teste de unidade deve ser consistente com seus resultados, ou seja, ele sempre retornará o mesmo resultado se você não alterar nada entre execuções.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-140">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="fc4b6-141">**Verificação automática**.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-141">**Self-Checking**.</span></span> <span data-ttu-id="fc4b6-142">O teste deve ser capaz de detectar automaticamente se ele foi aprovado ou reprovado sem nenhuma interação humana.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-142">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="fc4b6-143">**Em tempo hábil**.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-143">**Timely**.</span></span> <span data-ttu-id="fc4b6-144">Um teste de unidade não deve levar um tempo desproporcionalmente longo para ser escrito comparado com o código que está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-144">A unit test should not take a disproportionally long time to write compared to the code being tested.</span></span> <span data-ttu-id="fc4b6-145">Se você achar que o teste do código está levando uma grande quantidade de tempo comparado com a escrita do código, considere um design mais testável.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-145">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="fc4b6-146">Vamos falar a mesma língua</span><span class="sxs-lookup"><span data-stu-id="fc4b6-146">Let's speak the same language</span></span>
<span data-ttu-id="fc4b6-147">O termo *simular* infelizmente é usado incorretamente quando falamos sobre o teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-147">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="fc4b6-148">Os itens a seguir definem os tipos mais comuns de *falsificações* ao escrever testes de unidade:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-148">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="fc4b6-149">*Falsificação* – Uma falsificação é um termo genérico que pode ser usado para descrever um stub ou um objeto fictício.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-149">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="fc4b6-150">Ser um stub ou uma simulação depende do contexto no qual ele é usado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-150">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="fc4b6-151">Então, em outras palavras, uma falsificação pode ser um stub ou uma simulação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-151">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="fc4b6-152">*Simulação* -um objeto fictício é um objeto falso no sistema que decide se um teste de unidade foi aprovado ou não.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-152">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="fc4b6-153">Uma simulação começa como falsificação até ser incorrida.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-153">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="fc4b6-154">*Stub* – Um stub é uma substituição controlável para uma dependência existente (ou colaborador) no sistema.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-154">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="fc4b6-155">Ao usar um stub, é possível testar seu código sem lidar diretamente com a dependência.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-155">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="fc4b6-156">Por padrão, uma falsificação começa como um stub.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-156">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="fc4b6-157">Considere o snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-157">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="fc4b6-158">Este seria um exemplo de um stub sendo chamado de simulação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-158">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="fc4b6-159">Nesse caso, ele é um stub.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-159">In this case, it is a stub.</span></span> <span data-ttu-id="fc4b6-160">Você está passando a ordem como um meio de poder instanciar `Purchase` (o sistema em teste).</span><span class="sxs-lookup"><span data-stu-id="fc4b6-160">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="fc4b6-161">O nome `MockOrder` também é muito enganoso, porque novamente, a ordem não é uma simulação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-161">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="fc4b6-162">Uma abordagem melhor seria</span><span class="sxs-lookup"><span data-stu-id="fc4b6-162">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="fc4b6-163">Renomeando a classe para `FakeOrder`, você tornou a classe muito mais genérica, a classe pode ser usada como uma simulação ou um stub.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-163">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="fc4b6-164">O que for melhor para o caso de teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-164">Whichever is better for the test case.</span></span> <span data-ttu-id="fc4b6-165">No exemplo acima, `FakeOrder` é usado como um stub.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-165">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="fc4b6-166">Você não está usando o `FakeOrder` em qualquer forma durante a declaração.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-166">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="fc4b6-167">`FakeOrder` apenas foi passado para a classe `Purchase` para satisfazer os requisitos do construtor.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-167">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="fc4b6-168">Para usá-lo como uma Simulação, você poderia fazer algo como isto</span><span class="sxs-lookup"><span data-stu-id="fc4b6-168">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="fc4b6-169">Nesse caso, você está verificando uma propriedade na Falsificação (declarando em relação a ela), então no snippet de código acima, o `mockOrder` é uma Simulação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-169">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc4b6-170">É importante usar esta terminologia corretamente.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-170">It's important to get this terminology correct.</span></span> <span data-ttu-id="fc4b6-171">Se você chamar seus stubs de "simulações", outros desenvolvedores farão suposições falsas sobre sua intenção.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-171">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="fc4b6-172">O ponto principal a lembrar sobre simulações versus stub é que simulações são como stubs, mas você declara com relação ao objeto fictício, enquanto você não declara com relação a um stub.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-172">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="fc4b6-173">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="fc4b6-173">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="fc4b6-174">Nomeando seus testes</span><span class="sxs-lookup"><span data-stu-id="fc4b6-174">Naming your tests</span></span>
<span data-ttu-id="fc4b6-175">O nome do seu teste deve ser composto por três partes:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-175">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="fc4b6-176">O nome do método que está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-176">The name of the method being tested.</span></span>
- <span data-ttu-id="fc4b6-177">O cenário em que ele está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-177">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="fc4b6-178">O comportamento esperado quando o cenário é invocado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-178">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="fc4b6-179">Por quê?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-179">Why?</span></span>
- <span data-ttu-id="fc4b6-180">Padrões de nomenclatura são importantes, porque eles expressam explicitamente a intenção do teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-180">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="fc4b6-181">Testes são mais do que apenas verificar se seu código funciona; eles também fornecem documentação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-181">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="fc4b6-182">Apenas examinando o conjunto de testes de unidade, você deve poder inferir o comportamento do seu código sem mesmo examinar o código em si.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-182">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="fc4b6-183">Além disso, quando os testes falharem, será possível ver exatamente quais cenários não atendem às suas expectativas.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-183">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="fc4b6-184">Ruim:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-184">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="fc4b6-185">Melhor:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-185">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="fc4b6-186">Organizando seus testes</span><span class="sxs-lookup"><span data-stu-id="fc4b6-186">Arranging your tests</span></span>
<span data-ttu-id="fc4b6-187">**Organizar, Agir, Declarar** é um padrão comum ao testar unidades.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-187">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="fc4b6-188">Como o nome implica, ele é composto por três ações principais:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-188">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="fc4b6-189">*Organizar* seus objetos, criando e configurando-os conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-189">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="fc4b6-190">*Agir* sobre um objeto.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-190">*Act* on an object.</span></span>
- <span data-ttu-id="fc4b6-191">*Declarar* que algo está conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-191">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="fc4b6-192">Por quê?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-192">Why?</span></span>
- <span data-ttu-id="fc4b6-193">Isso separa claramente o que está sendo testado das etapas *organizar* e *declarar*.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-193">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="fc4b6-194">Menos oportunidade de combinar declarações com o código "Agir".</span><span class="sxs-lookup"><span data-stu-id="fc4b6-194">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="fc4b6-195">A legibilidade é um dos aspectos mais importante ao escrever um teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-195">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="fc4b6-196">A separação de cada uma dessas ações dentro do teste realça claramente as dependências necessárias para chamar seu código, a maneira como seu código está sendo chamado e o que você está tentando declarar.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-196">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="fc4b6-197">Embora seja possível combinar algumas etapas e reduzir o tamanho do seu teste, a principal meta é tornar o teste o mais legível possível.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-197">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="fc4b6-198">Ruim:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-198">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="fc4b6-199">Melhor:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-199">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="fc4b6-200">Escrever testes com o mínimo de aprovação</span><span class="sxs-lookup"><span data-stu-id="fc4b6-200">Write minimally passing tests</span></span>
<span data-ttu-id="fc4b6-201">A entrada a ser usada em um teste de unidade deve ser a mais simples possível a fim de verificar o comportamento que você está testando no momento.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-201">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="fc4b6-202">Por quê?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-202">Why?</span></span>
- <span data-ttu-id="fc4b6-203">Os testes se tornam mais resilientes a alterações futuras na base de código.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-203">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="fc4b6-204">Mais próximo do comportamento do teste ao longo da implementação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-204">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="fc4b6-205">Testes que incluem mais informações do que as necessárias para serem aprovados têm maior chance de introduzir erros no teste e podem deixar a intenção dele menos clara.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-205">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="fc4b6-206">Ao escrever testes, concentre-se no comportamento.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-206">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="fc4b6-207">Definir propriedades extra em modelos ou usar valores diferentes de zero quando não for necessário só fará desviar do que você está tentando provar.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-207">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="fc4b6-208">Ruim:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-208">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="fc4b6-209">Melhor:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-209">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="fc4b6-210">Evitar cadeias de caracteres mágicas</span><span class="sxs-lookup"><span data-stu-id="fc4b6-210">Avoid magic strings</span></span>
<span data-ttu-id="fc4b6-211">Nomear variáveis em testes de unidade é tão importante, se não mais importante, do que nomear variáveis no código de produção.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-211">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="fc4b6-212">Os testes de unidade não devem conter cadeias de caracteres mágicas.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-212">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="fc4b6-213">Por quê?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-213">Why?</span></span>
- <span data-ttu-id="fc4b6-214">Evita a necessidade de o leitor do teste inspecionar o código de produção a fim de descobrir o que torna o valor especial.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-214">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="fc4b6-215">Mostra explicitamente o que você está tentando *provar*, em vez de o que você está tentando *realizar*.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-215">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="fc4b6-216">Cadeias de caracteres mágicas podem gerar confusão no leitor dos seus testes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-216">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="fc4b6-217">Se uma cadeia de caracteres parecer estar fora do comum, eles poderão ser perguntar por que um determinado valor foi escolhido para um parâmetro ou valor retornado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-217">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="fc4b6-218">Talvez isso os leve a examinar mais detalhadamente os detalhes da implementação, em vez de se concentrar no teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-218">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="fc4b6-219">Ao escrever testes, seu objetivo deve ser expressar o máximo de intenção possível.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-219">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="fc4b6-220">No caso de cadeias de caracteres mágicas, uma boa abordagem é atribuir esses valores a constantes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-220">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="fc4b6-221">Ruim:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-221">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="fc4b6-222">Melhor:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-222">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="fc4b6-223">Evitar a lógica em testes</span><span class="sxs-lookup"><span data-stu-id="fc4b6-223">Avoid logic in tests</span></span>
<span data-ttu-id="fc4b6-224">Ao escrever seus testes de unidade, evite a concatenação manual de cadeia de caracteres e condições lógicas como `if`, `while`, `for`, `switch`, etc.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-224">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="fc4b6-225">Por quê?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-225">Why?</span></span>
- <span data-ttu-id="fc4b6-226">Menor chance de introduzir um bug dentro dos seus testes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-226">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="fc4b6-227">Concentre-se no resultado final, em vez de nos detalhes da implementação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-227">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="fc4b6-228">Quando você introduz a lógica em seu conjunto de testes, a possibilidade de introduzir um bug nela aumenta drasticamente.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-228">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="fc4b6-229">O último lugar que você deseja encontrar um bug é dentro do seu conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-229">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="fc4b6-230">Você deve ter um alto nível de confiança de que seus testes funcionam; caso contrário, você não confiará neles.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-230">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="fc4b6-231">Testes nos quais você não confia não fornecem nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-231">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="fc4b6-232">Quando um teste falha, convém ter uma noção de que algo está realmente errado com o seu código e de que isso não pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-232">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="fc4b6-233">Se a lógica em seu teste parecer inevitável, considere dividir o teste em dois ou mais testes diferentes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-233">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="fc4b6-234">Ruim:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-234">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="fc4b6-235">Melhor:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-235">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="fc4b6-236">Preferir métodos auxiliares para instalação (setup) e desinstalação (teardown)</span><span class="sxs-lookup"><span data-stu-id="fc4b6-236">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="fc4b6-237">Se você precisar de um objeto ou estado semelhante para seus testes, prefira um método auxiliar do que usar atributos Setup e Teardown, se existirem.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-237">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="fc4b6-238">Por quê?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-238">Why?</span></span>
- <span data-ttu-id="fc4b6-239">Menos confusão ao ler os testes, uma vez que todo o código está visível de dentro de cada teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-239">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="fc4b6-240">Menos chance de configurar demais ou de menos para o teste específico.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-240">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="fc4b6-241">Menos chance de compartilhar estado entre testes, o que cria dependências indesejadas entre eles.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-241">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="fc4b6-242">Nas estruturas de teste de unidade, `Setup` é chamado antes de cada teste de unidade dentro do seu conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-242">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="fc4b6-243">Embora alguns possam conceber isso como uma ferramenta útil, ela geralmente acaba levando a testes difíceis de ler e sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-243">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="fc4b6-244">Cada teste geralmente terá requisitos diferentes para fazer o teste entrar em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-244">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="fc4b6-245">Infelizmente, `Setup` força você a usar os mesmos requisitos exatos para cada teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-245">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="fc4b6-246">O xUnit removeu SetUp e TearDown a partir da versão 2.x</span><span class="sxs-lookup"><span data-stu-id="fc4b6-246">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="fc4b6-247">Ruim:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-247">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="fc4b6-248">Melhor:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-248">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="fc4b6-249">Evitar várias declarações</span><span class="sxs-lookup"><span data-stu-id="fc4b6-249">Avoid multiple asserts</span></span>
<span data-ttu-id="fc4b6-250">Ao escrever seus testes, tente incluir apenas uma declaração por teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-250">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="fc4b6-251">Abordagens comuns para usar apenas uma declaração incluem:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-251">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="fc4b6-252">Criar um teste separado para cada declaração.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-252">Create a separate test for each assert.</span></span>
- <span data-ttu-id="fc4b6-253">Usar testes parametrizados.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-253">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="fc4b6-254">Por quê?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-254">Why?</span></span>
- <span data-ttu-id="fc4b6-255">Se uma declaração falhar, as subsequentes não serão avaliadas.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-255">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="fc4b6-256">Garante que você não está declarando vários casos em seus testes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-256">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="fc4b6-257">Oferece a você todo o panorama do porquê seus testes estão falhando.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-257">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="fc4b6-258">Ao introduzir várias declarações em um caso de teste, não há garantida de que todas elas serão executadas.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-258">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="fc4b6-259">Na maioria das estruturas de teste de unidade, após uma declaração falhar em um teste de unidade, os testes seguintes serão considerados reprovados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-259">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="fc4b6-260">Isso pode ser confuso, porque a funcionalidade que está realmente em funcionamento será mostrada como falha.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-260">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="fc4b6-261">Uma exceção comum a essa regra é ao declarar em relação a um objeto.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-261">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="fc4b6-262">Nesse caso, é geralmente aceitável ter várias declarações com relação a cada propriedade para garantir que o objeto está no estado em que você espera que ele esteja.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-262">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="fc4b6-263">Ruim:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-263">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="fc4b6-264">Melhor:</span><span class="sxs-lookup"><span data-stu-id="fc4b6-264">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="fc4b6-265">Validar métodos privados por métodos públicos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="fc4b6-265">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="fc4b6-266">Na maioria dos casos, não deve haver a necessidade de testar um método privado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-266">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="fc4b6-267">Métodos privados são um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-267">Private methods are an implementation detail.</span></span> <span data-ttu-id="fc4b6-268">Você pode pensar dessa forma: métodos privados nunca existem isoladamente.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-268">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="fc4b6-269">Em algum momento, haverá um método voltado para o público que chame o método privado como parte de sua implementação.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-269">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="fc4b6-270">O que importa é o resultado final do método público que é chamado no privado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-270">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="fc4b6-271">Considere o seguinte caso</span><span class="sxs-lookup"><span data-stu-id="fc4b6-271">Consider the following case</span></span>

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

<span data-ttu-id="fc4b6-272">Sua primeira reação pode ser começar a escrever um teste para `trimInput` porque você deseja certificar-se de que o método está funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-272">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="fc4b6-273">No entanto, é totalmente possível que `ParseLogLine` manipule `sanitizedInput` de uma maneira inesperada, tornando um teste em relação a `trimInput` inútil.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-273">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="fc4b6-274">O teste real deve ser feito em relação ao método voltado para o público `ParseLogLine`, porque esse é o que importa no fim das contas.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-274">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="fc4b6-275">Com esse ponto de vista, se você vir um método privado, encontre o método público e escreva seus testes com relação a esse método.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-275">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="fc4b6-276">Só porque um método privado retorna o resultado esperado não significa que o sistema que eventualmente chama o método privado usa o resultado corretamente.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-276">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="fc4b6-277">Referências estáticas de stub</span><span class="sxs-lookup"><span data-stu-id="fc4b6-277">Stub static references</span></span>
<span data-ttu-id="fc4b6-278">Um dos princípios de um teste de unidade é que ele deve ter controle completo do sistema em teste.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-278">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="fc4b6-279">Isso pode ser problemático quando o código de produção inclui chamadas às referências estáticas (por exemplo, `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="fc4b6-279">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="fc4b6-280">Considere o código a seguir</span><span class="sxs-lookup"><span data-stu-id="fc4b6-280">Consider the following code</span></span>

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

<span data-ttu-id="fc4b6-281">Como esse código pode possivelmente ter unidades testadas?</span><span class="sxs-lookup"><span data-stu-id="fc4b6-281">How can this code possibly be unit tested?</span></span> <span data-ttu-id="fc4b6-282">Você pode tentar uma abordagem como</span><span class="sxs-lookup"><span data-stu-id="fc4b6-282">You may try an approach such as</span></span>

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

<span data-ttu-id="fc4b6-283">Infelizmente, você perceberá rapidamente que há alguns problemas com seus testes.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-283">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="fc4b6-284">Se o conjunto de testes for executado em uma terça-feira, o segundo teste será aprovado, mas o primeiro não.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-284">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="fc4b6-285">Se o conjunto de testes for executado em qualquer outro dia, o primeiro teste será aprovado, mas o segundo não.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-285">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="fc4b6-286">Para resolver esses problemas, será necessário introduzir uma *costura* em seu código de produção.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-286">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="fc4b6-287">Uma abordagem é encapsular o código que você precisa controlar em uma interface e fazer o código de produção depender dessa interface.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-287">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public bool GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
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

<span data-ttu-id="fc4b6-288">Seu conjunto de testes agora se torna</span><span class="sxs-lookup"><span data-stu-id="fc4b6-288">Your test suite now becomes</span></span>

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

<span data-ttu-id="fc4b6-289">Agora o conjunto de testes tem controle total sobre `DateTime.Now` e pode fazer stub de qualquer valor ao ser chamado no método.</span><span class="sxs-lookup"><span data-stu-id="fc4b6-289">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
