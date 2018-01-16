---
title: "Inícios rápidos – Introdução às classes – Guia de C#"
description: Crie seu primeiro programa em C# e explore os conceitos de orientado a objeto
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 55d6050d7573b9088b361fb571b96425533bda1f
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="introduction-to-classes"></a><span data-ttu-id="979b2-103">Introdução às classes</span><span class="sxs-lookup"><span data-stu-id="979b2-103">Introduction to classes</span></span>

<span data-ttu-id="979b2-104">Este início rápido espera que você tenha uma máquina que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="979b2-104">This quick start expects that you have a machine you can use for development.</span></span> <span data-ttu-id="979b2-105">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="979b2-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="979b2-106">Confira uma visão geral dos comandos que você usará na [introdução aos inícios rápidos locais](local-environment.md) com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="979b2-106">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="979b2-107">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="979b2-107">Create your application</span></span>

<span data-ttu-id="979b2-108">Usando uma janela de terminal, crie um diretório chamado **classes**.</span><span class="sxs-lookup"><span data-stu-id="979b2-108">Using a terminal window, create a directory named **classes**.</span></span> <span data-ttu-id="979b2-109">Você compilará o aplicativo nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="979b2-109">You'll build your application there.</span></span> <span data-ttu-id="979b2-110">Altere para esse diretório e digite `dotnet new console` na janela do console.</span><span class="sxs-lookup"><span data-stu-id="979b2-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="979b2-111">Esse comando cria o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="979b2-111">This command creates your application.</span></span> <span data-ttu-id="979b2-112">Abra **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="979b2-112">Open **Program.cs**.</span></span> <span data-ttu-id="979b2-113">Ele deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="979b2-113">It should look like this:</span></span>

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

<span data-ttu-id="979b2-114">Neste início rápido, você criará novos tipos que representam uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="979b2-114">In this quick start, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="979b2-115">Normalmente, os desenvolvedores definem cada classe em um arquivo de texto diferente.</span><span class="sxs-lookup"><span data-stu-id="979b2-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="979b2-116">Isso facilita o gerenciamento à medida que o tamanho do programa aumenta.</span><span class="sxs-lookup"><span data-stu-id="979b2-116">That makes it easier to manage as a program grows in size.</span></span>  <span data-ttu-id="979b2-117">Crie um novo arquivo chamado **BankAccount.cs** no diretório **classes**.</span><span class="sxs-lookup"><span data-stu-id="979b2-117">Create a new file named **BankAccount.cs** in the **classes** directory.</span></span> 

<span data-ttu-id="979b2-118">Esse arquivo conterá a definição de uma ***conta bancária***.</span><span class="sxs-lookup"><span data-stu-id="979b2-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="979b2-119">A programação Orientada a Objeto organiza o código por meio da criação de tipos na forma de ***classes***.</span><span class="sxs-lookup"><span data-stu-id="979b2-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="979b2-120">Essas classes contêm o código que representa uma entidade específica.</span><span class="sxs-lookup"><span data-stu-id="979b2-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="979b2-121">A classe `BankAccount` representa uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="979b2-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="979b2-122">O código implementa operações específicas por meio de métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="979b2-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="979b2-123">Nesse início rápido, a conta bancária dá suporte a esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="979b2-123">In this quick start, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="979b2-124">Ela tem um número com 10 dígitos que identifica exclusivamente a conta bancária.</span><span class="sxs-lookup"><span data-stu-id="979b2-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="979b2-125">Ela tem uma cadeia de caracteres que armazena o nome ou os nomes dos proprietários.</span><span class="sxs-lookup"><span data-stu-id="979b2-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="979b2-126">O saldo pode ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="979b2-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="979b2-127">Ela aceita depósitos.</span><span class="sxs-lookup"><span data-stu-id="979b2-127">It accepts deposits.</span></span>
1. <span data-ttu-id="979b2-128">Ele aceita saques.</span><span class="sxs-lookup"><span data-stu-id="979b2-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="979b2-129">O saldo inicial deve ser positivo.</span><span class="sxs-lookup"><span data-stu-id="979b2-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="979b2-130">Os saques não podem resultar em um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="979b2-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="979b2-131">Definir o tipo de conta bancária</span><span class="sxs-lookup"><span data-stu-id="979b2-131">Define the bank account type</span></span>

