---
title: Tipo de dados Object (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 1ac906494c49810e3d389591b1044f412e7320bc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513045"
---
# <a name="object-data-type"></a>Tipo de dados Object

Contém endereços que se referem a objetos. Você pode atribuir qualquer tipo de referência (cadeia de caracteres, matriz, classe ou interface) `Object` a uma variável. Uma `Object` variável também pode se referir a dados de qualquer tipo de valor `Boolean`(numérico `Date`,, `Char`,, estrutura ou Enumeração).

## <a name="remarks"></a>Comentários

O `Object` tipo de dados pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância de objeto que seu aplicativo reconhece. Use `Object` quando você não souber em tempo de compilação a qual tipo de dados a variável pode apontar.

O valor padrão de `Object` é `Nothing` (uma referência nula).

## <a name="data-types"></a>Tipos de Dados

Você pode atribuir uma variável, constante ou expressão de qualquer tipo de dados a uma `Object` variável. Para determinar o tipo de dados `Object` ao qual uma variável se refere atualmente, você <xref:System.Type.GetTypeCode%2A> pode usar o <xref:System.Type?displayProperty=nameWithType> método da classe. O exemplo a seguir ilustra essa situação.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

O `Object` tipo de dados é um tipo de referência. No entanto, Visual Basic `Object` trata uma variável como um tipo de valor quando se refere aos dados de um tipo de valor.

## <a name="storage"></a>Armazenamento

Qualquer tipo de dados ao qual se refere `Object` , uma variável não contém o próprio valor de dados, mas sim um ponteiro para o valor. Ele sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento para os dados que representam o valor da variável. Devido ao código que usa o ponteiro para localizar os dados, `Object` as variáveis que mantêm os tipos de valor são um pouco mais lentas para acessar do que as variáveis explicitamente digitadas.

## <a name="programming-tips"></a>Dicas de programação

- **Considerações sobre interoperabilidade.** Se você estiver fazendo a interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos com, tenha em mente que os tipos de ponteiro em outros ambientes não são `Object` compatíveis com o tipo de Visual Basic.

- **Desempenho.** Uma variável que você declara com `Object` o tipo é flexível o suficiente para conter uma referência a qualquer objeto. No entanto, quando você invoca um método ou propriedade em tal variável, sempre ocorre a *ligação tardia* (em tempo de execução). Para forçar a *ligação antecipada* (no momento da compilação) e melhorar o desempenho, declare a variável com um nome de classe específico ou converta-a para o tipo de dados específico.

  Ao declarar uma variável de objeto, tente usar um tipo de classe específico, por exemplo <xref:System.OperatingSystem>, em vez do `Object` tipo generalizado. Você também deve usar a classe mais específica disponível, <xref:System.Windows.Forms.TextBox> como em vez de <xref:System.Windows.Forms.Control>, para que você possa acessar suas propriedades e métodos. Normalmente, você pode usar a lista de **classes** no Pesquisador de **objetos** para localizar os nomes de classe disponíveis.

- **Ampliação.** Todos os tipos de dados e todos os tipos de `Object` referência ampliam para o tipo de dados. Isso significa que você pode converter qualquer tipo `Object` para sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.

  No entanto, se você converter entre tipos `Object`de valor e, Visual Basic executar operações chamadas *Boxing* e unboxing, o que torna a execução mais lenta.

- **Digite os caracteres.** `Object`Não tem caractere de tipo literal ou caractere de tipo de identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a <xref:System.Object?displayProperty=nameWithType> classe.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra `Object` uma variável que aponta para uma instância de objeto.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>Consulte também

- <xref:System.Object>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Como: Determinar se dois objetos estão relacionados](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Como: Determinar se dois objetos são idênticos](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
