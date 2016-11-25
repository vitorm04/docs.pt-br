---
title: "Tratando e gerando exceções no .NET"
description: "Entenda como usar exceções no .NET"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf116df6-0042-46bf-be13-b69864816210
translationtype: Human Translation
ms.sourcegitcommit: 9584699ad7e745ae3cb059b1bb8327301c9a3286
ms.openlocfilehash: 5271b63a47aa2fcc81cd9c8b1ffd22e618829412

---

# <a name="handling-and-throwing-exceptions-in-net"></a>Tratando e gerando exceções no .NET

Aplicativos devem ser capazes de tratar de erros que ocorrem durante a execução de uma maneira consistente. O .NET fornece um modelo para notificar aplicativos sobre erros de maneira uniforme: operações do .NET indicam falhas por meio da geração de exceções.

## <a name="exceptions"></a>Exceções

Uma exceção é qualquer condição de erro ou comportamento inesperado encontrado por um programa em execução. Exceções podem ser geradas devido a uma falha em seu código ou no código que você chama (como uma biblioteca compartilhada), recursos do sistema operacional não disponíveis, condições inesperadas encontradas pelo tempo de execução (como código que não pode ser verificado) e assim por diante. Seu aplicativo pode se recuperar de algumas dessas condições, mas não de outras. Embora você possa se recuperar da maioria das exceções de aplicativo, não é possível recuperar-se da maioria das exceções de tempo de execução.

No .NET, uma exceção é um objeto que herda da classe [System.Exception](xref:System.Exception). Uma exceção é lançada de uma área do código em que ocorreu um problema. A exceção é passada pilha acima até que o aplicativo trate dela ou o programa seja encerrado.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Métodos de tratamento de exceção vs. tratamento de erro tradicional

Tradicionalmente, o modelo de tratamento de erro da linguagem confiava na forma exclusiva da linguagem de detectar erros e localizar manipuladores para eles ou no mecanismo de tratamento de erro fornecido pelo sistema operacional. A maneira como o .NET implementa o tratamento de exceção oferece as seguintes vantagens:

- O lançamento e tratamento de exceção funciona da mesma maneira para linguagens de programação .NET.

- Não requer nenhuma sintaxe de linguagem específica para tratamento de exceção, mas permite que cada linguagem defina sua própria sintaxe.

- Exceções podem ser geradas pelos limites de processo e até mesmo de computador.

- O código de tratamento de exceção pode ser adicionado a um aplicativo para aumentar a confiabilidade do programa.

As exceções oferecem vantagens sobre outros métodos de notificação de erro, como códigos de retorno. Falhas não passam despercebidas porque se uma exceção for lançada e você não tratar dela, o tempo de execução encerra o aplicativo. Valores inválidos não continuam a se propagar através do sistema como resultado do código que não consegue verificar se há um código de retorno de falha. 

## <a name="exception-class-and-properties"></a>Classe e propriedades da exceção

A classe @System.Exception é a classe base da qual as exceções herdam. Por exemplo, a hierarquia de classe @System.InvalidCastException é como se segue:

```
Object
  Exception
    SystemException
       InvalidCastException
```

A classe @System.Exception tem as propriedades a seguir, que ajudam a facilitar o entendimento de uma exceção.

