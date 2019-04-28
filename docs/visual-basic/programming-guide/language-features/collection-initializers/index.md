---
title: Inicializadores de coleção (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: 538efc11e477a4e90b7bca286da4ed56105d7ecb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906822"
---
# <a name="collection-initializers-visual-basic"></a>Inicializadores de coleção (Visual Basic)

Os *inicializadores de coleção* fornecem uma sintaxe abreviada que permite criar uma coleção e preenchê-la com um conjunto inicial de valores. Os inicializadores de coleção são úteis quando você está criando uma coleção de um conjunto de valores conhecidos, por exemplo, uma lista de opções de menu ou de categorias, um conjunto inicial de valores numéricos, uma lista estática de cadeias de caracteres, como nomes de mês ou de dias, ou localizações geográficas, como uma lista de estados usada para validação.

Para obter mais informações sobre coleções, consulte [Coleções](../../../../visual-basic/programming-guide/concepts/collections.md).

Você identificará um inicializador de coleção usando a palavra-chave `From` seguida por chaves (`{}`). Isso é semelhante à sintaxe de literal de matriz descrita em [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md). Os exemplos a seguir mostram várias maneiras de usar inicializadores de coleção para criar coleções.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> O C# também fornece inicializadores de coleção. Os inicializadores de coleção C# fornecem a mesma funcionalidade que a dos inicializadores de coleção do Visual Basic. Para obter mais informações sobre os inicializadores de coleção do C#, consulte [Inicializadores de objeto e de coleção](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Sintaxe

Um inicializador de coleção consiste em uma lista de valores separados por vírgula colocados entre chaves (`{}`), precedidos pela palavra-chave `From`, conforme mostrado no código a seguir.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Ao criar uma coleção, como uma <xref:System.Collections.Generic.List%601> ou uma <xref:System.Collections.Generic.Dictionary%602>, você deverá fornecer o tipo de coleção antes do inicializador de coleção, conforme mostrado no código a seguir.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Você não pode combinar um inicializador de coleção com um inicializador de objeto para inicializar o mesmo objeto de coleção. Você pode usar os inicializadores de objeto para inicializar objetos em um inicializador de coleção.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Criação de uma coleção usando um inicializador de coleção

Ao criar uma coleção usando um inicializador de coleção, todo valor fornecido no inicializador de coleção será passado ao método `Add` apropriado da coleção. Por exemplo, se você criar uma <xref:System.Collections.Generic.List%601> usando um inicializador de coleção, todo valor de cadeia de caracteres no inicializador de coleção será passado ao método <xref:System.Collections.Generic.List%601.Add%2A>. Se desejar criar uma coleção usando um inicializador de coleção, o tipo especificado deverá ser um tipo de coleção válido. Os exemplos de tipos de coleção válidos incluem as classes que implementam a interface <xref:System.Collections.Generic.IEnumerable%601> ou que herdam a classe <xref:System.Collections.CollectionBase>. O tipo especificado também deve expor um método `Add` que atenda aos seguintes critérios.

- O método `Add` deve estar disponível no escopo em que o inicializador de coleção está sendo chamado. Se você estiver usando o inicializador de coleção em um cenário no qual os métodos não públicos da coleção possam ser acessados, o método `Add` não precisará ser público.

- O método `Add` deve ser um membro de instância ou um membro `Shared` da classe da coleção ou um método de extensão.

- Um método `Add` que possa ser correspondido deve existir, com base nas regras de resolução de sobrecarga, para os tipos fornecidos no inicializador de coleção.

 Por exemplo, o exemplo de código a seguir mostra como criar uma coleção `List(Of Customer)` usando um inicializador de coleção. Quando o código for executado, todo objeto `Customer` será passado ao método `Add(Customer)` da lista genérica.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

O exemplo de código a seguir mostra o código equivalente que não usa um inicializador de coleção.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Se a coleção tiver um método `Add` com parâmetros correspondentes ao construtor do objeto `Customer`, você poderá aninhar os valores de parâmetro do método `Add` nos inicializadores de coleção, conforme será discutido na próxima seção. Se a coleção não tiver um método `Add`, você poderá criar um como um método de extensão. Para obter um exemplo de como criar uma `Add` método como um método de extensão para uma coleção, consulte [como: Criar um método para Adicionar extensão usado por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Para obter um exemplo de como criar uma coleção personalizada que pode ser usada com um inicializador de coleção, consulte [como: Criar uma coleção usada por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Aninhando inicializadores de coleção

Você pode aninhar valores em um inicializador de coleção para identificar uma sobrecarga específica de um método `Add` para a coleção que está sendo criada. Os valores passados ao método `Add` devem ser separados por vírgula e colocados entre chaves (`{}`), como você faria em uma literal de matriz ou em um inicializador de coleção.

Ao criar uma coleção usando valores aninhados, todo elemento da lista de valores aninhados é passado como um argumento ao método `Add` correspondente aos tipos de elemento. Por exemplo, o exemplo de código a seguir cria um <xref:System.Collections.Generic.Dictionary%602> em que as chaves são do tipo `Integer` e os valores, do tipo `String`. Cada uma das listas de valores aninhados corresponde ao método <xref:System.Collections.Generic.Dictionary%602.Add%2A> do `Dictionary`.

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

O exemplo de código anterior é equivalente ao seguinte código.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

Somente as listas de valores aninhados do primeiro nível de aninhamento são enviadas ao método `Add` do tipo de coleção. Níveis de aninhamento mais profundos são tratados como literais de matriz e as listas de valores aninhados não correspondem ao método `Add` de nenhuma coleção.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|---|---|
|[Como: Criar um método para Adicionar extensão usado por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Mostra como criar um método de extensão chamado `Add`, que pode ser usado para preencher uma coleção com valores de um inicializador de coleção.|
|[Como: Criar uma coleção usada por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Mostra como habilitar o uso de um inicializador de coleção, incluindo um método `Add` em uma classe de coleção que implementa `IEnumerable`.|

## <a name="see-also"></a>Consulte também

- [Coleções](../../../../visual-basic/programming-guide/concepts/collections.md)
- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Inicializadores de objeto: Tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Propriedades Autoimplementadas](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Como: Inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Como: Criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
