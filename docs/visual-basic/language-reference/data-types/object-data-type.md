---
title: Tipo de dados do objeto | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Object
- vb.Variant
dev_langs:
- VB
helpviewer_keywords:
- object variables, Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type, reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: db26082709f6b3a8278d20f4ade68e10f46839de
ms.lasthandoff: 03/13/2017

---
# <a name="object-data-type"></a>Tipo de dados Object
Contém os endereços que se referem a objetos. Você pode atribuir qualquer tipo de referência (string, array, classe ou interface) para um `Object` variável. Um `Object` variável também pode se referir aos dados de qualquer tipo de valor (numérico, `Boolean`, `Char`, `Date`, estrutura, ou enumeração).  
  
## <a name="remarks"></a>Comentários  
 O `Object` tipo de dados pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância do objeto aplicativo reconhece. Use `Object` quando você não souber em tempo de compilação qual tipo de dados a variável pode apontar.  
  
 O valor padrão de `Object` é `Nothing` (uma referência nula).  
  
## <a name="data-types"></a>Tipos de Dados  
 Você pode atribuir uma variável, uma constante ou uma expressão de qualquer tipo de dados para um `Object` variável. Para determinar o tipo de dados um `Object` variável atualmente se refere, você pode usar o <xref:System.Type.GetTypeCode%2A>método de <xref:System.Type?displayProperty=fullName>classe.</xref:System.Type?displayProperty=fullName> </xref:System.Type.GetTypeCode%2A> O exemplo a seguir ilustra essa situação.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 O `Object` é um tipo de referência. No entanto, o Visual Basic trata uma `Object` variável como um tipo de valor quando ela se refere aos dados de um tipo de valor.  
  
## <a name="storage"></a>Armazenamento  
 Qualquer tipo de dados que ela se refere, uma `Object` variável não contém o valor dos dados em si, mas em vez disso, um ponteiro para o valor. Ela sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento de dados que representa o valor da variável. Por causa do código que usa o ponteiro para localizar os dados, `Object` variáveis contém tipos de valor são um pouco mais lentas para acesso do que explicitamente variáveis digitadas.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos de ponteiro em outros ambientes não são compatíveis com o Visual Basic `Object` tipo.  
  
-   **Desempenho.** Uma variável declarada com o `Object` tipo é flexível o suficiente para conter uma referência a qualquer objeto. No entanto, quando você invoca um método ou propriedade nesse tipo de variável, você sempre provoca *ligação tardia* (em tempo de execução). Para forçar o *vinculação inicial* (em tempo de compilação) e um melhor desempenho, declarar a variável com um nome de classe específico ou convertê-lo para o tipo de dados específico.  
  
     Quando você declarar uma variável de objeto, tente usar um tipo de classe específico, por exemplo <xref:System.OperatingSystem>, em vez de generalizada `Object` tipo.</xref:System.OperatingSystem> Você também deve usar a classe mais específica disponível, tais como <xref:System.Windows.Forms.TextBox>em vez de <xref:System.Windows.Forms.Control>, de modo que você pode acessar suas propriedades e métodos.</xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.TextBox> Você pode usar o **Classes** lista no **Pesquisador de objetos** para localizar nomes de classe disponíveis.  
  
-   **Ampliação.** Todos os tipos de dados e todos os tipos de referência ampliam-se para o `Object` tipo de dados. Isso significa que você pode converter qualquer tipo de `Object` sem encontrar uma <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
     No entanto, se você converter entre tipos de valor e `Object`, Visual Basic executa operações chamadas *conversão boxing* e *unboxing*, que tornam a execução mais lenta.  
  
-   **Caracteres de tipo.** `Object`não possui caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a <xref:System.Object?displayProperty=fullName>classe.</xref:System.Object?displayProperty=fullName>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra um `Object` variável que aponta para uma instância do objeto.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object></xref:System.Object>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Como: determinar se dois objetos estão relacionados](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Como determinar se dois objetos são idênticos](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