<span data-ttu-id="979b2-132">Você pode começar criando as noções básicas de uma classe que define esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="979b2-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="979b2-133">Ela deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="979b2-133">It would look like this:</span></span>

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

<span data-ttu-id="979b2-134">Antes de continuar, vamos dar uma olhada no que você compilou.</span><span class="sxs-lookup"><span data-stu-id="979b2-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="979b2-135">A declaração `namespace` fornece uma maneira de organizar logicamente seu código.</span><span class="sxs-lookup"><span data-stu-id="979b2-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="979b2-136">Esse início rápido é relativamente pequeno, portanto, você colocará todo o código em um namespace.</span><span class="sxs-lookup"><span data-stu-id="979b2-136">This quick start is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="979b2-137">`public class BankAccount` define a classe ou o tipo que você está criando.</span><span class="sxs-lookup"><span data-stu-id="979b2-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="979b2-138">Tudo dentro de `{` e `}` logo após a declaração da classe define o comportamento da classe.</span><span class="sxs-lookup"><span data-stu-id="979b2-138">Everything inside the `{` and `}` that follows the class declaration defines the behavior of the class.</span></span> <span data-ttu-id="979b2-139">Há cinco ***membros*** na classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="979b2-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="979b2-140">As três primeiras são ***propriedades***.</span><span class="sxs-lookup"><span data-stu-id="979b2-140">The first three are ***properties***.</span></span> <span data-ttu-id="979b2-141">Propriedades são elementos de dados que podem ter um código que impõe a validação ou outras regras.</span><span class="sxs-lookup"><span data-stu-id="979b2-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="979b2-142">Os últimos dois são ***métodos***.</span><span class="sxs-lookup"><span data-stu-id="979b2-142">The last two are ***methods***.</span></span> <span data-ttu-id="979b2-143">Métodos são blocos de código que executam uma única função.</span><span class="sxs-lookup"><span data-stu-id="979b2-143">Methods are blocks of code that peform a single function.</span></span> <span data-ttu-id="979b2-144">A leitura dos nomes de cada um dos membros deve fornecer informações suficientes para você, ou outro desenvolvedor, entender o que a classe faz.</span><span class="sxs-lookup"><span data-stu-id="979b2-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="979b2-145">Abrir uma nova conta</span><span class="sxs-lookup"><span data-stu-id="979b2-145">Open a new account</span></span>

