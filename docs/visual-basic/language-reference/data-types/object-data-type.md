---
title: Tipo de dados Object
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 847f2b50296ad1a1ba6f0009d1d6afced27f9abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-data-type"></a>Tipo de dados Object
Contém os endereços que se referem a objetos. Você pode atribuir qualquer tipo de referência (cadeia de caracteres, matriz, classe ou interface) para um `Object` variável. Um `Object` variável também pode referir-se aos dados de qualquer tipo de valor (numérico, `Boolean`, `Char`, `Date`, estrutura, ou enumeração).  
  
## <a name="remarks"></a>Comentários  
 O `Object` tipo de dados pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância do objeto aplicativo reconhece. Use `Object` quando você não souber em tempo de compilação qual tipo de dados a variável pode apontar.  
  
 O valor padrão de `Object` é `Nothing` (uma referência nula).  
  
## <a name="data-types"></a>Tipos de Dados  
 Você pode atribuir uma variável, constante ou expressão de qualquer tipo de dados para um `Object` variável. Para determinar o tipo de dados um `Object` variável atualmente se refere a, você pode usar o <xref:System.Type.GetTypeCode%2A> método o <xref:System.Type?displayProperty=nameWithType> classe. O exemplo a seguir ilustra essa situação.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 O `Object` tipo de dados é um tipo de referência. No entanto, o Visual Basic trata um `Object` variável como um tipo de valor quando ela se refere aos dados de um tipo de valor.  
  
## <a name="storage"></a>Armazenamento  
 Qualquer tipo de dados que se refere a um `Object` variável não contém o valor dos dados em si, mas em vez disso, um ponteiro para o valor. Ele sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento de dados que representa o valor da variável. Por causa do código que usa o ponteiro para localizar os dados, `Object` variáveis, mantendo os tipos de valor são um pouco mais lentas para acesso do que explicitamente variáveis digitadas.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos de ponteiro em outros ambientes não são compatíveis com o Visual Basic `Object` tipo.  
  
-   **Desempenho.** Uma variável declarada com o `Object` tipo é flexível o suficiente para conter uma referência a qualquer objeto. No entanto, quando você invoca um método ou propriedade nesse tipo de variável, você sempre provoca *associação tardia* (tempo de execução). Para forçar *associação inicial* (em tempo de compilação) e melhor desempenho, declare a variável com um nome de classe específica ou converta-a para o tipo de dados específico.  
  
     Quando você declara uma variável de objeto, tente usar um tipo de classe específica, por exemplo <xref:System.OperatingSystem>, em vez de generalizado `Object` tipo. Você também deve usar a classe mais específica disponível, como <xref:System.Windows.Forms.TextBox> em vez de <xref:System.Windows.Forms.Control>, de modo que você pode acessar suas propriedades e métodos. Normalmente, você pode usar o **Classes** lista o **Pesquisador de objetos** para localizar nomes de classe disponíveis.  
  
-   **Ampliação.** Ampliam a todos os tipos de dados e todos os tipos de referência para o `Object` tipo de dados. Isso significa que você pode converter qualquer tipo de `Object` sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
     No entanto, se você converter entre tipos de valor e `Object`, Visual Basic executa operações chamadas *boxing* e *unboxing*, que tornam a execução mais lenta.  
  
-   **Caracteres de tipo.** `Object`não tem o caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente do .NET Framework é o <xref:System.Object?displayProperty=nameWithType> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra um `Object` variável aponta para uma instância do objeto.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Como determinar se dois objetos estão relacionados](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Como determinar se dois objetos são idênticos](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
