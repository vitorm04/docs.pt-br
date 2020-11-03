---
title: Melhores práticas para escrever testes de unidade
description: Conheça as melhores práticas para escrever testes de unidade que promovem a qualidade e a resiliência do código em projetos .NET Core e .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 6c1e9a665ad541bf6109634a6df857880ee47042
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281643"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="e2c5b-103">Melhores práticas de teste de unidade com .NET Core e .NET Standard</span><span class="sxs-lookup"><span data-stu-id="e2c5b-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="e2c5b-104">Há diversas vantagens para escrever testes de unidade; eles ajudam com a regressão, fornecem a documentação e facilitam o bom design.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="e2c5b-105">No entanto, testes de unidade difíceis de ler e frágeis podem causar estragos na sua base de código.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="e2c5b-106">Este artigo descreve algumas melhores práticas com relação ao design de teste de unidade para projetos .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="e2c5b-107">Neste guia, você aprenderá algumas melhores práticas ao escrever testes de unidade para manter seus testes resilientes e fáceis de entender.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="e2c5b-108">Por [John Reese](https://reese.dev) com agradecimentos especiais a [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="e2c5b-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="e2c5b-109">Por que o teste de unidade?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="e2c5b-110">Menos tempo realizando testes funcionais</span><span class="sxs-lookup"><span data-stu-id="e2c5b-110">Less time performing functional tests</span></span>

<span data-ttu-id="e2c5b-111">Testes funcionais são caros.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-111">Functional tests are expensive.</span></span> <span data-ttu-id="e2c5b-112">Normalmente, envolvem abrir o aplicativo e realizar uma série de etapas que você (ou outra pessoa) deve seguir a fim de validar o comportamento esperado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="e2c5b-113">Essas etapas nem sempre podem ser de conhecimento do testador, o que significa que ele terá que entrar em contato com alguém com maior conhecimento na área para executar o teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="e2c5b-114">O teste em si pode levar segundos para alterações triviais ou minutos para alterações maiores.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="e2c5b-115">Por fim, esse processo deve ser repetido para todas as alterações feitas no sistema.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="e2c5b-116">Os testes de unidade, por outro lado, levam milissegundos, podem ser executados à imprensa de um botão e não necessariamente exigem qualquer conhecimento do sistema em geral.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button, and don't necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="e2c5b-117">A aprovação ou reprovação no teste cabe ao executor do teste, não ao indivíduo.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="e2c5b-118">Proteção contra regressão</span><span class="sxs-lookup"><span data-stu-id="e2c5b-118">Protection against regression</span></span>

<span data-ttu-id="e2c5b-119">Defeitos de regressão são defeitos introduzidos quando uma alteração foi feita no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="e2c5b-120">É comum os testadores não só testarem seu novo recurso, mas também recursos que existiam antes a fim de verificar se recursos previamente implementados ainda funcionam conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="e2c5b-121">Com o teste de unidade, é possível executar novamente todo o conjunto de testes após todo build ou até mesmo após a alteração de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="e2c5b-122">Você poderá confiar que o novo código não interromperá a funcionalidade existente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="e2c5b-123">Documentação executável</span><span class="sxs-lookup"><span data-stu-id="e2c5b-123">Executable documentation</span></span>

<span data-ttu-id="e2c5b-124">Nem sempre pode ser óbvio o que um método específico faz ou como ele se comporta diante de uma determinada entrada.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="e2c5b-125">Você pode se perguntar: como este método se comportará se eu passar uma cadeia de caracteres em branco?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="e2c5b-126">Nulo?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-126">Null?</span></span>

<span data-ttu-id="e2c5b-127">Quando você tem um conjunto de testes de unidade bem nomeados, cada teste deve ser capaz de explicar claramente a saída esperada de uma determinada entrada.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="e2c5b-128">Além disso, ele deve ser capaz de verificar se isso realmente funciona.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="e2c5b-129">Código menos acoplado</span><span class="sxs-lookup"><span data-stu-id="e2c5b-129">Less coupled code</span></span>

<span data-ttu-id="e2c5b-130">Pode ser difícil para o teste de unidade quando o código está bem acoplado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="e2c5b-131">Sem criar testes de unidade para o código que você está escrevendo, o acoplamento pode ser menos aparente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="e2c5b-132">Escrever testes para seu código o desacoplará naturalmente, porque seria mais difícil testar, caso contrário.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="e2c5b-133">Características de um bom teste de unidade</span><span class="sxs-lookup"><span data-stu-id="e2c5b-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="e2c5b-134">**Rápido**.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-134">**Fast**.</span></span> <span data-ttu-id="e2c5b-135">Não é incomum para projetos maduros ter milhares de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="e2c5b-136">Os testes de unidade devem levar muito pouco tempo para serem executados.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="e2c5b-137">Milissegundos.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-137">Milliseconds.</span></span>
- <span data-ttu-id="e2c5b-138">**Isolado**.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-138">**Isolated**.</span></span> <span data-ttu-id="e2c5b-139">Testes de unidade são autônomos, podem ser executados em isolamento e não têm dependências em nenhum fator externo, como um sistema de arquivos ou o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="e2c5b-140">**Repetível**.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-140">**Repeatable**.</span></span> <span data-ttu-id="e2c5b-141">A execução de um teste de unidade deve ser consistente com seus resultados, ou seja, ele sempre retornará o mesmo resultado se você não alterar nada entre execuções.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="e2c5b-142">**Verificação automática**.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-142">**Self-Checking**.</span></span> <span data-ttu-id="e2c5b-143">O teste deve ser capaz de detectar automaticamente se ele foi aprovado ou reprovado sem nenhuma interação humana.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="e2c5b-144">**Em tempo hábil**.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-144">**Timely**.</span></span> <span data-ttu-id="e2c5b-145">Um teste de unidade não deve levar um tempo desproporcionalmente longo para ser escrito comparado com o código que está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="e2c5b-146">Se você achar que o teste do código está levando uma grande quantidade de tempo comparado com a escrita do código, considere um design mais testável.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="code-coverage"></a><span data-ttu-id="e2c5b-147">Cobertura de código</span><span class="sxs-lookup"><span data-stu-id="e2c5b-147">Code coverage</span></span>

<span data-ttu-id="e2c5b-148">Uma porcentagem alta de cobertura de código geralmente está associada a uma qualidade de código mais alta.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-148">A high code coverage percentage is often associated with a higher quality of code.</span></span> <span data-ttu-id="e2c5b-149">No entanto, a própria medição *não pode* determinar a qualidade do código.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-149">However, the measurement itself *cannot* determine the quality of code.</span></span> <span data-ttu-id="e2c5b-150">Definir uma meta de porcentagem de cobertura de código excessivamente ambicioso pode ser de pré-produção.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-150">Setting an overly ambitious code coverage percentage goal can be counterproductive.</span></span> <span data-ttu-id="e2c5b-151">Imagine um projeto complexo com milhares de ramificações condicionais e imagine que você definiu uma meta de cobertura de código de 95%.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-151">Imagine a complex project with thousands of conditional branches, and imagine that you set a goal of 95% code coverage.</span></span> <span data-ttu-id="e2c5b-152">Atualmente, o projeto mantém a cobertura de código de 90%.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-152">Currently the project maintains 90% code coverage.</span></span> <span data-ttu-id="e2c5b-153">A quantidade de tempo que leva para levar em conta todos os casos de borda dos 5% restantes pode ser um grande empreendimento, e a proposta de valor diminui rapidamente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-153">The amount of time it takes to account for all of the edge cases in the remaining 5% could be a massive undertaking, and the value proposition quickly diminishes.</span></span>

<span data-ttu-id="e2c5b-154">Uma porcentagem alta de cobertura de código não é um indicador de sucesso, nem significa alta qualidade de código.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-154">A high code coverage percentage is not an indicator of success, nor does it imply high code quality.</span></span> <span data-ttu-id="e2c5b-155">Ele representa apenas a quantidade de código coberta pelos testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-155">It just represents the amount of code that is covered by unit tests.</span></span> <span data-ttu-id="e2c5b-156">Para obter mais informações, consulte [cobertura de código de teste de unidade](unit-testing-code-coverage.md).</span><span class="sxs-lookup"><span data-stu-id="e2c5b-156">For more information, see [unit testing code coverage](unit-testing-code-coverage.md).</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="e2c5b-157">Vamos falar a mesma língua</span><span class="sxs-lookup"><span data-stu-id="e2c5b-157">Let's speak the same language</span></span>

<span data-ttu-id="e2c5b-158">A *simulação* de termos, infelizmente, geralmente é usada para falar sobre os testes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-158">The term *mock* is unfortunately often misused when talking about testing.</span></span> <span data-ttu-id="e2c5b-159">Os seguintes pontos definem os tipos mais comuns de *falsificações* ao escrever testes de unidade:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-159">The following points define the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="e2c5b-160">*Falso* -uma falsificação é um termo genérico que pode ser usado para descrever um stub ou um objeto fictício.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-160">*Fake* - A fake is a generic term that can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="e2c5b-161">Seja um stub ou uma simulação depende do contexto no qual ele é usado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-161">Whether it's a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="e2c5b-162">Então, em outras palavras, uma falsificação pode ser um stub ou uma simulação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-162">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="e2c5b-163">*Simulação* -um objeto fictício é um objeto falso no sistema que decide se um teste de unidade foi aprovado ou não.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-163">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="e2c5b-164">Uma simulação começa como falsa até ser declarada.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-164">A mock starts out as a Fake until it's asserted against.</span></span>

<span data-ttu-id="e2c5b-165">*Stub* – Um stub é uma substituição controlável para uma dependência existente (ou colaborador) no sistema.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-165">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="e2c5b-166">Ao usar um stub, é possível testar seu código sem lidar diretamente com a dependência.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-166">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="e2c5b-167">Por padrão, uma falsificação começa como um stub.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-167">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="e2c5b-168">Considere o seguinte snippet de código:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-168">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="e2c5b-169">Este seria um exemplo de um stub sendo chamado de simulação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-169">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="e2c5b-170">Nesse caso, ele é um stub.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-170">In this case, it is a stub.</span></span> <span data-ttu-id="e2c5b-171">Você está passando a ordem como um meio de poder instanciar `Purchase` (o sistema em teste).</span><span class="sxs-lookup"><span data-stu-id="e2c5b-171">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="e2c5b-172">O nome `MockOrder` também é enganoso porque, novamente, a ordem não é uma simulação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-172">The name `MockOrder` is also misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="e2c5b-173">Uma abordagem melhor seria</span><span class="sxs-lookup"><span data-stu-id="e2c5b-173">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="e2c5b-174">Renomeando a classe para `FakeOrder`, você tornou a classe muito mais genérica, a classe pode ser usada como uma simulação ou um stub.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-174">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="e2c5b-175">O que for melhor para o caso de teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-175">Whichever is better for the test case.</span></span> <span data-ttu-id="e2c5b-176">No exemplo acima, `FakeOrder` é usado como um stub.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-176">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="e2c5b-177">Você não está usando o `FakeOrder` em qualquer forma durante a declaração.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-177">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="e2c5b-178">`FakeOrder` foi passado para a `Purchase` classe para atender aos requisitos do construtor.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-178">`FakeOrder` was passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="e2c5b-179">Para usá-lo como uma Simulação, você poderia fazer algo como isto</span><span class="sxs-lookup"><span data-stu-id="e2c5b-179">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="e2c5b-180">Nesse caso, você está verificando uma propriedade na Falsificação (declarando em relação a ela), então no snippet de código acima, o `mockOrder` é uma Simulação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-180">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2c5b-181">É importante usar esta terminologia corretamente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-181">It's important to get this terminology correct.</span></span> <span data-ttu-id="e2c5b-182">Se você chamar seus stubs de "simulações", outros desenvolvedores farão suposições falsas sobre sua intenção.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-182">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="e2c5b-183">O ponto principal a lembrar sobre simulações versus stub é que simulações são como stubs, mas você declara com relação ao objeto fictício, enquanto você não declara com relação a um stub.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-183">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="e2c5b-184">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="e2c5b-184">Best practices</span></span>

<span data-ttu-id="e2c5b-185">Tente não introduzir dependências na infraestrutura ao escrever testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-185">Try not to introduce dependencies on infrastructure when writing unit tests.</span></span> <span data-ttu-id="e2c5b-186">Isso torna os testes lentos e frágeis e deve ser reservado para testes de integração.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-186">These make the tests slow and brittle and should be reserved for integration tests.</span></span> <span data-ttu-id="e2c5b-187">Você pode evitar essas dependências no aplicativo seguindo o [Princípio de Dependências Explícitas](https://deviq.com/explicit-dependencies-principle) e usando a [Injeção de Dependência](../extensions/dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="e2c5b-187">You can avoid these dependencies in your application by following the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle) and using [Dependency Injection](../extensions/dependency-injection.md).</span></span> <span data-ttu-id="e2c5b-188">Você também pode manter seus testes de unidade em um projeto separado de seus testes de integração.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-188">You can also keep your unit tests in a separate project from your integration tests.</span></span> <span data-ttu-id="e2c5b-189">Isso garante que seu projeto de teste de unidade não tenha referências a ou dependências em pacotes de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-189">This ensures your unit test project doesn't have references to or dependencies on infrastructure packages.</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="e2c5b-190">Nomeando seus testes</span><span class="sxs-lookup"><span data-stu-id="e2c5b-190">Naming your tests</span></span>

<span data-ttu-id="e2c5b-191">O nome do seu teste deve ser composto por três partes:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-191">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="e2c5b-192">O nome do método que está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-192">The name of the method being tested.</span></span>
- <span data-ttu-id="e2c5b-193">O cenário em que ele está sendo testado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-193">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="e2c5b-194">O comportamento esperado quando o cenário é invocado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-194">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="e2c5b-195">Por quê?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-195">Why?</span></span>

- <span data-ttu-id="e2c5b-196">Padrões de nomenclatura são importantes, porque eles expressam explicitamente a intenção do teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-196">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="e2c5b-197">Testes são mais do que apenas verificar se seu código funciona; eles também fornecem documentação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-197">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="e2c5b-198">Apenas examinando o conjunto de testes de unidade, você deve poder inferir o comportamento do seu código sem mesmo examinar o código em si.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-198">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="e2c5b-199">Além disso, quando os testes falharem, será possível ver exatamente quais cenários não atendem às suas expectativas.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-199">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="e2c5b-200">Ruim:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-200">Bad:</span></span>

[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="e2c5b-201">Melhor:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-201">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="e2c5b-202">Organizando seus testes</span><span class="sxs-lookup"><span data-stu-id="e2c5b-202">Arranging your tests</span></span>

<span data-ttu-id="e2c5b-203">**Organizar, Agir, Declarar** é um padrão comum ao testar unidades.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-203">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="e2c5b-204">Como o nome implica, ele é composto por três ações principais:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-204">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="e2c5b-205">*Organizar* seus objetos, criando e configurando-os conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-205">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="e2c5b-206">*Agir* em um objeto.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-206">*Act* on an object.</span></span>
- <span data-ttu-id="e2c5b-207">*Declarar* que algo está conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-207">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="e2c5b-208">Por quê?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-208">Why?</span></span>

- <span data-ttu-id="e2c5b-209">Isso separa claramente o que está sendo testado das etapas *organizar* e *declarar*.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-209">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="e2c5b-210">Menos oportunidade de combinar declarações com o código "Agir".</span><span class="sxs-lookup"><span data-stu-id="e2c5b-210">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="e2c5b-211">A legibilidade é um dos aspectos mais importante ao escrever um teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-211">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="e2c5b-212">A separação de cada uma dessas ações dentro do teste realça claramente as dependências necessárias para chamar seu código, a maneira como seu código está sendo chamado e o que você está tentando declarar.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-212">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="e2c5b-213">Embora seja possível combinar algumas etapas e reduzir o tamanho do seu teste, a principal meta é tornar o teste o mais legível possível.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-213">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="e2c5b-214">Ruim:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-214">Bad:</span></span>

[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="e2c5b-215">Melhor:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-215">Better:</span></span>

[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="e2c5b-216">Escrever testes com o mínimo de aprovação</span><span class="sxs-lookup"><span data-stu-id="e2c5b-216">Write minimally passing tests</span></span>

<span data-ttu-id="e2c5b-217">A entrada a ser usada em um teste de unidade deve ser a mais simples possível a fim de verificar o comportamento que você está testando no momento.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-217">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="e2c5b-218">Por quê?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-218">Why?</span></span>

- <span data-ttu-id="e2c5b-219">Os testes se tornam mais resilientes a alterações futuras na base de código.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-219">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="e2c5b-220">Mais próximo do comportamento do teste ao longo da implementação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-220">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="e2c5b-221">Testes que incluem mais informações do que as necessárias para serem aprovados têm maior chance de introduzir erros no teste e podem deixar a intenção dele menos clara.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-221">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="e2c5b-222">Ao escrever testes, você deseja se concentrar no comportamento.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-222">When writing tests, you want to focus on the behavior.</span></span> <span data-ttu-id="e2c5b-223">Definir propriedades extra em modelos ou usar valores diferentes de zero quando não for necessário só fará desviar do que você está tentando provar.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-223">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="e2c5b-224">Ruim:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-224">Bad:</span></span>

[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="e2c5b-225">Melhor:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-225">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="e2c5b-226">Evitar cadeias de caracteres mágicas</span><span class="sxs-lookup"><span data-stu-id="e2c5b-226">Avoid magic strings</span></span>

<span data-ttu-id="e2c5b-227">Nomear variáveis em testes de unidade é tão importante, se não mais importante, do que nomear variáveis no código de produção.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-227">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="e2c5b-228">Os testes de unidade não devem conter cadeias de caracteres mágicas.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-228">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="e2c5b-229">Por quê?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-229">Why?</span></span>

- <span data-ttu-id="e2c5b-230">Evita a necessidade de o leitor do teste inspecionar o código de produção a fim de descobrir o que torna o valor especial.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-230">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="e2c5b-231">Mostra explicitamente o que você está tentando *provar* , em vez de o que você está tentando *realizar*.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-231">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="e2c5b-232">Cadeias de caracteres mágicas podem gerar confusão no leitor dos seus testes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-232">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="e2c5b-233">Se uma cadeia de caracteres parecer estar fora do comum, eles poderão ser perguntar por que um determinado valor foi escolhido para um parâmetro ou valor retornado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-233">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="e2c5b-234">Talvez isso os leve a examinar mais detalhadamente os detalhes da implementação, em vez de se concentrar no teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-234">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="e2c5b-235">Ao escrever testes, seu objetivo deve ser expressar o máximo de intenção possível.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-235">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="e2c5b-236">No caso de cadeias de caracteres mágicas, uma boa abordagem é atribuir esses valores a constantes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-236">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="e2c5b-237">Ruim:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-237">Bad:</span></span>

[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="e2c5b-238">Melhor:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-238">Better:</span></span>

[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="e2c5b-239">Evitar a lógica em testes</span><span class="sxs-lookup"><span data-stu-id="e2c5b-239">Avoid logic in tests</span></span>

<span data-ttu-id="e2c5b-240">Ao escrever seus testes de unidade, evite a concatenação manual de cadeia de caracteres e condições lógicas como `if`, `while`, `for`, `switch`, etc.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-240">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="e2c5b-241">Por quê?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-241">Why?</span></span>

- <span data-ttu-id="e2c5b-242">Menor chance de introduzir um bug dentro dos seus testes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-242">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="e2c5b-243">Concentre-se no resultado final, em vez de nos detalhes da implementação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-243">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="e2c5b-244">Quando você introduz a lógica em seu conjunto de testes, a possibilidade de introduzir um bug nela aumenta drasticamente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-244">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="e2c5b-245">O último lugar que você deseja encontrar um bug é dentro do seu conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-245">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="e2c5b-246">Você deve ter um alto nível de confiança de que seus testes funcionam; caso contrário, você não confiará neles.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-246">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="e2c5b-247">Testes nos quais você não confia não fornecem nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-247">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="e2c5b-248">Quando um teste falha, convém ter uma noção de que algo está realmente errado com o seu código e de que isso não pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-248">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="e2c5b-249">Se a lógica em seu teste parecer inevitável, considere dividir o teste em dois ou mais testes diferentes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-249">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="e2c5b-250">Ruim:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-250">Bad:</span></span>

[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="e2c5b-251">Melhor:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-251">Better:</span></span>

[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="e2c5b-252">Preferir métodos auxiliares para instalação (setup) e desinstalação (teardown)</span><span class="sxs-lookup"><span data-stu-id="e2c5b-252">Prefer helper methods to setup and teardown</span></span>

<span data-ttu-id="e2c5b-253">Se você precisar de um objeto ou estado semelhante para seus testes, prefira um método auxiliar do que o aproveitamento `Setup` e os `Teardown` atributos, se existirem.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-253">If you require a similar object or state for your tests, prefer a helper method than leveraging `Setup` and `Teardown` attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="e2c5b-254">Por quê?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-254">Why?</span></span>

- <span data-ttu-id="e2c5b-255">Menos confusão ao ler os testes, uma vez que todo o código está visível de dentro de cada teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-255">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="e2c5b-256">Menos chance de configurar demais ou de menos para o teste específico.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-256">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="e2c5b-257">Menos chance de compartilhar o estado entre os testes, que cria dependências indesejadas entre eles.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-257">Less chance of sharing state between tests, which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="e2c5b-258">Nas estruturas de teste de unidade, `Setup` é chamado antes de cada teste de unidade dentro do seu conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-258">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="e2c5b-259">Embora alguns possam conceber isso como uma ferramenta útil, ela geralmente acaba levando a testes difíceis de ler e sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-259">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="e2c5b-260">Cada teste geralmente terá requisitos diferentes para fazer o teste entrar em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-260">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="e2c5b-261">Infelizmente, `Setup` força você a usar os mesmos requisitos exatos para cada teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-261">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="e2c5b-262">O xUnit removeu SetUp e TearDown a partir da versão 2.x</span><span class="sxs-lookup"><span data-stu-id="e2c5b-262">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="e2c5b-263">Ruim:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-263">Bad:</span></span>

[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="e2c5b-264">Melhor:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-264">Better:</span></span>

[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="e2c5b-265">Evitar várias declarações</span><span class="sxs-lookup"><span data-stu-id="e2c5b-265">Avoid multiple asserts</span></span>

<span data-ttu-id="e2c5b-266">Ao escrever seus testes, tente incluir apenas uma declaração por teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-266">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="e2c5b-267">Abordagens comuns para usar apenas uma declaração incluem:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-267">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="e2c5b-268">Criar um teste separado para cada declaração.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-268">Create a separate test for each assert.</span></span>
- <span data-ttu-id="e2c5b-269">Usar testes parametrizados.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-269">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="e2c5b-270">Por quê?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-270">Why?</span></span>

- <span data-ttu-id="e2c5b-271">Se uma declaração falhar, as subsequentes não serão avaliadas.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-271">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="e2c5b-272">Garante que você não está declarando vários casos em seus testes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-272">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="e2c5b-273">Oferece a você todo o panorama do porquê seus testes estão falhando.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-273">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="e2c5b-274">Ao introduzir várias declarações em um caso de teste, não há garantida de que todas elas serão executadas.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-274">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="e2c5b-275">Na maioria das estruturas de teste de unidade, após uma declaração falhar em um teste de unidade, os testes seguintes serão considerados reprovados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-275">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="e2c5b-276">Isso pode ser confuso, porque a funcionalidade que está realmente em funcionamento será mostrada como falha.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-276">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="e2c5b-277">Uma exceção comum a essa regra é ao declarar em relação a um objeto.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-277">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="e2c5b-278">Nesse caso, é geralmente aceitável ter várias declarações com relação a cada propriedade para garantir que o objeto está no estado em que você espera que ele esteja.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-278">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="e2c5b-279">Ruim:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-279">Bad:</span></span>

[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="e2c5b-280">Melhor:</span><span class="sxs-lookup"><span data-stu-id="e2c5b-280">Better:</span></span>

[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="e2c5b-281">Validar métodos privados por métodos públicos de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="e2c5b-281">Validate private methods by unit testing public methods</span></span>

<span data-ttu-id="e2c5b-282">Na maioria dos casos, não deve haver a necessidade de testar um método privado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-282">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="e2c5b-283">Métodos privados são um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-283">Private methods are an implementation detail.</span></span> <span data-ttu-id="e2c5b-284">Você pode pensar dessa forma: métodos privados nunca existem isoladamente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-284">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="e2c5b-285">Em algum momento, haverá um método voltado para o público que chame o método privado como parte de sua implementação.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-285">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="e2c5b-286">O que importa é o resultado final do método público que é chamado no privado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-286">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="e2c5b-287">Considere o seguinte caso</span><span class="sxs-lookup"><span data-stu-id="e2c5b-287">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="e2c5b-288">Sua primeira reação pode ser começar a escrever um teste para `TrimInput` porque você deseja certificar-se de que o método está funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-288">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="e2c5b-289">No entanto, é totalmente possível que `ParseLogLine` manipule `sanitizedInput` de uma maneira inesperada, tornando um teste em relação a `TrimInput` inútil.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-289">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="e2c5b-290">O teste real deve ser feito em relação ao método voltado para o público `ParseLogLine`, porque esse é o que importa no fim das contas.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-290">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_StartsAndEndsWithSpace_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="e2c5b-291">Com esse ponto de vista, se você vir um método privado, encontre o método público e escreva seus testes com relação a esse método.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-291">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="e2c5b-292">Só porque um método privado retorna o resultado esperado não significa que o sistema que eventualmente chama o método privado usa o resultado corretamente.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-292">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="e2c5b-293">Referências estáticas de stub</span><span class="sxs-lookup"><span data-stu-id="e2c5b-293">Stub static references</span></span>

<span data-ttu-id="e2c5b-294">Um dos princípios de um teste de unidade é que ele deve ter controle completo do sistema em teste.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-294">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="e2c5b-295">Isso pode ser problemático quando o código de produção inclui chamadas para referências estáticas (por exemplo, `DateTime.Now` ).</span><span class="sxs-lookup"><span data-stu-id="e2c5b-295">This can be problematic when production code includes calls to static references (for example, `DateTime.Now`).</span></span> <span data-ttu-id="e2c5b-296">Considere o código a seguir</span><span class="sxs-lookup"><span data-stu-id="e2c5b-296">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if (DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="e2c5b-297">Como esse código pode possivelmente ter unidades testadas?</span><span class="sxs-lookup"><span data-stu-id="e2c5b-297">How can this code possibly be unit tested?</span></span> <span data-ttu-id="e2c5b-298">Você pode tentar uma abordagem como</span><span class="sxs-lookup"><span data-stu-id="e2c5b-298">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
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

<span data-ttu-id="e2c5b-299">Infelizmente, você perceberá rapidamente que há alguns problemas com seus testes.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-299">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="e2c5b-300">Se o conjunto de testes for executado em uma terça-feira, o segundo teste será aprovado, mas o primeiro não.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-300">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="e2c5b-301">Se o conjunto de testes for executado em qualquer outro dia, o primeiro teste será aprovado, mas o segundo não.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-301">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="e2c5b-302">Para resolver esses problemas, será necessário introduzir uma *costura* em seu código de produção.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-302">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="e2c5b-303">Uma abordagem é encapsular o código que você precisa controlar em uma interface e fazer o código de produção depender dessa interface.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-303">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if (dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="e2c5b-304">Seu conjunto de testes agora se torna</span><span class="sxs-lookup"><span data-stu-id="e2c5b-304">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
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

<span data-ttu-id="e2c5b-305">Agora o conjunto de testes tem controle total sobre `DateTime.Now` e pode fazer stub de qualquer valor ao ser chamado no método.</span><span class="sxs-lookup"><span data-stu-id="e2c5b-305">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