| Nome da Propriedade | Descrição |
| ------------- | ----------- |
| @System.Exception.Data | Um @System.Collections.IDictionary que contém dados arbitrários em pares chave-valor. |
| @System.Exception.HelpLink | Pode conter uma URL (ou URN) para um arquivo de ajuda que fornece informações abrangentes sobre a causa de uma exceção. |
| @System.Exception.InnerException | Essa propriedade pode ser usada para criar e manter uma série de exceções durante o tratamento de exceção. Você pode usá-lo para criar uma nova exceção contendo exceções previamente capturadas. A exceção original pode ser capturada pela segunda exceção na propriedade @System.Exception.InnerException, permitindo que o código que trata da segunda exceção examine as informações adicionais. Por exemplo, suponha que você tem um método que recebe um argumento que está formatado de modo inadequado.  O código tenta ler o argumento, mas uma exceção é gerada. O método captura a exceção e gera um @System.FormatException. Para melhorar a capacidade do chamador a fim de determinar o motivo pelo qual uma exceção é gerada, às vezes é desejável que um método capture uma exceção gerada por uma rotina auxiliar e, em seguida, gere uma exceção mais indicativa do erro que ocorreu. Uma exceção mais nova e mais significativa pode ser criada, na qual a referência à exceção interna pode ser definida para a exceção original. Essa exceção mais significativa pode, em seguida, ser gerada para o chamador. Observe que com essa funcionalidade você pode criar uma série de exceções vinculadas que termina com a primeira exceção gerada. |
| @System.Exception.Message | Fornece detalhes sobre a causa de uma exceção.
| @System.Exception.Source | Obtém ou define o nome do aplicativo ou objeto que causa o erro. |
| @System.Exception.StackTrace | Contém um rastreamento de pilha que pode ser usado para determinar onde um erro ocorreu. O rastreamento de pilha inclui o nome do arquivo de origem e o número de linha de programa se informações de depuração estiverem disponíveis. |

A maioria das classes que herdam de @System.Exception não implementam membros adicionais ou fornecem funcionalidade adicional; elas simplesmente herdam de @System.Exception. Portanto, as informações mais importantes para uma exceção podem ser encontradas na hierarquia de classes de exceção, no nome da exceção e nas informações contidas na exceção.

É recomendável gerar e capturar apenas objetos que derivam de @System.Exception,, mas é possível gerar como uma exceção qualquer objeto que derive da classe @System.Object. Observe que nem todas as linguagens dão suporte à geração e captura de objetos que não derivam de @System.Exception.

## <a name="common-exceptions"></a>Exceções comuns

A tabela a seguir lista algumas exceções comuns com exemplos do que pode causá-las.

| Tipo de exceção | Tipo base | Descrição | Exemplo |
| -------------- | --------- | ----------- | ------- |
| @System.Exception | @System.Object | A classe base para todas as exceções. | Nenhuma (use uma classe derivada dessa exceção). |
| @System.IndexOutOfRangeException | @System.Exception | Gerada pelo tempo de execução somente quando uma matriz é indexada incorretamente. | Indexar uma matriz fora do intervalo válido: `arr[arr.Length+1]` |
| @System.NullReferenceException | @System.Exception | Gerada pelo tempo de execução somente quando um objeto nulo é referenciado. | `object o = null; o.ToString();` |
| @System.InvalidOperationException | @System.Exception | Gerada por métodos quando em um estado inválido. | Chamar `Enumerator.GetNext()` após a remoção de um item da coleção subjacente. |
| @System.ArgumentException | @System.Exception | A classe base para todas as exceções de argumento. | Nenhuma (use uma classe derivada dessa exceção). |
| @System.ArgumentNullException | @System.Exception | Gerada por métodos que não permitem que um argumento seja nulo. | `String s = null; "Calculate".IndexOf (s);` |
| @System.ArgumentOutOfRangeException | @System.Exception | Gerada por métodos que verificam se os argumentos estão em um determinado intervalo. | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Como usar o bloco try/catch para capturar exceções

Coloque as seções do código que podem gerar exceções em um bloco `try` e coloque o código que trata de exceções em um bloco `catch`. O bloco `catch` é uma série de instruções que começam com a palavra-chave `catch`, seguido por um tipo de exceção e uma ação a ser tomada.

O exemplo de código a seguir usa um bloco `try`/`catch` para capturar uma possível exceção. O método `Main` contém um bloco `try` com uma instrução @System.IO.StreamReader que abre um arquivo de dados chamado `data.txt` e grava uma cadeia de caracteres do arquivo. Após o bloco `try` há um bloco `catch`, que captura qualquer exceção resultante do bloco `try`.

C#
```
using System;
using System.IO;

public class ProcessFile
{
    public static void Main()
    {
        try
        {
            StreamReader sr = File.OpenText("data.txt");
            Console.WriteLine("The first line of this file is {0}", sr.ReadLine());
            sr.Dispose();
        }
        catch (Exception e)
        {
            Console.WriteLine("An error occurred: '{0}'", e);
        }
    }
}
```

