---
title: Tipo de dados de objeto (Visual Basic)
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
ms.openlocfilehash: 94d3ddcf71194eb69a2d26bcdf549aaf693e46e6
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255700"
---
# <a name="object-data-type"></a>Tipo de dados Object
Contém os endereços que se referem a objetos. Você pode atribuir qualquer tipo de referência (cadeia de caracteres, matriz, classe ou interface) para um `Object` variável. Uma `Object` variável também pode consultar dados de qualquer tipo de valor (numérico, `Boolean`, `Char`, `Date`, estrutura, ou enumeração).  
  
## <a name="remarks"></a>Comentários  
 O `Object` tipo de dados pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância do objeto que seu aplicativo reconheça. Use `Object` quando você não souber em tempo de compilação qual tipo de dados a variável pode apontar.  
  
 O valor padrão de `Object` é `Nothing` (uma referência nula).  
  
## <a name="data-types"></a>Tipos de Dados  
 Você pode atribuir uma variável, constante ou expressão de qualquer tipo de dados para um `Object` variável. Para determinar o tipo de dados uma `Object` variável atualmente se refere, você pode usar o <xref:System.Type.GetTypeCode%2A> método o <xref:System.Type?displayProperty=nameWithType> classe. O exemplo a seguir ilustra essa situação.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 O `Object` tipo de dados é um tipo de referência. No entanto, o Visual Basic trata um `Object` variável como um tipo de valor quando ele se refere a dados de um tipo de valor.  
  
## <a name="storage"></a>Armazenamento  
 Qualquer tipo de dados que ele se refere, um `Object` variável não contém o valor dos dados em si, mas em vez disso, um ponteiro para o valor. Ela sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento de dados que representa o valor da variável. Por causa do código que usa o ponteiro para localizar os dados, `Object` variáveis mantendo os tipos de valor são um pouco mais lentas do que acessar explicitamente as variáveis digitadas.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, tenha em mente que os tipos de ponteiro em outros ambientes não são compatíveis com o Visual Basic `Object` tipo.  
  
-   **Desempenho.** Uma variável declarada com o `Object` tipo é flexível o suficiente para conter uma referência a qualquer objeto. No entanto, quando você invoca um método ou propriedade nesse tipo de variável, você sempre provoca *ligação tardia* (no tempo de execução). Para forçar *vinculação inicial* (no tempo de compilação) e um melhor desempenho, declare a variável com um nome de classe específica ou convertê-lo para o tipo de dados específico.  
  
     Quando você declara uma variável de objeto, tente usar um tipo de classe específica, por exemplo <xref:System.OperatingSystem>, em vez do generalizado `Object` tipo. Você também deve usar a classe mais específica disponível, como <xref:System.Windows.Forms.TextBox> em vez de <xref:System.Windows.Forms.Control>, de modo que você pode acessar suas propriedades e métodos. Normalmente, você pode usar o **Classes** lista o **Pesquisador de objetos** para localizar nomes de classe disponíveis.  
  
-   **Ampliação.** Todos os tipos de dados e todos os tipos de referência são ampliados com o `Object` tipo de dados. Isso significa que você pode converter qualquer tipo de `Object` sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
     No entanto, se você converter entre tipos de valor e `Object`, Visual Basic executa operações denominadas *boxing* e *unboxing*, que tornam a execução mais lenta.  
  
-   **Caracteres de tipo.** `Object` não tem nenhum caractere de tipo literal ou um caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Object?displayProperty=nameWithType> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra um `Object` variável que aponta para uma instância do objeto.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Como determinar se dois objetos estão relacionados](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Como determinar se dois objetos são idênticos](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
