---
title: "Tipos genéricos no Visual Basic (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- generic interfaces
- data type arguments, defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword, using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures, generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes, Visual Basic
- parameters, type
- type arguments
- interfaces, generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters, generic
- generic structures
- generic classes
- type parameters
- data type arguments
- structures, generic
- parameters, data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
caps.latest.revision: 45
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1f6c48ff7f72eb86526ed4d71e6259b7886aab25
ms.lasthandoff: 03/13/2017

---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Tipos genéricos no Visual Basic (Visual Basic)
A *tipo genérico* é um único elemento de programação que se adapta ao executar a mesma funcionalidade para uma variedade de tipos de dados. Quando você define uma classe genérica ou procedimento, você não precisa definir uma versão separada para cada tipo de dados para o qual deseja executar essa funcionalidade.  
  
 Uma analogia é uma chave de fenda com cabeçotes removíveis. Você inspeciona o parafuso você precisa ativar e seleciona o cabeçote correto para aquele parafuso (encaixado, ultrapassado, estrelada). Depois de inserir a cabeça correta no identificador de chave de fenda, você executar a mesma função exata com a chave de fenda saber apertar o parafuso.  
  
 ![Diagrama de uma chave de fenda definido como uma ferramenta genérica](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")  
Chave de fenda definido como uma ferramenta genérica  
  
 Quando você define um tipo genérico, você pode parametrizá-lo com um ou mais tipos de dados. Isso permite o uso de código para personalizar os tipos de dados aos seus requisitos. Seu código pode declarar vários elementos de programação diferentes a partir do elemento genérico, cada um agindo em um conjunto diferente de tipos de dados. Mas todos os elementos declarados realizam a lógica idêntica, não importa quais tipos de dados que estão usando.  
  
 Por exemplo, você talvez queira criar e usar uma classe da fila que opera em um tipo de dados específico, como `String`. Você pode declarar essa classe de <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>, como mostra o exemplo a seguir.</xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
 [!code-vb[VbVbalrDataTypes n º&1;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 Agora você pode usar `stringQ` para trabalhar exclusivamente com `String` valores. Porque `stringQ` é específico para `String` em vez de ser generalizado para `Object` valores, você não tem a conversão de tipo ou associação tardia. Isso economiza tempo de execução e reduz os erros de tempo de execução.  
  
 Para obter mais informações sobre como usar um tipo genérico, consulte [como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Exemplo de uma classe genérica  
 O exemplo a seguir mostra uma definição de uma classe genérica.  
  
 [!code-vb[VbVbalrDataTypes n º&2;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 No esqueleto anterior, `t` é um *parâmetro de tipo*, ou seja, um espaço reservado para um tipo de dados que você fornece ao declarar a classe. Em outro lugar no seu código, você pode declarar várias versões do `classHolder` , fornecendo vários tipos de dados para `t`. O exemplo a seguir mostra duas declarações desse tipo.  
  
 [!code-vb[VbVbalrDataTypes n º&3;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 As declarações anteriores declaram *classes construídas*, no qual um tipo específico substitui o parâmetro de tipo. Essa substituição é propagada por todo o código dentro da classe construída. O exemplo a seguir mostra o que o `processNewItem` procedimento parece em `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes n º&4;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 Para obter um exemplo mais completo, consulte [como: definir uma classe que pode fornecer funcionalidade idêntica em diferentes tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Elementos de programação qualificados  
 Você pode definir e usar classes genéricas, estruturas, interfaces, procedimentos e representantes. Observe que o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] define várias classes genéricas, estruturas e interfaces que representam elementos genéricos comumente usados. O <xref:System.Collections.Generic?displayProperty=fullName>namespace fornece dicionários, listas, filas e pilhas.</xref:System.Collections.Generic?displayProperty=fullName> Antes de definir seu próprio elemento genérico, verifique se ele já está disponível em <xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName>  
  
 Procedimentos não são de tipos, mas você pode definir e usar procedimentos genéricos. Consulte [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Vantagens de tipos genéricos  
 Um tipo genérico serve como base para declarar vários elementos de programação diferentes, cada uma delas opera em um tipo de dados específico. As alternativas para um tipo genérico são:  
  
1.  Um único tipo de operando com o `Object` tipo de dados.  
  
2.  Um conjunto de *específicos do tipo* versões do tipo, cada versão individualmente codificada e operando em um determinado tipo de dados como `String`, `Integer`, ou um tipo definido pelo usuário, como `customer`.  
  
 Um tipo genérico tem as seguintes vantagens sobre essas alternativas:  
  
-   **Segurança de tipo.** Tipos genéricos impõem verificação de tipos em tempo de compilação. Tipos baseados em `Object` aceitar qualquer tipo de dados, e você deve escrever código para verificar se um tipo de dados de entrada é aceitável. Com tipos genéricos, o compilador pode detectar incompatibilidades de tipo antes do tempo de execução.  
  
-   **Desempenho.** Tipos genéricos não têm de *caixa* e *unbox* dados, porque cada um deles é especializado para um tipo de dados. Operações com base em `Object` devem encaixotar tipos de dados de entrada para convertê-los para `Object` e converter dados destinados para saída. Conversões boxing e unboxing reduzem o desempenho.  
  
     Tipos baseados em `Object` são também de ligação tardia, o que significa que acessar seus membros requer código extra no tempo de execução. Isso também reduz o desempenho.  
  
-   **Código de consolidação.** O código em um tipo genérico deve ser definido apenas uma vez. Um conjunto de versões de tipo específico de um tipo deve replicar o mesmo código em cada versão, com a única diferença é o tipo de dados específicos para essa versão. Com tipos genéricos, as versões específicas do tipo são todas geradas a partir do tipo genérico original.  
  
-   **Reutilização de código.** Código que não depende de um determinado tipo de dados pode ser reutilizado com vários tipos de dados se ele for genérico. Você geralmente pode reutilizá-lo mesmo com um tipo de dados que você não originalmente prevê.  
  
-   **Suporte ao IDE.** Quando você usa um tipo construído declarado de um tipo genérico, o ambiente de desenvolvimento integrado (IDE) pode lhe dar mais suporte enquanto você estiver desenvolvendo seu código. Por exemplo, o IntelliSense pode mostrar as opções de tipo específico para um argumento a um construtor ou método.  
  
-   **Algoritmos genéricos.** Abstratos algoritmos que são independentes de tipo são bons candidatos para tipos genéricos. Por exemplo, um procedimento genérico que classifica itens usando a <xref:System.IComparable>interface pode ser usada com qualquer tipo de dados que implemente <xref:System.IComparable>.</xref:System.IComparable> </xref:System.IComparable>  
  
## <a name="constraints"></a>Restrições  
 Embora o código em uma definição de tipo genérico deve ser tanto independente de tipo quanto possível, talvez seja necessário exigir uma determinada capacidade de qualquer tipo de dados fornecido para o tipo genérico. Por exemplo, se você quiser comparar dois itens com a finalidade de classificação ou ordenamento, seus tipos de dados devem implementar a <xref:System.IComparable>interface.</xref:System.IComparable> Você pode aplicar esse requisito adicionando uma *restrição* para o parâmetro de tipo.  
  
### <a name="example-of-a-constraint"></a>Exemplo de uma restrição  
 O exemplo a seguir mostra uma definição de uma classe com uma restrição que requer o argumento de tipo para implementar <xref:System.IComparable>.</xref:System.IComparable>  
  
 [!code-vb[VbVbalrDataTypes n º&5;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 Se o código subsequente tentar construir uma classe de `itemManager` fornecendo um tipo que não implementa <xref:System.IComparable>, o compilador sinaliza um erro.</xref:System.IComparable>  
  
### <a name="types-of-constraints"></a>Tipos de restrições  
 A restrição pode especificar os seguintes requisitos em qualquer combinação:  
  
-   O argumento de tipo deve implementar uma ou mais interfaces  
  
-   O argumento de tipo deve ser do tipo de, ou herdar de, no máximo uma classe  
  
-   O argumento de tipo deve expor um construtor sem parâmetros acessível para o código que cria objetos a partir dele  
  
-   O argumento de tipo deve ser um *tipo de referência*, ou deve ser um *tipo de valor*  
  
 Se você precisar impor mais de um requisito, use uma vírgula *lista de restrições* entre chaves (`{ }`). Para exigir um construtor acessível, você inclui o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave na lista. Para exigir um tipo de referência, inclua o `Class` palavra-chave; para exigir um tipo de valor, incluem o `Structure` palavra-chave.  
  
 Para obter mais informações sobre restrições, consulte [tipo lista](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Exemplo de várias restrições  
 O exemplo a seguir mostra uma definição de uma classe genérica com uma lista de restrição no parâmetro de tipo. No código que cria uma instância dessa classe, o argumento de tipo deve implementar o <xref:System.IComparable>e <xref:System.IDisposable>interfaces, ser um tipo de referência e expor um construtor sem parâmetros acessível.</xref:System.IDisposable> </xref:System.IComparable>  
  
 [!code-vb[VbVbalrDataTypes n º&6;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## <a name="important-terms"></a>Termos importantes  
 Tipos genéricos apresentam e usam os seguintes termos:  
  
-   *Tipo genérico*. Uma definição de classe, estrutura, interface, procedimento ou representante para o qual você fornece pelo menos um tipo de dados quando você declará-la.  
  
-   *Parâmetro de tipo*. Em uma definição de tipo genérico, um espaço reservado para um tipo de dados você fornece ao declarar o tipo.  
  
-   *O argumento de tipo*. Um tipo de dados específico que substitui um parâmetro de tipo quando você declara um tipo construído de um tipo genérico.  
  
-   *Restrição*. Uma condição em um parâmetro de tipo que restringe o argumento de tipo, você pode fornecer para ele. Uma restrição pode exigir que o argumento de tipo deve implementar uma interface específica, ser ou herdar de uma determinada classe, ter um construtor sem parâmetros acessível ou ser um tipo de referência ou um tipo de valor. Você pode combinar essas restrições, mas você pode especificar no máximo uma classe.  
  
-   *Tipo construído*. Uma classe, estrutura, interface, procedimento ou representante declarado de um tipo genérico fornecendo argumentos de tipo para seus parâmetros de tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [De](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Como](../../../../visual-basic/language-reference/statements/as-clause.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8)   
 [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
