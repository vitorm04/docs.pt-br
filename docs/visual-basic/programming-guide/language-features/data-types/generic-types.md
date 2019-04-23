---
title: Tipos genéricos no Visual Basic (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: 768f7704851a5f54f4b4a7535fe2584e20bfaa0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301224"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Tipos genéricos no Visual Basic (Visual Basic)
Um *tipo genérico* é um único elemento de programação que se adapta ao executar a mesma funcionalidade para uma variedade de tipos de dados. Quando você define uma classe genérica ou um procedimento, você não precisa definir uma versão separada para cada tipo de dados para os quais você talvez queira executar essa funcionalidade.  
  
 Uma analogia é uma chave de fenda com cabeçotes removíveis. Você inspeciona o parafuso você precisa desativar e selecione o cabeçalho correto para aquele parafuso (encaixado, ultrapassado, estrelado). Depois de inserir a cabeça correta no identificador de chave de fenda, você executar a mesma função exata com a chave de fenda, saber apertar o parafuso.  
  
 ![Diagrama de uma chave de fenda definido com cabeçotes diferentes.](./media/generic-types/generic-screwdriver-set.gif)  
  
 Quando você define um tipo genérico, parametrize-o com um ou mais tipos de dados. Isso permite que o uso de código para personalizar os tipos de dados para seus requisitos. Seu código pode declarar vários elementos de programação diferentes a partir do elemento genérico, cada um agindo em um conjunto diferente de tipos de dados. Mas todos os elementos declarados realizam a lógica idêntica, não importa quais tipos de dados que estão usando.  
  
 Por exemplo, você talvez queira criar e usar uma classe de fila que opera em um tipo de dados específico, como `String`. Você pode declarar essa classe de <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Agora você pode usar `stringQ` para trabalhar exclusivamente com `String` valores. Porque `stringQ` é específico para `String` em vez de ser generalizado para `Object` valores, você não tenha tardia associação ou conversão de tipos. Isso economiza tempo de execução e reduz os erros de tempo de execução.  
  
 Para obter mais informações sobre como usar um tipo genérico, consulte [como: Usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Exemplo de uma classe genérica  
 O exemplo a seguir mostra uma definição de uma classe genérica.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 No esqueleto anterior, `t` é um *parâmetro de tipo*, ou seja, um espaço reservado para um tipo de dados que você fornece ao declarar a classe. Em outro lugar no seu código, você pode declarar as várias versões do `classHolder` , fornecendo vários tipos de dados para `t`. O exemplo a seguir mostra duas declarações desse tipo.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 As declarações anteriores declaram *classes construídas*, no qual um tipo específico substitui o parâmetro de tipo. Essa substituição é propagada por todo o código dentro da classe construída. O exemplo a seguir mostra o que o `processNewItem` procedimento parece em `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Para obter um exemplo mais completo, confira [Como: Definir uma classe que pode fornecer uma funcionalidade idêntica em tipos de dados diferentes](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Elementos de programação qualificados  
 Você pode definir e usar delegados, estruturas, interfaces, procedimentos e as classes genéricas. Observe que o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] define várias classes genéricas, estruturas e interfaces que representam os elementos genéricos comumente usados. O <xref:System.Collections.Generic?displayProperty=nameWithType> namespace fornece dicionários, listas, filas e pilhas. Antes de definir seu próprio elemento genérico, confira se ele já está disponível em <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Procedimentos não são de tipos, mas você pode definir e usar procedimentos genéricos. Ver [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Vantagens de tipos genéricos  
 Um tipo genérico serve como base para declarar vários elementos de programação diferentes, cada uma delas opera em um tipo de dados específico. As alternativas para um tipo genérico são:  
  
1. Um único tipo de operando com o `Object` tipo de dados.  
  
2. Um conjunto de *específicos do tipo* as versões do tipo, cada versão individualmente codificada e operando em um tipo de dados específico, como `String`, `Integer`, ou um tipo definido pelo usuário, como `customer`.  
  
 Um tipo genérico tem as seguintes vantagens sobre essas alternativas:  
  
-   **Segurança de tipo.** Tipos genéricos impõem a verificação de tipo em tempo de compilação. Tipos baseados em `Object` aceitar qualquer tipo de dados, e você deve escrever código para verificar se um tipo de dados de entrada é aceitável. Com tipos genéricos, o compilador pode detectar incompatibilidades de tipo antes do tempo de execução.  
  
-   **Desempenho.** Tipos genéricos não é necessário *caixa de* e *conversão unboxing* dados, porque cada um deles é especializado para um tipo de dados. Operações com base em `Object` deve caixa tipos de dados de entrada para convertê-las para `Object` e conversão unboxing dados destinados à saída. Conversões boxing e unboxing reduzem o desempenho.  
  
     Tipos baseados em `Object` são também de associação tardia, o que significa que acessar seus membros requer código extra em tempo de execução. Isso também reduz o desempenho.  
  
-   **Código de consolidação.** O código em um tipo genérico deve ser definido apenas uma vez. Um conjunto de versões de tipo específico de um tipo deve replicar o mesmo código em cada versão, com a única diferença é o tipo de dados específico para essa versão. Com tipos genéricos, as versões específicas do tipo são todas geradas a partir do tipo genérico original.  
  
-   **Reutilização de código.** Código que não depende de um determinado tipo de dados pode ser reutilizado com vários tipos de dados se ele for genérico. Geralmente, você pode reutilizá-lo mesmo com um tipo de dados que você não originalmente prevê.  
  
-   **Suporte do IDE.** Quando você usa um tipo construído declarado de um tipo genérico, o ambiente de desenvolvimento integrado (IDE) pode lhe dar mais suporte enquanto você estiver desenvolvendo seu código. Por exemplo, o IntelliSense pode mostrar as opções de tipo específico para um argumento para um construtor ou método.  
  
-   **Algoritmos genéricos.** Abstratos algoritmos que são independentes de tipo são bons candidatos para tipos genéricos. Por exemplo, um procedimento genérico que classifica os itens que usam o <xref:System.IComparable> interface pode ser usado com qualquer tipo de dados que implemente <xref:System.IComparable>.  
  
## <a name="constraints"></a>Restrições  
 Embora o código em uma definição de tipo genérico deve ser tão independente de tipo quanto possível, você precisa exigir uma determinada capacidade de qualquer tipo de dados fornecido para o tipo genérico. Por exemplo, se você quiser comparar dois itens com a finalidade de classificação ou agrupamento, o tipo de dados deve implementar o <xref:System.IComparable> interface. Você pode aplicar esse requisito, adicionando um *restrição* para o parâmetro de tipo.  
  
### <a name="example-of-a-constraint"></a>Exemplo de uma restrição  
 O exemplo a seguir mostra uma definição de uma classe com uma restrição que requer o argumento de tipo para implementar <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Se o código subsequente tenta construir uma classe de `itemManager` fornecendo um tipo que não implementa <xref:System.IComparable>, o compilador sinaliza um erro.  
  
### <a name="types-of-constraints"></a>Tipos de restrições  
 A restrição pode especificar os requisitos a seguir em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve ser do tipo de, ou herdar de, no máximo uma classe  
  
-   O argumento de tipo deve expor um construtor sem parâmetros acessível para o código que cria objetos a partir dele  
  
-   O argumento de tipo deve ser um *tipo de referência*, ou deve ser um *tipo de valor*  
  
 Se você precisar de mais de um requisito de impor, use uma separada por vírgulas *lista de restrições* entre chaves (`{ }`). Para exigir um construtor acessível, você inclui o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave na lista. Para exigir um tipo de referência, você deve incluir a `Class` palavra-chave; para exigir um tipo de valor, você incluir o `Structure` palavra-chave.  
  
 Para obter mais informações sobre restrições, consulte [lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Exemplo de várias restrições  
 O exemplo a seguir mostra uma definição de uma classe genérica com uma lista de restrições no parâmetro de tipo. No código que cria uma instância dessa classe, o argumento de tipo deve implementar ambas as <xref:System.IComparable> e <xref:System.IDisposable> interfaces, ser um tipo de referência e expor um construtor sem parâmetros acessível.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Termos importantes  
 Tipos genéricos apresentam e usam os seguintes termos:  
  
-   *Tipo genérico*. Uma definição de classe, estrutura, interface, procedimento ou delegado para o qual você fornecer pelo menos um tipo de dados quando você declará-la.  
  
-   *Parâmetro de tipo*. Em uma definição de tipo genérico, um espaço reservado para um tipo de dados você fornece ao declarar o tipo.  
  
-   *O argumento de tipo*. Um tipo de dados específico que substitui um parâmetro de tipo quando você declara um tipo construído de um tipo genérico.  
  
-   *Restrição*. Uma condição em um parâmetro de tipo que restringe o argumento de tipo que você pode fornecer para ele. Uma restrição pode exigir que o argumento de tipo deve implementar uma interface específica, ser ou herdar de uma determinada classe, ter um construtor sem parâmetros acessível ou ser um tipo de referência ou um tipo de valor. Você pode combinar essas restrições, mas você pode especificar no máximo uma classe.  
  
-   *Tipo construído*. Uma classe, estrutura, interface, procedimento ou delegado declarado de um tipo genérico, fornecendo argumentos de tipo para seus parâmetros de tipo.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Of](../../../../visual-basic/language-reference/statements/of-clause.md)
- [As](../../../../visual-basic/language-reference/statements/as-clause.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Covariância e Contravariância](../../concepts/covariance-contravariance/index.md)
- [Iteradores](../../../../visual-basic/programming-guide/concepts/iterators.md)
