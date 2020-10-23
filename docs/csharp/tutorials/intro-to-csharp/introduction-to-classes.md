---
title: Tutorial Classes e objetos – introdução ao C#
description: Crie seu primeiro programa em C# e explore os conceitos de orientado a objeto
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 0955b0ac33b346b9880c8af70bd73cb458120f35
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434892"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="4c5e3-103">Explorar programação orientada a objeto com classes e objetos</span><span class="sxs-lookup"><span data-stu-id="4c5e3-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="4c5e3-104">Este tutorial espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="4c5e3-105">O tutorial do .NET [Olá, mundo em 10 minutos](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) tem instruções para configurar seu ambiente de desenvolvimento local no Windows, Linux ou MacOS.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="4c5e3-106">Uma visão geral dos comandos que você usará está em [Familiarize-se com as ferramentas de desenvolvimento](local-environment.md), com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="4c5e3-107">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4c5e3-107">Create your application</span></span>

<span data-ttu-id="4c5e3-108">Usando uma janela de terminal, crie um diretório chamado *classes*.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="4c5e3-109">Você compilará o aplicativo nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-109">You'll build your application there.</span></span> <span data-ttu-id="4c5e3-110">Altere para esse diretório e digite `dotnet new console` na janela do console.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="4c5e3-111">Esse comando cria o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-111">This command creates your application.</span></span> <span data-ttu-id="4c5e3-112">Abra *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-112">Open *Program.cs*.</span></span> <span data-ttu-id="4c5e3-113">Ele deverá ser parecido com:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-113">It should look like this:</span></span>

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="4c5e3-114">Neste tutorial, você criará novos tipos que representam uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="4c5e3-115">Normalmente, os desenvolvedores definem cada classe em um arquivo de texto diferente.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="4c5e3-116">Isso facilita o gerenciamento à medida que o tamanho do programa aumenta.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="4c5e3-117">Crie um novo arquivo chamado *BankAccount.cs* no diretório *classes*.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="4c5e3-118">Esse arquivo conterá a definição de uma \***conta bancária**_.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-118">This file will contain the definition of a \***bank account**_.</span></span> <span data-ttu-id="4c5e3-119">A programação orientada a objeto organiza o código criando tipos na forma de _*_classes_*_.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-119">Object Oriented programming organizes code by creating types in the form of _*_classes_*_.</span></span> <span data-ttu-id="4c5e3-120">Essas classes contêm o código que representa uma entidade específica.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="4c5e3-121">A classe `BankAccount` representa uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="4c5e3-122">O código implementa operações específicas por meio de métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="4c5e3-123">Neste tutorial, a conta bancária dá suporte a este comportamento:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="4c5e3-124">Ela tem um número com 10 dígitos que identifica exclusivamente a conta bancária.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="4c5e3-125">Ela tem uma cadeia de caracteres que armazena o nome ou os nomes dos proprietários.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="4c5e3-126">O saldo pode ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="4c5e3-127">Ela aceita depósitos.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-127">It accepts deposits.</span></span>
1. <span data-ttu-id="4c5e3-128">Ele aceita saques.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="4c5e3-129">O saldo inicial deve ser positivo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="4c5e3-130">Os saques não podem resultar em um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="4c5e3-131">Definir o tipo de conta bancária</span><span class="sxs-lookup"><span data-stu-id="4c5e3-131">Define the bank account type</span></span>

<span data-ttu-id="4c5e3-132">Você pode começar criando as noções básicas de uma classe que define esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="4c5e3-133">Crie um novo arquivo usando o comando _\*file: New\*\*.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-133">Create a new file using the _*File:New*\* command.</span></span> <span data-ttu-id="4c5e3-134">Nomeie-o como *BankAccount.cs*.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="4c5e3-135">Adicione o seguinte código ao arquivo *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="4c5e3-135">Add the following code to your *BankAccount.cs* file:</span></span>

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

