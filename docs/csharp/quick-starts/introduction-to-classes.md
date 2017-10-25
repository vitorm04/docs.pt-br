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
ms.openlocfilehash: c2b267562f78b359d5ceaa696ff9a9bdcffa5821
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-classes"></a>Introdução às classes

Esta lição pressupõe que você instalou o [SDK do .NET Core](http://dot.net/core) e um editor de sua escolha. Se você não tiver um, experimente o [Visual Studio Code](https://code.visualstudio.com/) ou o [Visual Studio](https://www.visualstudio.com/) no Mac ou Windows.

## <a name="create-your-application"></a>Criar seu aplicativo

Usando uma janela de terminal, crie um diretório chamado **classes**. Você compilará o aplicativo nesse diretório. Altere para esse diretório e digite `dotnet new console` na janela do console. Esse comando cria o aplicativo. Abra **Program.cs**. Ele deve ter esta aparência:

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

Neste início rápido, você criará novos tipos que representam uma conta bancária. Normalmente, os desenvolvedores definem cada classe em um arquivo de texto diferente. Isso facilita o gerenciamento à medida que o tamanho do programa aumenta.  Crie um novo arquivo chamado **BankAccount.cs** no diretório **classes**. 

Esse arquivo conterá a definição de uma ***conta bancária***. A programação Orientada a Objeto organiza o código por meio da criação de tipos na forma de ***classes***. Essas classes contêm o código que representa uma entidade específica. A classe `BankAccount` representa uma conta bancária. O código implementa operações específicas por meio de métodos e propriedades. Nesse início rápido, a conta bancária dá suporte a esse comportamento:

1. Ela tem um número com 10 dígitos que identifica exclusivamente a conta bancária.
1. Ela tem uma cadeia de caracteres que armazena o nome ou os nomes dos proprietários.
1. O saldo pode ser recuperado.
1. Ela aceita depósitos.
1. Ele aceita saques.
1. O saldo inicial deve ser positivo.
1. Os saques não podem resultar em um saldo negativo.

## <a name="define-the-bank-account-type"></a>Definir o tipo de conta bancária

Você pode começar criando as noções básicas de uma classe que define esse comportamento. Ela deve ter esta aparência:

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

        public void MakeWithdrawal(decimal amount, DateTime date, string payee, string note)
        {
        }
    }
}
```

Antes de continuar, vamos dar uma olhada no que você compilou.  A declaração `namespace` fornece uma maneira de organizar logicamente seu código. Esse início rápido é relativamente pequeno, portanto, você colocará todo o código em um namespace. 

`public class BankAccount` define a classe ou o tipo que você está criando. Tudo dentro de `{` e `}` logo após a declaração da classe define o comportamento da classe. Há cinco ***membros*** na classe `BankAccount`. As três primeiras são ***propriedades***. Propriedades são elementos de dados que podem ter um código que impõe a validação ou outras regras. Os últimos dois são ***métodos***. Métodos são blocos de código que executam uma única função. A leitura dos nomes de cada um dos membros deve fornecer informações suficientes para você, ou outro desenvolvedor, entender o que a classe faz.

## <a name="open-a-new-account"></a>Abrir uma nova conta

O primeiro recurso a ser implementado serve para abrir uma conta bancária. Quando um cliente abre uma conta, ele deve fornecer um saldo inicial e informações sobre o proprietário, ou proprietários, dessa conta. 

A criação de novo objeto do tipo `BankAccount` significa a definição de um ***construtor*** que atribui esses valores. Um ***construtor*** é um membro que tem o mesmo nome da classe. Ele é usado para inicializar objetos desse tipo de classe. Adicione o seguinte construtor ao tipo `BankAccount`:

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Construtores são chamados quando você cria um objeto usando [`new`](../language-reference/keywords/new.md). Substitua a linha `Console.WriteLine("Hello World!");` no arquivo ***program.cs*** pela seguinte linha (substitua `<name>` pelo seu nome):

```csharp
var account = new BankAccount("<name", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance".);
```

Digite `dotnet run` para ver o que acontece.  

Você notou que o número da conta está em branco? É hora de corrigir isso. O número da conta deve ser atribuído na construção do objeto. Mas não é responsabilidade do chamador criá-lo. O código da classe `BankAccount` deve saber como atribuir novos números de conta.  Uma maneira simples de fazer isso é começar com um número de 10 dígitos. Incremente-o à medida que novas contas são criadas. Por fim, armazene o número da conta atual quando um objeto for construído.

Adicione a seguinte declaração de membro à classe `BankAccount`:

```csharp
private static int accountNumberSeed = 1234567890;
```

Este é um membro de dados. Ele é `private`, o que significa que ele só pode ser acessado pelo código dentro da classe `BankAccount`. É uma maneira de separar as responsabilidades públicas (como ter um número de conta) da implementação privada (como os números de conta são gerados.) Adicione as duas linhas a seguir ao construtor para atribuir o número da conta:

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Digite `dotnet run` para ver os resultados.

## <a name="create-deposits-and-withdrawals"></a>Criar depósitos e saques

A classe da conta bancária precisa aceitar depósitos e saques para funcionar corretamente. Vamos implementar depósitos e saques criando um diário de todas as transações da conta. Isso apresenta algumas vantagens em comparação à simples atualização do saldo em cada transação. O histórico pode ser usado para auditar todas as transações e gerenciar os saldos diários. Ao calcular o saldo do histórico de todas as transações, quando for necessário, todos os erros corrigidos em uma única transação serão refletidos corretamente no saldo no próximo cálculo.

Vamos começar criando um novo tipo para representar uma transação. É um tipo simples que não tem qualquer responsabilidade. Ele precisa de algumas propriedades. Crie um novo arquivo chamado ***Transaction.cs***. Adicione o seguinte código a ele:

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

Agora, vamos adicionar um <xref:System.Collections.Generic.List%601> de `Transaction` objetos à classe `BankAccount`. Adicione a seguinte declaração:

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

A classe <xref:System.Collections.Generic.List%601> exige que você importe um namespace diferente. Adicione o seguinte no início de **BankAccount.cs**:

```csharp
using System.Collections.Generic;
```

Agora, vamos alterar como `Balance` é reportado.  Ele pode ser encontrado somando os valores de todas as transações. Modifique a declaração do `Balance` na classe `BankAccount` para o seguinte:

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

Este exemplo mostra um aspecto importante das ***propriedades***. Agora, você está calculando o saldo quando outro programador solicita o valor. Seu cálculo enumera todas as transações e fornece a soma como o saldo atual.

Depois, implemente os métodos `MakeDeposit` e `MakeWithdrawal`. Esses métodos aplicarão as duas últimas regras: que o saldo inicial deve ser positivo, e que qualquer saque não pode criar um saldo negativo. 

Isso introduz o conceito de ***exceções***. A forma padrão de indicar que um método não pode concluir seu trabalho com êxito é lançar uma exceção. O tipo de exceção e a mensagem associada a ele descrevem o erro. Aqui, o método `MakeDeposit` lançará uma exceção se o valor do depósito for negativo. O método `MakeWithdrawal` lançará uma exceção se o valor do saque for negativo ou se a aplicação do saque resultar em um saldo negativo:

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

A instrução [`throw`](../language-reference/throw.md) **lança** uma exceção. A execução do método atual termina e será retomada quando encontrar uma correspondência do bloco `catch`. Você adicionará um bloco `catch` para testar esse código um pouco mais tarde.

O construtor deve receber uma alteração para que adicione uma transação inicial, em vez de atualizar o saldo diretamente. Como você já escreveu o método `MakeDeposit`, chame-o de seu construtor. O construtor concluído deve ter esta aparência:

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> é uma propriedade que retorna a data e a hora atuais. Teste isso adicionando alguns depósitos e saques ao método `Main`:

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

Depois, teste se você recebe condições de erro ao tentar criar uma conta com um saldo negativo:

```csharp
// Test that the initial balances must be positive:
try {
    var invalidAccount = new BankAccount("invalid", -55);
} catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

Use as [instruções `try` e `catch`](../language-reference/keywords/try-catch.md) para marcar um bloco de código que pode gerar exceções, e para detectar esses erros esperados. Use a mesma técnica para testar o código lançado por um saldo negativo:

```csharp
// Test for a negative balance
try {
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
} catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

Salve o arquivo e digite `dotnet run` para testá-lo.

## <a name="challenge---log-all-transactions"></a>Desafio – registrar em log todas as transações

Para concluir este início rápido, você pode escrever o método `GetAccountHistory` que cria um `string` para o histórico de transações. adicione esse método ao tipo `BankAccount`:

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

Isso usa a classe <xref:System.Text.StringBuilder> para formatar uma cadeia de caracteres que contém uma linha para cada transação. Você viu o código de formatação da cadeia de caracteres anteriormente nesses inícios rápidos. Um caractere novo é `\t`. Ele insere uma guia para formatar a saída.

Adicione esta linha para testá-la no **Program.cs**:

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Digite `dotnet run` para ver os resultados.

## <a name="next-steps"></a>Próximas etapas

Se você não conseguir avançar, veja a origem deste início rápido [em nosso repositório do GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/)

Parabéns, você concluiu todos os nossos Inícios Rápido. Se você quiser saber mais, experimente nossos [tutoriais](../tutorials/index.md)