---
title: Tutorial Classes e objetos – introdução ao C#
description: Crie seu primeiro programa em C# e explore os conceitos de orientado a objeto
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 6b4c135b7adf96de3a234cde02485a1e84fc9fd3
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204776"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="00c84-103">Explorar programação orientada a objeto com classes e objetos</span><span class="sxs-lookup"><span data-stu-id="00c84-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="00c84-104">Este tutorial espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="00c84-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="00c84-105">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="00c84-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="00c84-106">Uma visão geral dos comandos que você usará está em [Familiarize-se com as ferramentas de desenvolvimento](local-environment.md), com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="00c84-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="00c84-107">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="00c84-107">Create your application</span></span>

<span data-ttu-id="00c84-108">Usando uma janela de terminal, crie um diretório chamado **classes**.</span><span class="sxs-lookup"><span data-stu-id="00c84-108">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="00c84-109">Você compilará o aplicativo nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="00c84-109">You'll build your application there.</span></span> <span data-ttu-id="00c84-110">Altere para esse diretório e digite `dotnet new console` na janela do console.</span><span class="sxs-lookup"><span data-stu-id="00c84-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="00c84-111">Esse comando cria o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00c84-111">This command creates your application.</span></span> <span data-ttu-id="00c84-112">Abra **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="00c84-112">Open **Program.cs**.</span></span> <span data-ttu-id="00c84-113">Ele deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="00c84-113">It should look like this:</span></span>

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

<span data-ttu-id="00c84-114">Neste tutorial, você criará novos tipos que representam uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="00c84-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="00c84-115">Normalmente, os desenvolvedores definem cada classe em um arquivo de texto diferente.</span><span class="sxs-lookup"><span data-stu-id="00c84-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="00c84-116">Isso facilita o gerenciamento à medida que o tamanho do programa aumenta.</span><span class="sxs-lookup"><span data-stu-id="00c84-116">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="00c84-117">Crie um novo arquivo chamado **BankAccount.cs** no diretório **classes**.</span><span class="sxs-lookup"><span data-stu-id="00c84-117">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="00c84-118">Esse arquivo conterá a definição de uma ***conta bancária***.</span><span class="sxs-lookup"><span data-stu-id="00c84-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="00c84-119">A programação Orientada a Objeto organiza o código por meio da criação de tipos na forma de ***classes***.</span><span class="sxs-lookup"><span data-stu-id="00c84-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="00c84-120">Essas classes contêm o código que representa uma entidade específica.</span><span class="sxs-lookup"><span data-stu-id="00c84-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="00c84-121">A classe `BankAccount` representa uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="00c84-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="00c84-122">O código implementa operações específicas por meio de métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="00c84-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="00c84-123">Neste tutorial, a conta bancária dá suporte a este comportamento:</span><span class="sxs-lookup"><span data-stu-id="00c84-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="00c84-124">Ela tem um número com 10 dígitos que identifica exclusivamente a conta bancária.</span><span class="sxs-lookup"><span data-stu-id="00c84-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="00c84-125">Ela tem uma cadeia de caracteres que armazena o nome ou os nomes dos proprietários.</span><span class="sxs-lookup"><span data-stu-id="00c84-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="00c84-126">O saldo pode ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="00c84-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="00c84-127">Ela aceita depósitos.</span><span class="sxs-lookup"><span data-stu-id="00c84-127">It accepts deposits.</span></span>
1. <span data-ttu-id="00c84-128">Ele aceita saques.</span><span class="sxs-lookup"><span data-stu-id="00c84-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="00c84-129">O saldo inicial deve ser positivo.</span><span class="sxs-lookup"><span data-stu-id="00c84-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="00c84-130">Os saques não podem resultar em um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="00c84-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="00c84-131">Definir o tipo de conta bancária</span><span class="sxs-lookup"><span data-stu-id="00c84-131">Define the bank account type</span></span>

<span data-ttu-id="00c84-132">Você pode começar criando as noções básicas de uma classe que define esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="00c84-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="00c84-133">Ela deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="00c84-133">It would look like this:</span></span>

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