<span data-ttu-id="4c5e3-136">Antes de continuar, vamos dar uma olhada no que você compilou.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="4c5e3-137">A declaração `namespace` fornece uma maneira de organizar logicamente seu código.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="4c5e3-138">Este tutorial é relativamente pequeno, portanto, você colocará todo o código em um namespace.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="4c5e3-139">`public class BankAccount` define a classe ou o tipo que você está criando.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="4c5e3-140">Tudo dentro do `{` e `}` que segue a declaração de classe define o estado e o comportamento da classe.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="4c5e3-141">Há cinco \***Membros**_ da `BankAccount` classe.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-141">There are five \***members**_ of the `BankAccount` class.</span></span> <span data-ttu-id="4c5e3-142">As três primeiras são _*_Propriedades_*_.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-142">The first three are _*_properties_*_.</span></span> <span data-ttu-id="4c5e3-143">Propriedades são elementos de dados que podem ter um código que impõe a validação ou outras regras.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="4c5e3-144">Os dois últimos são _*_métodos_*_.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-144">The last two are _*_methods_*_.</span></span> <span data-ttu-id="4c5e3-145">Os métodos são blocos de código que executam uma única função.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="4c5e3-146">A leitura dos nomes de cada um dos membros deve fornecer informações suficientes para você, ou outro desenvolvedor, entender o que a classe faz.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="4c5e3-147">Abrir uma nova conta</span><span class="sxs-lookup"><span data-stu-id="4c5e3-147">Open a new account</span></span>

