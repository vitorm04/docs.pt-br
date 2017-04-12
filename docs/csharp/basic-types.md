---
title: "Tipos básicos | Guia de C#"
description: "Saiba mais sobre os tipos principais (numéricos, cadeias de caracteres e objetos) em todos os programas em C#"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 57c5524a18535778db337500b0a7e9013ce93519
ms.lasthandoff: 03/13/2017

---

# <a name="types-variables-and-values"></a>Tipos, variáveis e valores  
O C# é uma linguagem fortemente tipada. Todas as variáveis e constantes têm um tipo, assim como cada expressão que é avaliada como um valor. Cada assinatura de método especifica um tipo para cada parâmetro de entrada e para o valor retornado. A biblioteca de classes .NET Framework define um conjunto de tipos numéricos internos, bem como tipos mais complexos que representam uma ampla variedade de constructos lógicos, como o sistema de arquivos, as conexões de rede, as coleções e as matrizes de objetos e as datas. Um programa em C# típico usa tipos da biblioteca de classes, bem como tipos definidos pelo usuário que modelam os conceitos que são específicos para o domínio do problema do programa.  
  
As informações armazenadas em um tipo podem incluir o seguinte:  
  
-   O espaço de armazenamento que uma variável do tipo requer.  
  
-   Os valores mínimo e máximo que ele pode representar.  
  
-   Os membros (métodos, campos, eventos e etc.) que ele contém.  
  
-   O tipo base do qual ele herda.  
  
-   O local no qual a memória para as variáveis será alocada em tempo de execução.  
  
-   Os tipos de operações que são permitidos.  
  