O Common Language Runtime captura exceções que não são capturadas por um bloco catch. Dependendo de como o tempo de execução estiver configurado, uma caixa de diálogo de depuração será exibida ou o programa interromperá a execução e será exibida uma caixa de diálogo com as informações de exceção ou, ainda, um erro será impresso para stderr.

> [!NOTE] 
> Quase qualquer linha de código pode causar uma exceção, especialmente exceções geradas pelo Common Language Runtime em si, como @System.OutOfMemoryException. A maioria dos aplicativos não precisa lidar com essas exceções, mas você deve estar ciente dessa possibilidade ao gravar bibliotecas para serem usadas por outros. Para obter sugestões sobre quando definir código em um bloco Try, veja [Práticas recomendadas para exceções](#best-practices-for-exceptions).
 
## <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Como usar exceções específicas em um bloco Catch

O exemplo de código anterior ilustra uma instrução básica `catch` que captura qualquer exceção. Em geral, no entanto, é uma boa prática capturar um tipo específico de exceção em vez de usar a instrução básica `catch`.

Quando ocorre uma exceção, ela é passada para cima na pilha e, a cada bloco catch, é dada a oportunidade de tratá-la. A ordem das instruções catch é importante. Coloque blocos catch direcionados para exceções específicas antes que um bloco catch de exceção geral ou o compilador possa emitir um erro. O bloco catch adequado é determinado ao fazer a correspondência entre o tipo da exceção e o nome da exceção especificada no bloco catch. Se não houver nenhum bloco catch específico, a exceção será detectada por um bloco catch geral, se houver.

O seguinte exemplo de código usa um bloco `try`/`catch` para capturar uma @System.InvalidCastException. O exemplo cria uma classe chamada `Employee` com uma única propriedade, nível do funcionário (`Emlevel`). Um método, `PromoteEmployee`, utiliza um objeto e incrementa o nível do funcionário. Um @System.InvalidCastException ocorre quando uma instância @System.DateTime é passada para o método `PromoteEmployee`.

C#
```
using System;

public class Employee
{
    //Create employee level property.
    public int Emlevel
    {
        get
        {
            return(emlevel);
        }
        set
        {
            emlevel = value;
        }
    }

    private int emlevel = 0;
}

public class Ex13
{
    public static void PromoteEmployee(Object emp)
    {
        //Cast object to Employee.
        Employee e = (Employee) emp;
        // Increment employee level.
        e.Emlevel = e.Emlevel + 1;
    }

    public static void Main()
    {
        try
        {
            Object o = new Employee();
            DateTime newyears = new DateTime(2001, 1, 1);
            //Promote the new employee.
            PromoteEmployee(o);
            //Promote DateTime; results in InvalidCastException as newyears is not an employee instance.
            PromoteEmployee(newyears);
        }
        catch (InvalidCastException e)
        {
            Console.WriteLine("Error passing data to PromoteEmployee method. " + e.Message);
        }
    }
}
```

## <a name="how-to-use-finally-blocks"></a>Como usar blocos finally

Quando ocorre uma exceção, a execução é interrompida e o controle é dado ao manipulador de exceção apropriado. Geralmente, isso significa que linhas de código que você espera que sejam executadas são ignoradas. A limpeza de alguns recursos, assim como o fechamento de um arquivo, precisará ser feita mesmo se uma exceção for gerada. Para fazer isso, você pode usar um bloco `finally`. Um bloco `finally` sempre é executado, independentemente de uma exceção ser ou não gerada.

O seguinte exemplo de código usa um bloco `try`/`catch` para capturar uma @System.ArgumentOutOfRangeException. O método `Main` cria duas matrizes e tenta copiar uma para a outra. A ação gera um @System.ArgumentOutOfRangeException e o erro é gravado no console. Este bloco `finally` é executado independentemente resultado da ação de cópia.

C#
```
using System;

class ArgumentOutOfRangeExample
{
    public static void Main()
    {
        int[] array1 = {0, 0};
        int[] array2 = {0, 0};

        try
        {
            Array.Copy(array1, array2, -1);
        }
        catch (ArgumentOutOfRangeException e)
        {
            Console.WriteLine("Error: {0}", e);
        }
        finally
        {
            Console.WriteLine("This statement is always executed.");
        }
    }
}
```

## <a name="how-to-explicitly-throw-exceptions"></a>Como gerar exceções explicitamente

Você pode gerar uma exceção explicitamente usando a instrução `throw`. Você também pode lançar novamente uma exceção capturada usando a instrução `throw`. É uma boa prática adicionar informações a uma exceção que é lançada novamente para fornecer mais informações durante a depuração.

O seguinte exemplo usa um bloco `try`/`catch` para capturar um possível @System.IO.FileNotFoundException. Após o bloco `try`, há um bloco `catch` que captura a @System.IO.FileNotFoundException e grava uma mensagem no console se o arquivo de dados não for encontrado. A próxima instrução é a instrução `throw`, que gera uma nova @System.IO.FileNotFoundException e adiciona informações de texto à exceção.

C#
```
using System;
using System.IO;

public class ProcessFile
{
   public static void Main()
      {
      FileStream fs = null;
      try   
      {
         //Opens a text tile.
         fs = new FileStream(@"C:\temp\data.txt", FileMode.Open);
         StreamReader sr = new StreamReader(fs);
         string line;

         //A value is read from the file and output to the console.
         line = sr.ReadLine();
         Console.WriteLine(line);
      }
      catch(FileNotFoundException e)
      {
         Console.WriteLine("[Data File Missing] {0}", e);
         throw new FileNotFoundException(@"[data.txt not in c:\temp directory]",e);
      }
      finally
      {
         if (fs != null)
            fs.Dispose();
      }
   }
}
```

## <a name="how-to-create-user-defined-exceptions"></a>Como criar exceções definidas pelo usuário

O .NET fornece uma hierarquia de classes de exceção derivada da classe base @System.Exception. No entanto, se nenhuma das exceções predefinidas atender às suas necessidades, é possível criar suas próprias classes de exceção derivando da classe @System.Exception.

Ao criar suas próprias exceções, encerre o nome de classe de exceção definida pelo usuário com a palavra "Exception" e implemente os três construtores comuns, como mostrado no exemplo a seguir. O exemplo define uma nova classe de exceção chamada `EmployeeListNotFoundException`. A classe é derivada de @System.Exception e inclui três construtores.

C#
```
using System;

public class EmployeeListNotFoundException: Exception
{
    public EmployeeListNotFoundException()
    {
    }

    public EmployeeListNotFoundException(string message)
        : base(message)
    {
    }

    public EmployeeListNotFoundException(string message, Exception inner)
        : base(message, inner)
    {
    }
}
```

> [!NOTE]
> Em situações nas quais você está usando a comunicação remota, você deve garantir que os metadados para todas as exceções definidas pelo usuário estejam disponíveis no servidor (computador chamado) e para o cliente (o objeto de proxy ou chamador). Para obter mais informações, consulte [Práticas recomendadas para exceções](#best-practices-for-exceptions).

## <a name="best-practices-for-exceptions"></a>Práticas recomendadas para exceções

Um aplicativo bem projetado sabe tratar erros e exceções para evitar falhas. Esta seção descreve as práticas recomendadas para tratar e criar exceções.

### <a name="use-trycatchfinally-blocks"></a>Usar blocos try/catch/finally

Use blocos `try`/`catch`/`finally` em torno de código que potencialmente possa gerar uma exceção. 

Sempre ordene exceções em blocos `catch` da mais específica para a menos específica.

Use um bloco `finally` para limpar os recursos, independentemente de você poder recuperá-los ou não.

### <a name="handle-common-conditions-without-throwing-exceptions"></a>Tratar de condições comuns sem gerar exceções

Para condições que têm boa probabilidade de ocorrer mas que podem disparar uma exceção, considere tratá-las de uma maneira que evite essa exceção. Por exemplo, se você tentar fechar uma conexão que já está fechada, você obterá um `InvalidOperationException`. Você pode evitar isso usando uma instrução `if` para verificar o estado da conexão antes de tentar fechá-la.

C#
```
if (conn.State != ConnectionState.Closed)
{
    conn.Close();
}
```

Se você não verificar estado da conexão antes de fechar, você poderá capturar a exceção `InvalidOperationException`.

C#
```
try
{
    conn.Close();
}
catch (InvalidOperationException ex)
{
    Console.WriteLine(ex.GetType().FullName);
    Console.WriteLine(ex.Message);
}
```

O método a escolher depende da frequência com que você espera que o evento ocorra.

- Use o tratamento de exceções se o evento não ocorrer muito frequentemente, ou seja, se o evento é realmente excepcional e indica um erro (como um fim de arquivo inesperado). Quando você usa o tratamento de exceções, menos código é executado em condições normais.

- Verifique a existência de condições de erro no código se o evento ocorrer rotineiramente e puder ser considerado parte da execução normal. Quando você verifica se há condições de erro comuns, menos código é executado porque você evita exceções.

### <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Projetar classes de modo que as exceções possam ser evitadas

Uma classe pode fornecer métodos ou propriedades que permitem que você evite fazer uma chamada que dispararia uma exceção. Por exemplo, uma classe @System.IO.FileStream fornece métodos que ajudam a determinar se ao final do arquivo foi atingido. Elas podem ser usadas para evitar exceções geradas quando você faz a leitura após o fim do arquivo. O exemplo a seguir mostra como ler até o final de um arquivo sem disparar uma exceção.

C#
```
class FileRead
{
    public void ReadAll(FileStream fileToRead)
    {
        // This if statement is optional
        // as it is very unlikely that
        // the stream would ever be null.
        if (fileToRead == null)
        {
            throw new System.ArgumentNullException();
        }

        int b;

        // Set the stream position to the beginning of the file.
        fileToRead.Seek(0, SeekOrigin.Begin);

        // Read each byte to the end of the file.
        for (int i = 0; i < fileToRead.Length; i++)
        {
            b = fileToRead.ReadByte();
            Console.Write(b.ToString());
            // Or do something else with the byte.
        }
    }
}
```

Outra maneira de evitar exceções é retornar nulo para casos muito comuns de erro, em vez de gerar uma exceção. Um caso extremamente comum de erro pode ser considerado um fluxo normal de controle. Ao retornar nulo nesses casos, você minimiza o impacto no desempenho de um aplicativo.

### <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Gerar exceções em vez de retornar um código de erro

Exceções asseguram que falhas não passem despercebidas porque o código de chamada não verificou um código de retorno. 

### <a name="use-the-predefined-net-exception-types"></a>Usar os tipos de exceção do .NET predefinidos

Apresente uma nova classe de exceção apenas quando a predefinida não se aplicar. Por exemplo:

- Gere uma exceção @System.InvalidOperationException se uma propriedade de definição ou chamada de método não for adequada para o estado atual do objeto.

- Gere uma exceção @System.ArgumentException ou uma das classes predefinidas que derivam de @System.ArgumentException se parâmetros inválidos forem passados.

### <a name="end-exception-class-names-with-the-word-exception"></a>Terminar os nomes das classes de exceção com a palavra `Exception`

Quando uma exceção personalizada for necessária, nomeie-a adequadamente e derive-a da classe @System.Exception. Por exemplo:

C#
```
public class MyFileNotFoundException : Exception
{
}
```

### <a name="include-three-constructors-in-custom-exception-classes"></a>Incluir três construtores em classes de exceção personalizada

Use pelo menos três os construtores comuns ao criar suas próprias classes de exceção: o construtor padrão, um construtor que recebe uma mensagem de cadeia de caracteres e uma exceção interna.

- @System.Exception.%23ctor, que usa valores padrão.

- @System.Exception.%23ctor(System.String), que aceita uma mensagem de cadeia de caracteres.

- @System.Exception.%23ctor(System.String,System.Exception), que aceita uma mensagem de cadeia de caracteres e uma exceção interna.

Para ver um exemplo, veja [Como criar exceções definidas pelo usuário](#how-to-create-user-defined-exceptions).

### <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Certifique-se de que os dados de exceção estão disponíveis quando o código é executado remotamente

Ao criar exceções definidas pelo usuário, assegure que os metadados para as exceções estejam disponíveis para códigos executando remotamente. 

Por exemplo, em tempos de execução do .NET que implementam domínios de aplicativo, podem ocorrer exceções entre domínios de aplicativo. Suponha que o Domínio de Aplicativo A crie o Domínio de aplicativo B, o qual executa o código que gera uma exceção. Para que o Domínio de Aplicativo A capture e trate corretamente a exceção, ele deverá ser capaz de localizar o assembly que contém a exceção gerada pelo Domínio de Aplicativo B. Se o Domínio de Aplicativo B gerar uma exceção contida em um assembly em sua base de aplicativo, mas não na base de aplicativo do Domínio de Aplicativo A, o Domínio de Aplicativo A não será capaz de localizar a exceção e o Common Language Runtime gerará uma exceção @System.IO.FileNotFoundException. Para evitar essa situação, você pode implantar o assembly que contém as informações de exceção de duas maneiras:

- Coloque o assembly em uma base de aplicativos comum compartilhada por ambos os domínios de aplicativos.

    \- ou -

- Se os domínios não compartilham uma base de aplicativos comum, assine o assembly que contém as informações de exceção com um nome forte e implante o assembly no cache de assembly global.

### <a name="include-a-localized-description-string-in-every-exception"></a>Incluir uma cadeia de caracteres de descrição localizada em cada exceção

A mensagem de erro que o usuário recebe é derivada da cadeia de caracteres de descrição da exceção que foi gerada, em vez do nome da classe de exceção.

### <a name="use-grammatically-correct-error-messages"></a>Usar mensagens de erro gramaticalmente corretas

Escreva frases claras e inclua pontuação final. Cada sentença em uma cadeia de caracteres descrição de uma exceção deve terminar com um ponto final. Por exemplo, "A tabela de log estourou." seria uma cadeia de caracteres de descrição apropriada.

### <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Em exceções personalizadas, forneça propriedades adicionais conforme necessário

Forneça propriedades adicionais para uma exceção (além da cadeia de caracteres de descrição) somente quando houver um cenário programático no qual as informações adicionais serão úteis. Por exemplo, o @System.IO.FileNotFoundException fornece a propriedade @System.IO.FileNotFoundException.FileName.

### <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Posicionar instruções throw de modo que o rastreamento de pilha seja útil

O rastreamento de pilha começa na instrução na qual a exceção é lançada e termina na instrução `catch` que captura a exceção.

### <a name="use-exception-builder-methods"></a>Usar métodos de construtor de exceção

É comum uma classe lançar a mesma exceção em locais diferentes em sua implementação. Para evitar excesso de código, use métodos auxiliares que criam a exceção e a retornam. Por exemplo:

C#
```
class FileReader
{
    private string fileName;

    public FileReader(string path)
    {
        fileName = path;
    }

    public byte[] Read(int bytes)
    {
        byte[] results = FileUtils.ReadFromFile(fileName, bytes);
        if (results == null)
        {
            throw NewFileIOException();
        }
        return results;
    }

    FileReaderException NewFileIOException()
    {
        string description = "My NewFileIOException Description";

        return new FileReaderException(description);
    }
}

```

Em alguns casos, é mais adequado usar o construtor da exceção para compilá-la. Um exemplo é uma classe de exceção global como @System.ArgumentException, 

### <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Limpar resultados intermediários ao lançar uma exceção

Os chamadores devem ser capazes de pressupor que não haverá efeitos colaterais quando uma exceção for gerada de um método. Por exemplo, se você tiver um código que transfere dinheiro retirando-o de uma conta e depositando em outra e uma exceção for gerada ao executar o depósito, você não desejará que a retirada permaneça em vigor.

C#
```
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Uma maneira de lidar com essa situação é capturar todas as exceções geradas pela transação do depósito e reverter a retirada.

C#
```
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw
    }
}
```

Este exemplo ilustra o uso de `throw` para gerar novamente a exceção original, que pode tornar mais fácil para os chamadores ver a causa real do problema sem a necessidade de examinar a propriedade @System.Exception.InnerException. Uma alternativa é gerar uma nova exceção e incluir a exceção original como a exceção interna:

C#
```
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>Consulte também

Para saber mais sobre o funcionamento de exceções no .NET, veja [O que todo desenvolvedor precisa saber sobre exceções no tempo de execução](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).



<!--HONumber=Nov16_HO3-->