<span data-ttu-id="4c5e3-148">O primeiro recurso a ser implementado serve para abrir uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="4c5e3-149">Quando um cliente abre uma conta, ele deve fornecer um saldo inicial e informações sobre o proprietário, ou proprietários, dessa conta.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="4c5e3-150">Criar um novo objeto do `BankAccount` tipo significa definir um _*_Construtor_*_ que atribua esses valores.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-150">Creating a new object of the `BankAccount` type means defining a _*_constructor_*_ that assigns those values.</span></span> <span data-ttu-id="4c5e3-151">Um _*_Construtor_*_ é um membro que tem o mesmo nome que a classe.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-151">A _*_constructor_*_ is a member that has the same name as the class.</span></span> <span data-ttu-id="4c5e3-152">Ele é usado para inicializar objetos desse tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="4c5e3-153">Adicione o seguinte construtor ao `BankAccount` tipo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="4c5e3-154">Coloque o seguinte código acima da declaração de `MakeDeposit` :</span><span class="sxs-lookup"><span data-stu-id="4c5e3-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="4c5e3-155">Os construtores são chamados quando você cria um objeto usando [`new`](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="4c5e3-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="4c5e3-156">Substitua a linha `Console.WriteLine("Hello World!");` em _Program. cs \* pelo código a seguir (substitua `<name>` pelo seu nome):</span><span class="sxs-lookup"><span data-stu-id="4c5e3-156">Replace the line `Console.WriteLine("Hello World!");` in _Program.cs\* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="4c5e3-157">Vamos executar o que você criou até agora.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-157">Let's run what you've built so far.</span></span> <span data-ttu-id="4c5e3-158">Se você estiver usando o Visual Studio, selecione **Iniciar sem depuração** no menu **executar** .</span><span class="sxs-lookup"><span data-stu-id="4c5e3-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="4c5e3-159">Se você estiver usando uma linha de comando, digite `dotnet run` o diretório em que você criou o projeto.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="4c5e3-160">Você notou que o número da conta está em branco?</span><span class="sxs-lookup"><span data-stu-id="4c5e3-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="4c5e3-161">É hora de corrigir isso.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-161">It's time to fix that.</span></span> <span data-ttu-id="4c5e3-162">O número da conta deve ser atribuído na construção do objeto.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="4c5e3-163">Mas não é responsabilidade do chamador criá-lo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="4c5e3-164">O código da classe `BankAccount` deve saber como atribuir novos números de conta.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="4c5e3-165">Uma maneira simples de fazer isso é começar com um número de 10 dígitos.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="4c5e3-166">Incremente-o à medida que novas contas são criadas.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-166">Increment it when each new account is created.</span></span> <span data-ttu-id="4c5e3-167">Por fim, armazene o número da conta atual quando um objeto for construído.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="4c5e3-168">Adicione uma declaração de membro à `BankAccount` classe.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="4c5e3-169">Coloque a seguinte linha de código após a chave de abertura `{` no início da `BankAccount` classe:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="4c5e3-170">Este é um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-170">This is a data member.</span></span> <span data-ttu-id="4c5e3-171">Ele é `private`, o que significa que ele só pode ser acessado pelo código dentro da classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="4c5e3-172">É uma maneira de separar as responsabilidades públicas (como ter um número de conta) da implementação privada (como os números de conta são gerados).</span><span class="sxs-lookup"><span data-stu-id="4c5e3-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="4c5e3-173">Ele também é `static`, o que significa que é compartilhado por todos os objetos `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="4c5e3-174">O valor de uma variável não estática é exclusivo para cada instância do objeto `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="4c5e3-175">Adicione as duas linhas a seguir ao construtor para atribuir o número da conta.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="4c5e3-176">Coloque-os após a linha que diz `this.Balance = initialBalance` :</span><span class="sxs-lookup"><span data-stu-id="4c5e3-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="4c5e3-177">Digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="4c5e3-178">Criar depósitos e saques</span><span class="sxs-lookup"><span data-stu-id="4c5e3-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="4c5e3-179">A classe da conta bancária precisa aceitar depósitos e saques para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="4c5e3-180">Vamos implementar depósitos e saques criando um diário de todas as transações da conta.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="4c5e3-181">Isso apresenta algumas vantagens em comparação à simples atualização do saldo em cada transação.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="4c5e3-182">O histórico pode ser usado para auditar todas as transações e gerenciar os saldos diários.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="4c5e3-183">Ao calcular o saldo do histórico de todas as transações, quando for necessário, todos os erros corrigidos em uma única transação serão refletidos corretamente no saldo no próximo cálculo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="4c5e3-184">Vamos começar criando um novo tipo para representar uma transação.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="4c5e3-185">É um tipo simples que não tem qualquer responsabilidade.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="4c5e3-186">Ele precisa de algumas propriedades.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-186">It needs a few properties.</span></span> <span data-ttu-id="4c5e3-187">Crie um novo arquivo chamado *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="4c5e3-188">Adicione os seguintes códigos a ela:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="4c5e3-189">Agora, vamos adicionar um <xref:System.Collections.Generic.List%601> de `Transaction` objetos à classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="4c5e3-190">Adicione a seguinte declaração após o Construtor em seu arquivo *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="4c5e3-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="4c5e3-191">A classe <xref:System.Collections.Generic.List%601> exige que você importe um namespace diferente.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="4c5e3-192">Adicione o seguinte no início de *BankAccount.cs*:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="4c5e3-193">Agora, vamos calcular corretamente o `Balance` .</span><span class="sxs-lookup"><span data-stu-id="4c5e3-193">Now, let's correctly compute the `Balance`.</span></span> <span data-ttu-id="4c5e3-194">O saldo atual pode ser encontrado somando-se os valores de todas as transações.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-194">The current balance can be found by summing the values of all transactions.</span></span> <span data-ttu-id="4c5e3-195">Como o código é atualmente, você só pode obter o saldo inicial da conta, portanto, você precisará atualizar a `Balance` propriedade.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-195">As the code is currently, you can only get the initial balance of the account, so you'll have to update the `Balance` property.</span></span> <span data-ttu-id="4c5e3-196">Substitua a linha `public decimal Balance { get; }` em *BankAccount.cs* pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-196">Replace the line `public decimal Balance { get; }` in *BankAccount.cs* with the following code:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="4c5e3-197">Este exemplo mostra um aspecto importante de \***Properties**_.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-197">This example shows an important aspect of \***properties**_.</span></span> <span data-ttu-id="4c5e3-198">Agora, você está calculando o saldo quando outro programador solicita o valor.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-198">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="4c5e3-199">Seu cálculo enumera todas as transações e fornece a soma como o saldo atual.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-199">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="4c5e3-200">Depois, implemente os métodos `MakeDeposit` e `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-200">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="4c5e3-201">Esses métodos aplicarão as duas últimas regras: que o saldo inicial deve ser positivo, e que qualquer saque não pode criar um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-201">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="4c5e3-202">Isso introduz o conceito de _*_exceções_*_.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-202">This introduces the concept of _*_exceptions_*_.</span></span> <span data-ttu-id="4c5e3-203">A forma padrão de indicar que um método não pode concluir seu trabalho com êxito é lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-203">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="4c5e3-204">O tipo de exceção e a mensagem associada a ele descrevem o erro.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-204">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="4c5e3-205">Aqui, o método `MakeDeposit` lançará uma exceção se o valor do depósito for negativo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-205">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="4c5e3-206">O `MakeWithdrawal` método lançará uma exceção se a quantidade de retirada for negativa ou se a aplicação da retirada resultar em um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-206">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="4c5e3-207">Adicione o seguinte código após a declaração da `allTransactions` lista:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-207">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="4c5e3-208">A [`throw`](../../language-reference/keywords/throw.md) instrução _*gera*\* uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-208">The [`throw`](../../language-reference/keywords/throw.md) statement _*throws*\* an exception.</span></span> <span data-ttu-id="4c5e3-209">A execução do bloco atual é encerrada e o controle transferido para o bloco `catch` da primeira correspondência encontrado na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-209">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="4c5e3-210">Você adicionará um bloco `catch` para testar esse código um pouco mais tarde.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-210">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="4c5e3-211">O construtor deve receber uma alteração para que adicione uma transação inicial, em vez de atualizar o saldo diretamente.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-211">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="4c5e3-212">Como você já escreveu o método `MakeDeposit`, chame-o de seu construtor.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-212">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="4c5e3-213">O construtor concluído deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-213">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="4c5e3-214"><xref:System.DateTime.Now?displayProperty=nameWithType> é uma propriedade que retorna a data e a hora atuais.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-214"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="4c5e3-215">Teste isso adicionando alguns depósitos e retirados em seu `Main` método, seguindo o código que cria um novo `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="4c5e3-215">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="4c5e3-216">Em seguida, teste se você está capturando condições de erro tentando criar uma conta com um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-216">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="4c5e3-217">Adicione o código a seguir após o código anterior que você acabou de adicionar:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-217">Add the following code after the preceding code you just added:</span></span>

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="4c5e3-218">Você usa as [ `try` `catch` instruções e](../../language-reference/keywords/try-catch.md) para marcar um bloco de código que pode gerar exceções e capturar os erros que você espera.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-218">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="4c5e3-219">Você pode usar a mesma técnica para testar o código que gera uma exceção para um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-219">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="4c5e3-220">Adicione o seguinte código ao final do seu `Main` método:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-220">Add the following code at the end of your `Main` method:</span></span>

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="4c5e3-221">Salve o arquivo e digite `dotnet run` para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-221">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="4c5e3-222">Desafio – registrar em log todas as transações</span><span class="sxs-lookup"><span data-stu-id="4c5e3-222">Challenge - log all transactions</span></span>

