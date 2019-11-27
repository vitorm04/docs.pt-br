---
title: Tipos genéricos
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
ms.openlocfilehash: 3dcd7756b10fab8f66f4d5c10acedd8f600eb2e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350119"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Tipos genéricos no Visual Basic (Visual Basic)
Um *tipo genérico* é um único elemento de programação que se adapta para executar a mesma funcionalidade para uma variedade de tipos de dados. Quando você define uma classe ou procedimento genérico, não é necessário definir uma versão separada para cada tipo de dados para o qual você talvez queira executar essa funcionalidade.  
  
 Uma analogia é um conjunto de chave de fenda com cabeçotes removíveis. Você inspeciona o parafuso que precisa ativar e seleciona a cabeça correta para esse parafuso (com fenda, cruzada, estrelado). Depois de inserir a cabeça correta no identificador da chave de fenda, você executará exatamente a mesma função com a chave de fenda, ou seja, virando o parafuso.  
  
 ![Diagrama de um conjunto de chave de fenda com cabeçotes diferentes.](./media/generic-types/generic-screwdriver-set.gif)  
  
 Quando você define um tipo genérico, você o parametriza com um ou mais tipos de dados. Isso permite que o código de uso Personalize os tipos de dados para seus requisitos. Seu código pode declarar vários elementos de programação diferentes do elemento genérico, cada um atuando em um conjunto diferente de tipos de dados. Mas os elementos declarados executam a lógica idêntica, não importa quais tipos de dados eles estão usando.  
  
 Por exemplo, talvez você queira criar e usar uma classe de fila que opere em um tipo de dados específico, como `String`. Você pode declarar uma classe desse tipo de <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Agora você pode usar `stringQ` para trabalhar exclusivamente com `String` valores. Como `stringQ` é específico para `String` em vez de ser generalizado para valores de `Object`, você não tem associação tardia ou conversão de tipo. Isso poupa tempo de execução e reduz os erros de tempo de execução.  
  
 Para obter mais informações sobre como usar um tipo genérico, consulte [como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Exemplo de uma classe genérica  
 O exemplo a seguir mostra uma definição de esqueleto de uma classe genérica.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 No esqueleto anterior, `t` é um *parâmetro de tipo*, ou seja, um espaço reservado para um tipo de dados que você fornece ao declarar a classe. Em outro lugar do código, você pode declarar várias versões do `classHolder` fornecendo vários tipos de dados para `t`. O exemplo a seguir mostra duas declarações desse tipo.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 As instruções anteriores declaram *classes construídas*, nas quais um tipo específico substitui o parâmetro de tipo. Essa substituição é propagada em todo o código dentro da classe construída. O exemplo a seguir mostra a aparência do procedimento de `processNewItem` no `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Para obter um exemplo mais completo, consulte [como: definir uma classe que pode fornecer funcionalidade idêntica em diferentes tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Elementos de programação qualificados  
 Você pode definir e usar classes, estruturas, interfaces, procedimentos e delegados genéricos. Observe que a .NET Framework define várias classes, estruturas e interfaces genéricas que representam elementos genéricos comumente usados. O namespace <xref:System.Collections.Generic?displayProperty=nameWithType> fornece dicionários, listas, filas e pilhas. Antes de definir seu próprio elemento genérico, confira se ele já está disponível no <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Os procedimentos não são tipos, mas você pode definir e usar procedimentos genéricos. Consulte [procedimentos genéricos em Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Vantagens dos tipos genéricos  
 Um tipo genérico serve como base para declarar vários elementos de programação diferentes, cada um operando em um tipo de dados específico. As alternativas para um tipo genérico são:  
  
1. Um único tipo operando no tipo de dados `Object`.  
  
2. Um conjunto de versões *específicas de tipo* do tipo, cada versão codificada individualmente e operando em um tipo de dados específico, como `String`, `Integer`ou um tipo definido pelo usuário, como `customer`.  
  
 Um tipo genérico tem as seguintes vantagens sobre essas alternativas:  
  
- **Segurança de tipo.** Tipos genéricos impõem verificação de tipo em tempo de compilação. Tipos com base em `Object` aceitam qualquer tipo de dados e você deve escrever código para verificar se um tipo de dados de entrada é aceitável. Com tipos genéricos, o compilador pode capturar incompatibilidades de tipo antes do tempo de execução.  
  
- **Desempenho.** Os tipos genéricos não têm dados *Box* e *unbox* , porque cada um é especializado para um tipo de dados. As operações baseadas em `Object` devem digitar tipos de dados de entrada para convertê-los em dados `Object` e unbox destinados para saída. Boxing e unboxing reduzem o desempenho.  
  
     Os tipos baseados em `Object` também são de associação tardia, o que significa que acessar seus membros requer código extra em tempo de execução. Isso também reduz o desempenho.  
  
- **Consolidação de código.** O código em um tipo genérico deve ser definido apenas uma vez. Um conjunto de versões específicas de tipo de um tipo deve replicar o mesmo código em cada versão, com a única diferença sendo o tipo de dados específico para essa versão. Com tipos genéricos, as versões específicas de tipo são todas geradas a partir do tipo genérico original.  
  
- **Reutilização de código.** O código que não depende de um determinado tipo de dados pode ser reutilizado com vários tipos de dados se for genérico. Muitas vezes, você pode reutilizá-lo mesmo com um tipo de dados que você não prevê originalmente.  
  
- **Suporte a IDE.** Quando você usa um tipo construído declarado de um tipo genérico, o IDE (ambiente de desenvolvimento integrado) pode oferecer mais suporte enquanto você está desenvolvendo seu código. Por exemplo, o IntelliSense pode mostrar as opções específicas de tipo para um argumento para um construtor ou método.  
  
- **Algoritmos genéricos.** Os algoritmos abstratos que são independentes de tipo são bons candidatos para tipos genéricos. Por exemplo, um procedimento genérico que classifica itens usando a interface <xref:System.IComparable> pode ser usado com qualquer tipo de dados que implementa <xref:System.IComparable>.  
  
## <a name="constraints"></a>Restrições  
 Embora o código em uma definição de tipo genérico deva ser o mais independente de tipo possível, talvez seja necessário exigir um determinado recurso de qualquer tipo de dados fornecido ao seu tipo genérico. Por exemplo, se você quiser comparar dois itens com a finalidade de classificar ou agrupar, seu tipo de dados deve implementar a interface <xref:System.IComparable>. Você pode impor esse requisito adicionando uma *restrição* ao parâmetro de tipo.  
  
### <a name="example-of-a-constraint"></a>Exemplo de uma restrição  
 O exemplo a seguir mostra uma definição de esqueleto de uma classe com uma restrição que requer o argumento de tipo para implementar <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Se o código subsequente tentar construir uma classe de `itemManager` fornecendo um tipo que não implementa <xref:System.IComparable>, o compilador sinalizará um erro.  
  
### <a name="types-of-constraints"></a>Tipos de restrições  
 Sua restrição pode especificar os seguintes requisitos em qualquer combinação:  
  
- O argumento de tipo deve implementar uma ou mais interfaces  
  
- O argumento de tipo deve ser do tipo ou herdar de, no máximo, uma classe  
  
- O argumento de tipo deve expor um construtor sem parâmetros acessível para o código que cria objetos a partir dele  
  
- O argumento de tipo deve ser um *tipo de referência*ou deve ser um *tipo de valor*  
  
 Se você precisar impor mais de um requisito, use uma *lista de restrições* separada por vírgulas dentro de chaves (`{ }`). Para exigir um construtor acessível, você inclui a palavra-chave [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) na lista. Para exigir um tipo de referência, você inclui a palavra-chave `Class`; para exigir um tipo de valor, você inclui a palavra-chave `Structure`.  
  
 Para obter mais informações sobre restrições, consulte [lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Exemplo de várias restrições  
 O exemplo a seguir mostra uma definição de esqueleto de uma classe genérica com uma lista de restrições no parâmetro de tipo. No código que cria uma instância dessa classe, o argumento de tipo deve implementar as interfaces <xref:System.IComparable> e <xref:System.IDisposable>, ser um tipo de referência e expor um construtor sem parâmetros acessível.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Termos importantes  
 Os tipos genéricos apresentam e usam os seguintes termos:  
  
- *Tipo genérico*. Uma definição de uma classe, estrutura, interface, procedimento ou delegado para o qual você fornece pelo menos um tipo de dados ao declará-lo.  
  
- *Parâmetro de tipo*. Em uma definição de tipo genérico, um espaço reservado para um tipo de dados que você fornece ao declarar o tipo.  
  
- *Argumento de tipo*. Um tipo de dados específico que substitui um parâmetro de tipo quando você declara um tipo construído de um tipo genérico.  
  
- *Restrição*. Uma condição em um parâmetro de tipo que restringe o argumento de tipo que você pode fornecer para ele. Uma restrição pode exigir que o argumento de tipo deva implementar uma interface específica, ser ou herdar de uma classe específica, ter um construtor sem parâmetros acessível ou ser um tipo de referência ou um tipo de valor. Você pode combinar essas restrições, mas pode especificar no máximo uma classe.  
  
- *Tipo construído*. Uma classe, estrutura, interface, procedimento ou delegado declarado de um tipo genérico fornecendo argumentos de tipo para seus parâmetros de tipo.  
  
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