<span data-ttu-id="00c84-134">Antes de continuar, vamos dar uma olhada no que você compilou.</span><span class="sxs-lookup"><span data-stu-id="00c84-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="00c84-135">A declaração `namespace` fornece uma maneira de organizar logicamente seu código.</span><span class="sxs-lookup"><span data-stu-id="00c84-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="00c84-136">Este tutorial é relativamente pequeno, portanto, você colocará todo o código em um namespace.</span><span class="sxs-lookup"><span data-stu-id="00c84-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="00c84-137">`public class BankAccount` define a classe ou o tipo que você está criando.</span><span class="sxs-lookup"><span data-stu-id="00c84-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="00c84-138">Tudo dentro de `{` e `}` logo após a declaração da classe define o comportamento da classe.</span><span class="sxs-lookup"><span data-stu-id="00c84-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="00c84-139">Há cinco ***membros*** na classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="00c84-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="00c84-140">As três primeiras são ***propriedades***.</span><span class="sxs-lookup"><span data-stu-id="00c84-140">The first three are ***properties***.</span></span> <span data-ttu-id="00c84-141">Propriedades são elementos de dados que podem ter um código que impõe a validação ou outras regras.</span><span class="sxs-lookup"><span data-stu-id="00c84-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="00c84-142">Os últimos dois são ***métodos***.</span><span class="sxs-lookup"><span data-stu-id="00c84-142">The last two are ***methods***.</span></span> <span data-ttu-id="00c84-143">Os métodos são blocos de código que executam uma única função.</span><span class="sxs-lookup"><span data-stu-id="00c84-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="00c84-144">A leitura dos nomes de cada um dos membros deve fornecer informações suficientes para você, ou outro desenvolvedor, entender o que a classe faz.</span><span class="sxs-lookup"><span data-stu-id="00c84-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="00c84-145">Abrir uma nova conta</span><span class="sxs-lookup"><span data-stu-id="00c84-145">Open a new account</span></span>