<span data-ttu-id="4c5e3-223">Para concluir este tutorial, escreva o método `GetAccountHistory` que cria um `string` para o histórico de transações.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-223">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="4c5e3-224">Adicione esse método ao tipo `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-224">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="4c5e3-225">Isso usa a classe <xref:System.Text.StringBuilder> para formatar uma cadeia de caracteres que contém uma linha para cada transação.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-225">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="4c5e3-226">Você viu o código de formatação da cadeia de caracteres anteriormente nesses tutoriais.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-226">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="4c5e3-227">Um caractere novo é `\t`.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-227">One new character is `\t`.</span></span> <span data-ttu-id="4c5e3-228">Ele insere uma guia para formatar a saída.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-228">That inserts a tab to format the output.</span></span>

<span data-ttu-id="4c5e3-229">Adicione esta linha para testá-la no *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-229">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="4c5e3-230">Execute o programa para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="4c5e3-230">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4c5e3-231">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4c5e3-231">Next steps</span></span>

<span data-ttu-id="4c5e3-232">Se você ficou preso, pode ver a origem deste tutorial [em nosso repositório GitHub](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span><span class="sxs-lookup"><span data-stu-id="4c5e3-232">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="4c5e3-233">Você pode continuar com o tutorial de [programação orientada a objeto](object-oriented-programming.md) .</span><span class="sxs-lookup"><span data-stu-id="4c5e3-233">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="4c5e3-234">Você pode saber mais sobre esses conceitos nestes artigos:</span><span class="sxs-lookup"><span data-stu-id="4c5e3-234">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="4c5e3-235">Instrução if e else</span><span class="sxs-lookup"><span data-stu-id="4c5e3-235">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="4c5e3-236">Instrução while</span><span class="sxs-lookup"><span data-stu-id="4c5e3-236">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="4c5e3-237">Instrução do</span><span class="sxs-lookup"><span data-stu-id="4c5e3-237">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="4c5e3-238">Instrução for</span><span class="sxs-lookup"><span data-stu-id="4c5e3-238">For statement</span></span>](../../language-reference/keywords/for.md)