O compilador usa as informações de tipo para garantir que todas as operações que são realizadas em seu código sejam *fortemente tipadas*. Por exemplo, se você declarar uma variável do tipo [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx), o compilador permitirá que você use a variável nas operações de adição e subtração. Se você tentar executar as mesmas operações em uma variável do tipo [bool](https://msdn.microsoft.com/library/c8f5xwh7.aspx), o compilador gerará um erro, como mostrado no exemplo a seguir:  
  
[!code-csharp[Segurança de tipos](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
>  Desenvolvedores de C e C++, observem que, em C#, [bool](https://msdn.microsoft.com/library/c8f5xwh7.aspx) não é conversível em [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx).  
  
O compilador insere as informações de tipo no arquivo executável como metadados. O CLR (Common Language Runtime) usa esses metadados em tempo de execução para assegurar mais segurança de tipos ao alocar e recuperar a memória.  

## <a name="specifying-types-in-variable-declarations"></a>Especificando tipos em declarações de variável  
Quando declara uma variável ou constante em um programa, você deve especificar o tipo da variável ou usar a palavra-chave [var](https://msdn.microsoft.com/library/bb383973.aspx) para permitir que o compilador infira o tipo. O exemplo a seguir mostra algumas declarações de variáveis que usam tipos numéricos internos e tipos complexos definidos pelo usuário:  
  
[!code-csharp[Declaração de variável](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Os tipos de parâmetros de método e valores de retornados são especificados na assinatura do método. A assinatura a seguir mostra um método que requer um [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx) como um argumento de entrada e retorna uma cadeia de caracteres:  
  
[!code-csharp[Assinatura do método](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Depois que uma variável é declarada, ela não pode ser declarada novamente com um novo tipo e não pode ter um valor atribuído que não seja compatível com seu tipo declarado. Por exemplo, você não pode declarar um [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx) e, em seguida, atribuir a ele um valor booliano de [true](https://msdn.microsoft.com/library/06d3w013.aspx). No entanto, os valores podem ser convertidos em outros tipos, por exemplo, quando são passados como argumentos de método ou atribuídos a novas variáveis. Uma *conversão de tipo* que não causa a perda de dados é executada automaticamente pelo compilador. Uma conversão que pode causar perda de dados requer um *cast* no código-fonte. 

Para obter mais informações, consulte [Conversões cast e conversões de tipo](https://msdn.microsoft.com/library/ms173105.aspx).
 
## <a name="built-in-types"></a>Tipos internos
O C# fornece um conjunto padrão de tipos numéricos internos para representar números inteiros, valores de ponto flutuante, expressões boolianas, caracteres de texto, valores decimais e outros tipos de dados. Também há tipos internos de **cadeias de caracteres** de **objetos**. Eles estão disponíveis para uso em qualquer programa em C#. Para obter mais informações sobre os tipos internos, consulte [Tabelas de referência de tipos](https://msdn.microsoft.com/library/1dhd7f2x.aspx).  
  
## <a name="custom-types"></a>Tipos personalizados  
Você usa os constructos [struct](https://msdn.microsoft.com/library/ah19swz4.aspx), [classe](https://msdn.microsoft.com/library/0b0thckt.aspx), [interface](https://msdn.microsoft.com/library/87d83y5b.aspx) e [enum](https://msdn.microsoft.com/library/sbbt4032.aspx) para criar seus próprios tipos personalizados. A biblioteca de classes .NET Framework em si é uma coleção de tipos personalizados fornecidos pela Microsoft que você pode usar em seus próprios aplicativos. Por padrão, os tipos usados com mais frequência na biblioteca de classes estão disponíveis em qualquer programa em C#. Outros ficam disponíveis somente quando você adiciona explicitamente uma referência de projeto ao assembly no qual eles estão definidos. Depois que o compilador tiver uma referência ao assembly, você pode declarar variáveis (e constantes) dos tipos declarados nesse assembly no código-fonte. Para obter mais informações, consulte [Biblioteca de classes .NET Framework](https://msdn.microsoft.com/library/gg145045(v=vs.110).aspx).  
  
## <a name="generic-types"></a>Tipos genéricos  
Um tipo pode ser declarado com um ou mais *parâmetros de tipo* que servem como um espaço reservado para o tipo real (o *tipo concreto*) que o código cliente fornecerá ao criar uma instância do tipo. Esses tipos são chamados de *tipos genéricos*. Por exemplo, o tipo do .NET Framework @System.Collections.Generic.List%601 tem um parâmetro de tipo que, por convenção, recebe o nome *T*. Ao criar uma instância do tipo, você especifica o tipo dos objetos que a lista conterá, por exemplo, a cadeia de caracteres:  
  
[!code-csharp[Tipos genéricos](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)] 
  
O uso do parâmetro de tipo possibilita a reutilização da mesma classe para conter qualquer tipo de elemento sem precisar converter cada elemento em [objeto](https://msdn.microsoft.com/library/9kkx3h3c.aspx). As classes de coleção genéricas são chamadas de *coleções fortemente tipadas* porque o compilador sabe o tipo específico dos elementos da coleção e pode gerar um erro em tempo de compilação se, por exemplo, você tentar adicionar um inteiro ao objeto `strings` no exemplo anterior. Para obter mais informações, consulte [Genéricos](programming-guide/generics/index.md). 

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Tipos implícitos, tipos anônimos e tipos de tupla  
Conforme mencionado anteriormente, você pode digitar implicitamente uma variável local (mas não os membros de classe) usando a palavra-chave [var](https://msdn.microsoft.com/library/bb383973.aspx). A variável ainda recebe um tipo em tempo de compilação, mas o tipo é fornecido pelo compilador. Para obter mais informações, consulte [Variáveis locais de tipo implícito](https://msdn.microsoft.com/library/bb384061.aspx).  
  
Em alguns casos, é inconveniente criar um tipo nomeado para conjuntos simples de valores relacionados que você não pretende armazenar ou transmitir para fora dos limites do método. Você pode criar *tipos anônimos* para essa finalidade. Para obter mais informações, consulte [Tipos anônimos](https://msdn.microsoft.com/library/bb397696.aspx).

É comum querer retornar mais de um valor de um método. Você pode criar *tipos de tupla* que retornam vários valores em uma única chamada de método. Para obter mais informações, consulte [Tuplas](tuples.md)

## <a name="the-common-type-system"></a>O Common Type System  
É importante entender dois pontos fundamentais sobre o sistema de tipo no .NET Framework:  
  
-   Ele dá suporte ao conceito de herança. Os tipos podem derivar de outros tipos, chamados *tipos base*. O tipo derivado herda (com algumas restrições) os métodos, as propriedades e outros membros do tipo base. O tipo base, por sua vez, pode derivar de algum outro tipo, nesse caso, o tipo derivado herda os membros de ambos os tipos base na sua hierarquia de herança. Todos os tipos, incluindo tipos numéricos internos, como o @System.Int32 (palavra-chave do C#: `int`), derivam, em última análise, de um único tipo base, que é o @System.Object (palavra-chave do C#: `object`). Essa hierarquia unificada de tipos é chamada de [CTS](../standard/common-type-system.md) (Common Type System). Para obter mais informações sobre herança em C#, consulte [Herança](https://msdn.microsoft.com/library/ms173149.aspx).  
  
-   Cada tipo no CTS é definido como um *tipo de valor* ou um *tipo de referência*. Isso inclui todos os tipos personalizados na biblioteca de classes .NET Framework e também seus próprios tipos definidos pelo usuário. Os tipos que você define usando a palavra-chave [struct](https://msdn.microsoft.com/library/ah19swz4.aspx) são tipos de valor. Todos os tipos numéricos internos são **structs**. Para obter mais informações sobre tipos de valor, consulte [Structs](structs.md). Os tipos que você define usando a palavra-chave [class](https://msdn.microsoft.com/library/0b0thckt.aspx) são tipos de referência. Para obter mais informações sobre tipos de referência, consulte [Classes](classes.md). Os tipos de referência e os tipos de valor têm diferentes regras de tempo de compilação e comportamento de tempo de execução diferente.
 
  
## <a name="see-also"></a>Consulte também
[Estruturas](structs.md)

[Classes](classes.md)