<span data-ttu-id="979b2-146">O primeiro recurso a ser implementado serve para abrir uma conta bancária.</span><span class="sxs-lookup"><span data-stu-id="979b2-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="979b2-147">Quando um cliente abre uma conta, ele deve fornecer um saldo inicial e informações sobre o proprietário, ou proprietários, dessa conta.</span><span class="sxs-lookup"><span data-stu-id="979b2-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="979b2-148">A criação de novo objeto do tipo `BankAccount` significa a definição de um ***construtor*** que atribui esses valores.</span><span class="sxs-lookup"><span data-stu-id="979b2-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="979b2-149">Um ***construtor*** é um membro que tem o mesmo nome da classe.</span><span class="sxs-lookup"><span data-stu-id="979b2-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="979b2-150">Ele é usado para inicializar objetos desse tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="979b2-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="979b2-151">Adicione o seguinte construtor ao tipo `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="979b2-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="979b2-152">Construtores são chamados quando você cria um objeto usando [`new`](../language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="979b2-152">Constructors are called when you create an object using [`new`](../language-reference/keywords/new.md).</span></span> <span data-ttu-id="979b2-153">Substitua a linha `Console.WriteLine("Hello World!");` no arquivo ***program.cs*** pela seguinte linha (substitua `<name>` pelo seu nome):</span><span class="sxs-lookup"><span data-stu-id="979b2-153">Replace the line `Console.WriteLine("Hello World!");` in ***program.cs*** with the following line (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="979b2-154">Digite `dotnet run` para ver o que acontece.</span><span class="sxs-lookup"><span data-stu-id="979b2-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="979b2-155">Você notou que o número da conta está em branco?</span><span class="sxs-lookup"><span data-stu-id="979b2-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="979b2-156">É hora de corrigir isso.</span><span class="sxs-lookup"><span data-stu-id="979b2-156">It's time to fix that.</span></span> <span data-ttu-id="979b2-157">O número da conta deve ser atribuído na construção do objeto.</span><span class="sxs-lookup"><span data-stu-id="979b2-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="979b2-158">Mas não é responsabilidade do chamador criá-lo.</span><span class="sxs-lookup"><span data-stu-id="979b2-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="979b2-159">O código da classe `BankAccount` deve saber como atribuir novos números de conta.</span><span class="sxs-lookup"><span data-stu-id="979b2-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="979b2-160">Uma maneira simples de fazer isso é começar com um número de 10 dígitos.</span><span class="sxs-lookup"><span data-stu-id="979b2-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="979b2-161">Incremente-o à medida que novas contas são criadas.</span><span class="sxs-lookup"><span data-stu-id="979b2-161">Increment it when each new account is created.</span></span> <span data-ttu-id="979b2-162">Por fim, armazene o número da conta atual quando um objeto for construído.</span><span class="sxs-lookup"><span data-stu-id="979b2-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="979b2-163">Adicione a seguinte declaração de membro à classe `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="979b2-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="979b2-164">Este é um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="979b2-164">This is a data member.</span></span> <span data-ttu-id="979b2-165">Ele é `private`, o que significa que ele só pode ser acessado pelo código dentro da classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="979b2-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="979b2-166">É uma maneira de separar as responsabilidades públicas (como ter um número de conta) da implementação privada (como os números de conta são gerados.) Adicione as duas linhas a seguir ao construtor para atribuir o número da conta:</span><span class="sxs-lookup"><span data-stu-id="979b2-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated.) Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="979b2-167">Digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="979b2-167">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="979b2-168">Criar depósitos e saques</span><span class="sxs-lookup"><span data-stu-id="979b2-168">Create deposits and withdrawals</span></span>

<span data-ttu-id="979b2-169">A classe da conta bancária precisa aceitar depósitos e saques para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="979b2-169">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="979b2-170">Vamos implementar depósitos e saques criando um diário de todas as transações da conta.</span><span class="sxs-lookup"><span data-stu-id="979b2-170">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="979b2-171">Isso apresenta algumas vantagens em comparação à simples atualização do saldo em cada transação.</span><span class="sxs-lookup"><span data-stu-id="979b2-171">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="979b2-172">O histórico pode ser usado para auditar todas as transações e gerenciar os saldos diários.</span><span class="sxs-lookup"><span data-stu-id="979b2-172">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="979b2-173">Ao calcular o saldo do histórico de todas as transações, quando for necessário, todos os erros corrigidos em uma única transação serão refletidos corretamente no saldo no próximo cálculo.</span><span class="sxs-lookup"><span data-stu-id="979b2-173">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="979b2-174">Vamos começar criando um novo tipo para representar uma transação.</span><span class="sxs-lookup"><span data-stu-id="979b2-174">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="979b2-175">É um tipo simples que não tem qualquer responsabilidade.</span><span class="sxs-lookup"><span data-stu-id="979b2-175">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="979b2-176">Ele precisa de algumas propriedades.</span><span class="sxs-lookup"><span data-stu-id="979b2-176">It needs a few properties.</span></span> <span data-ttu-id="979b2-177">Crie um novo arquivo chamado ***Transaction.cs***.</span><span class="sxs-lookup"><span data-stu-id="979b2-177">Create a new file named ***Transaction.cs***.</span></span> <span data-ttu-id="979b2-178">Adicione o seguinte código a ele:</span><span class="sxs-lookup"><span data-stu-id="979b2-178">Add the following code to it:</span></span>

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

<span data-ttu-id="979b2-179">Agora, vamos adicionar um <xref:System.Collections.Generic.List%601> de `Transaction` objetos à classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="979b2-179">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="979b2-180">Adicione a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="979b2-180">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<span data-ttu-id="979b2-181">A classe <xref:System.Collections.Generic.List%601> exige que você importe um namespace diferente.</span><span class="sxs-lookup"><span data-stu-id="979b2-181">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="979b2-182">Adicione o seguinte no início de **BankAccount.cs**:</span><span class="sxs-lookup"><span data-stu-id="979b2-182">Add the following at the beginning of **BankAccount.cs**:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="979b2-183">Agora, vamos alterar como `Balance` é reportado.</span><span class="sxs-lookup"><span data-stu-id="979b2-183">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="979b2-184">Ele pode ser encontrado somando os valores de todas as transações.</span><span class="sxs-lookup"><span data-stu-id="979b2-184">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="979b2-185">Modifique a declaração do `Balance` na classe `BankAccount` para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="979b2-185">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

<span data-ttu-id="979b2-186">Este exemplo mostra um aspecto importante das ***propriedades***.</span><span class="sxs-lookup"><span data-stu-id="979b2-186">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="979b2-187">Agora, você está calculando o saldo quando outro programador solicita o valor.</span><span class="sxs-lookup"><span data-stu-id="979b2-187">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="979b2-188">Seu cálculo enumera todas as transações e fornece a soma como o saldo atual.</span><span class="sxs-lookup"><span data-stu-id="979b2-188">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="979b2-189">Depois, implemente os métodos `MakeDeposit` e `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="979b2-189">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="979b2-190">Esses métodos aplicarão as duas últimas regras: que o saldo inicial deve ser positivo, e que qualquer saque não pode criar um saldo negativo.</span><span class="sxs-lookup"><span data-stu-id="979b2-190">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="979b2-191">Isso introduz o conceito de ***exceções***.</span><span class="sxs-lookup"><span data-stu-id="979b2-191">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="979b2-192">A forma padrão de indicar que um método não pode concluir seu trabalho com êxito é lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="979b2-192">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="979b2-193">O tipo de exceção e a mensagem associada a ele descrevem o erro.</span><span class="sxs-lookup"><span data-stu-id="979b2-193">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="979b2-194">Aqui, o método `MakeDeposit` lançará uma exceção se o valor do depósito for negativo.</span><span class="sxs-lookup"><span data-stu-id="979b2-194">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="979b2-195">O método `MakeWithdrawal` lançará uma exceção se o valor do saque for negativo ou se a aplicação do saque resultar em um saldo negativo:</span><span class="sxs-lookup"><span data-stu-id="979b2-195">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

<span data-ttu-id="979b2-196">A instrução [`throw`](../language-reference/keywords/throw.md) **lança** uma exceção.</span><span class="sxs-lookup"><span data-stu-id="979b2-196">The [`throw`](../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="979b2-197">A execução do método atual termina e será retomada quando encontrar uma correspondência do bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="979b2-197">Execution of the current method ends, and will resume when a matching `catch` block is found.</span></span> <span data-ttu-id="979b2-198">Você adicionará um bloco `catch` para testar esse código um pouco mais tarde.</span><span class="sxs-lookup"><span data-stu-id="979b2-198">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="979b2-199">O construtor deve receber uma alteração para que adicione uma transação inicial, em vez de atualizar o saldo diretamente.</span><span class="sxs-lookup"><span data-stu-id="979b2-199">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="979b2-200">Como você já escreveu o método `MakeDeposit`, chame-o de seu construtor.</span><span class="sxs-lookup"><span data-stu-id="979b2-200">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="979b2-201">O construtor concluído deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="979b2-201">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<span data-ttu-id="979b2-202"><xref:System.DateTime.Now?displayProperty=nameWithType> é uma propriedade que retorna a data e a hora atuais.</span><span class="sxs-lookup"><span data-stu-id="979b2-202"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="979b2-203">Teste isso adicionando alguns depósitos e saques ao método `Main`:</span><span class="sxs-lookup"><span data-stu-id="979b2-203">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="979b2-204">Depois, teste se você recebe condições de erro ao tentar criar uma conta com um saldo negativo:</span><span class="sxs-lookup"><span data-stu-id="979b2-204">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

```csharp
// Test that the initial balances must be positive:
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

<span data-ttu-id="979b2-205">Use as [instruções `try` e `catch`](../language-reference/keywords/try-catch.md) para marcar um bloco de código que pode gerar exceções, e para detectar esses erros esperados.</span><span class="sxs-lookup"><span data-stu-id="979b2-205">You use the [`try` and `catch` statements](../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions, and to catch those errors that you expect.</span></span> <span data-ttu-id="979b2-206">Use a mesma técnica para testar o código lançado por um saldo negativo:</span><span class="sxs-lookup"><span data-stu-id="979b2-206">You can use the same technique to test the code that throws for a negative balance:</span></span>

```csharp
// Test for a negative balance
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

<span data-ttu-id="979b2-207">Salve o arquivo e digite `dotnet run` para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="979b2-207">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="979b2-208">Desafio – registrar em log todas as transações</span><span class="sxs-lookup"><span data-stu-id="979b2-208">Challenge - log all transactions</span></span>

<span data-ttu-id="979b2-209">Para concluir este início rápido, você pode escrever o método `GetAccountHistory` que cria um `string` para o histórico de transações.</span><span class="sxs-lookup"><span data-stu-id="979b2-209">To finish this quick start, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="979b2-210">adicione esse método ao tipo `BankAccount`:</span><span class="sxs-lookup"><span data-stu-id="979b2-210">add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

<span data-ttu-id="979b2-211">Isso usa a classe <xref:System.Text.StringBuilder> para formatar uma cadeia de caracteres que contém uma linha para cada transação.</span><span class="sxs-lookup"><span data-stu-id="979b2-211">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="979b2-212">Você viu o código de formatação da cadeia de caracteres anteriormente nesses inícios rápidos.</span><span class="sxs-lookup"><span data-stu-id="979b2-212">You've seen the string formatting code earlier in these quick starts.</span></span> <span data-ttu-id="979b2-213">Um caractere novo é `\t`.</span><span class="sxs-lookup"><span data-stu-id="979b2-213">One new character is `\t`.</span></span> <span data-ttu-id="979b2-214">Ele insere uma guia para formatar a saída.</span><span class="sxs-lookup"><span data-stu-id="979b2-214">That inserts a tab to format the output.</span></span>

<span data-ttu-id="979b2-215">Adicione esta linha para testá-la no **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="979b2-215">Add this line to test it in **Program.cs**:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="979b2-216">Digite `dotnet run` para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="979b2-216">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="979b2-217">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="979b2-217">Next Steps</span></span>

<span data-ttu-id="979b2-218">Se você não conseguir avançar, veja a origem deste início rápido [em nosso repositório do GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span><span class="sxs-lookup"><span data-stu-id="979b2-218">If you got stuck, you can see the source for this quick start [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)</span></span>

<span data-ttu-id="979b2-219">Parabéns, você concluiu todos os nossos Inícios Rápido.</span><span class="sxs-lookup"><span data-stu-id="979b2-219">Congratulations, you've finished all our Quick Starts.</span></span> <span data-ttu-id="979b2-220">Se você quiser saber mais, experimente nossos [tutoriais](../tutorials/index.md)</span><span class="sxs-lookup"><span data-stu-id="979b2-220">If you're eager to learn more, try our [tutorials](../tutorials/index.md)</span></span>