<span data-ttu-id="00c84-146">O primeiro recurso a ser implementado serve para abrir uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="00c84-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="00c84-147">Quando um cliente abre uma conta, ele deve fornecer um saldo inicial e informações sobre o proprietário, ou proprietários, dessa conta.</span><span class="sxs-lookup"><span data-stu-id="00c84-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="00c84-148">A criação de novo objeto do tipo `BankAccount` significa a definição de um ***construtor*** que atribui esses valores.</span><span class="sxs-lookup"><span data-stu-id="00c84-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="00c84-149">Um ***construtor*** é um membro que tem o mesmo nome da classe.</span><span class="sxs-lookup"><span data-stu-id="00c84-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="00c84-150">Ele é usado para inicializar objetos desse tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="00c84-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="00c84-151">Adicione o seguinte construtor ao tipo `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="00c84-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="00c84-152">Construtores são chamados quando você cria um objeto usando [`new`](../../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="00c84-152">Constructors are called when you create an object using [`new`](../../language-reference/keywords/new.md).</span></span> <span data-ttu-id="00c84-153">Substitua a linha `Console.WriteLine("Hello World!");` no arquivo ***program.cs*** pela seguinte linha (substitua `<name>` pelo seu nome):</span><span class="sxs-lookup"><span data-stu-id="00c84-153">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="00c84-154">Digite `dotnet run` para ver o que acontece.</span><span class="sxs-lookup"><span data-stu-id="00c84-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="00c84-155">Você notou que o número da conta está em branco?</span><span class="sxs-lookup"><span data-stu-id="00c84-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="00c84-156">É hora de corrigir isso.</span><span class="sxs-lookup"><span data-stu-id="00c84-156">It's time to fix that.</span></span> <span data-ttu-id="00c84-157">O número da conta deve ser atribuído na construção do objeto.</span><span class="sxs-lookup"><span data-stu-id="00c84-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="00c84-158">Mas não é responsabilidade do chamador criá-lo.</span><span class="sxs-lookup"><span data-stu-id="00c84-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="00c84-159">O código da classe `BankAccount` deve saber como atribuir novos números de conta.</span><span class="sxs-lookup"><span data-stu-id="00c84-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="00c84-160">Uma maneira simples de fazer isso é começar com um número de 10 dígitos.</span><span class="sxs-lookup"><span data-stu-id="00c84-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="00c84-161">Incremente-o à medida que novas contas são criadas.</span><span class="sxs-lookup"><span data-stu-id="00c84-161">Increment it when each new account is created.</span></span> <span data-ttu-id="00c84-162">Por fim, armazene o número da conta atual quando um objeto for construído.</span><span class="sxs-lookup"><span data-stu-id="00c84-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="00c84-163">Adicione a seguinte declaração de membro à classe `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="00c84-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="00c84-164">Este é um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="00c84-164">This is a data member.</span></span> <span data-ttu-id="00c84-165">Ele é `private`, o que significa que ele só pode ser acessado pelo código dentro da classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="00c84-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="00c84-166">É uma maneira de separar as responsabilidades públicas (como ter um número de conta) da implementação privada (como os números de conta são gerados.) Ele também é `static`, o que significa que é compartilhado por todos os objetos `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="00c84-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="00c84-167">O valor de uma variável não estática é exclusivo para cada instância do objeto `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="00c84-167">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="00c84-168">Adicione as duas linhas a seguir ao construtor para atribuir o número da conta:</span><span class="sxs-lookup"><span data-stu-id="00c84-168">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="00c84-169">Digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="00c84-169">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="00c84-170">Criar depósitos e saques</span><span class="sxs-lookup"><span data-stu-id="00c84-170">Create deposits and withdrawals</span></span>

<span data-ttu-id="00c84-171">A classe da conta bancária precisa aceitar depósitos e saques para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="00c84-171">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="00c84-172">Vamos implementar depósitos e saques criando um diário de todas as transações da conta.</span><span class="sxs-lookup"><span data-stu-id="00c84-172">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="00c84-173">Isso apresenta algumas vantagens em comparação à simples atualização do saldo em cada transação.</span><span class="sxs-lookup"><span data-stu-id="00c84-173">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="00c84-174">O histórico pode ser usado para auditar todas as transações e gerenciar os saldos diários.</span><span class="sxs-lookup"><span data-stu-id="00c84-174">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="00c84-175">Ao calcular o saldo do histórico de todas as transações, quando for necessário, todos os erros corrigidos em uma única transação serão refletidos corretamente no saldo no próximo cálculo.</span><span class="sxs-lookup"><span data-stu-id="00c84-175">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="00c84-176">Vamos começar criando um novo tipo para representar uma transação.</span><span class="sxs-lookup"><span data-stu-id="00c84-176">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="00c84-177">É um tipo simples que não tem qualquer responsabilidade.</span><span class="sxs-lookup"><span data-stu-id="00c84-177">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="00c84-178">Ele precisa de algumas propriedades.</span><span class="sxs-lookup"><span data-stu-id="00c84-178">It needs a few properties.</span></span> <span data-ttu-id="00c84-179">Crie um novo arquivo chamado ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="00c84-179">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="00c84-180">Adicione o seguinte código a ele:</span><span class="sxs-lookup"><span data-stu-id="00c84-180">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="00c84-181">Agora, vamos adicionar um <xref:System.Collections.Generic.List%601> de `Transaction` objetos à classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="00c84-181">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="00c84-182">Adicione a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="00c84-182">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="00c84-183">A classe <xref:System.Collections.Generic.List%601> exige que você importe um namespace diferente.</span><span class="sxs-lookup"><span data-stu-id="00c84-183">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="00c84-184">Adicione o seguinte no início de **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="00c84-184">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="00c84-185">Agora, vamos alterar como `Balance` é reportado.</span><span class="sxs-lookup"><span data-stu-id="00c84-185">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="00c84-186">Ele pode ser encontrado somando os valores de todas as transações.</span><span class="sxs-lookup"><span data-stu-id="00c84-186">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="00c84-187">Modifique a declaração do `Balance` na classe `BankAccount` para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="00c84-187">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="00c84-188">Este exemplo mostra um aspecto importante das ***propriedades***.</span><span class="sxs-lookup"><span data-stu-id="00c84-188">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="00c84-189">Agora, você está calculando o saldo quando outro programador solicita o valor.</span><span class="sxs-lookup"><span data-stu-id="00c84-189">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="00c84-190">Seu cálculo enumera todas as transações e fornece a soma como o saldo atual.</span><span class="sxs-lookup"><span data-stu-id="00c84-190">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="00c84-191">Depois, implemente os métodos `MakeDeposit` e `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="00c84-191">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="00c84-192">Esses métodos aplicarão as duas últimas regras: que o saldo inicial deve ser positivo, e que qualquer saque não pode criar um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="00c84-192">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="00c84-193">Isso introduz o conceito de ***exceções***.</span><span class="sxs-lookup"><span data-stu-id="00c84-193">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="00c84-194">A forma padrão de indicar que um método não pode concluir seu trabalho com êxito é lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="00c84-194">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="00c84-195">O tipo de exceção e a mensagem associada a ele descrevem o erro.</span><span class="sxs-lookup"><span data-stu-id="00c84-195">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="00c84-196">Aqui, o método `MakeDeposit` lançará uma exceção se o valor do depósito for negativo.</span><span class="sxs-lookup"><span data-stu-id="00c84-196">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="00c84-197">O método `MakeWithdrawal` lançará uma exceção se o valor do saque for negativo ou se a aplicação do saque resultar em um saldo negativo:</span><span class="sxs-lookup"><span data-stu-id="00c84-197">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="00c84-198">A instrução [`throw`](../../language-reference/keywords/throw.md) **lança** uma exceção.</span><span class="sxs-lookup"><span data-stu-id="00c84-198">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="00c84-199">A execução do bloco atual é encerrada e o controle transferido para o bloco `catch` da primeira correspondência encontrado na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="00c84-199">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="00c84-200">Você adicionará um bloco `catch` para testar esse código um pouco mais tarde.</span><span class="sxs-lookup"><span data-stu-id="00c84-200">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="00c84-201">O construtor deve receber uma alteração para que adicione uma transação inicial, em vez de atualizar o saldo diretamente.</span><span class="sxs-lookup"><span data-stu-id="00c84-201">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="00c84-202">Como você já escreveu o método `MakeDeposit`, chame-o de seu construtor.</span><span class="sxs-lookup"><span data-stu-id="00c84-202">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="00c84-203">O construtor concluído deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="00c84-203">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="00c84-204"><xref:System.DateTime.Now?displayProperty=nameWithType> é uma propriedade que retorna a data e a hora atuais.</span><span class="sxs-lookup"><span data-stu-id="00c84-204"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="00c84-205">Teste isso adicionando alguns depósitos e saques ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="00c84-205">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="00c84-206">Depois, teste se você recebe condições de erro ao tentar criar uma conta com um saldo negativo:</span><span class="sxs-lookup"><span data-stu-id="00c84-206">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

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

<span data-ttu-id="00c84-207">Use as [instruções `try` e `catch`](../../language-reference/keywords/try-catch.md) para marcar um bloco de código que possa gerar exceções e detectar esses erros esperados.</span><span class="sxs-lookup"><span data-stu-id="00c84-207">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="00c84-208">Use a mesma técnica a fim de testar o código que gera uma exceção para um saldo negativo:</span><span class="sxs-lookup"><span data-stu-id="00c84-208">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

```csharp
// Test for a negative balance:
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

<span data-ttu-id="00c84-209">Salve o arquivo e digite `dotnet run` para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="00c84-209">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="00c84-210">Desafio – registrar em log todas as transações</span><span class="sxs-lookup"><span data-stu-id="00c84-210">Challenge - log all transactions</span></span>

<span data-ttu-id="00c84-211">Para concluir este tutorial, escreva o método `GetAccountHistory` que cria um `string` para o histórico de transações.</span><span class="sxs-lookup"><span data-stu-id="00c84-211">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="00c84-212">Adicione esse método ao tipo `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="00c84-212">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="00c84-213">Isso usa a classe <xref:System.Text.StringBuilder> para formatar uma cadeia de caracteres que contém uma linha para cada transação.</span><span class="sxs-lookup"><span data-stu-id="00c84-213">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="00c84-214">Você viu o código de formatação da cadeia de caracteres anteriormente nesses tutoriais.</span><span class="sxs-lookup"><span data-stu-id="00c84-214">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="00c84-215">Um caractere novo é `\t`.</span><span class="sxs-lookup"><span data-stu-id="00c84-215">One new character is `\t`.</span></span> <span data-ttu-id="00c84-216">Ele insere uma guia para formatar a saída.</span><span class="sxs-lookup"><span data-stu-id="00c84-216">That inserts a tab to format the output.</span></span>

<span data-ttu-id="00c84-217">Adicione esta linha para testá-la no **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="00c84-217">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="00c84-218">Digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="00c84-218">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="00c84-219">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="00c84-219">Next Steps</span></span>

<span data-ttu-id="00c84-220">Se você não conseguir avançar, veja a origem deste tutorial [em nosso repositório GitHub](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="00c84-220">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="00c84-221">Parabéns, você concluiu todos os nossos tutoriais de introdução ao C#.</span><span class="sxs-lookup"><span data-stu-id="00c84-221">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="00c84-222">Se quiser saber mais, temos outros [tutoriais](../index.md) para você experimentar</span><span class="sxs-lookup"><span data-stu-id="00c84-222">If you're eager to learn more, try more of our [tutorials](../index.md)</span></span>
