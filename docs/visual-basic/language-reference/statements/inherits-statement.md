---
title: "Instrução Inherits | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Inherits
- Inherits
dev_langs:
- VB
helpviewer_keywords:
- Inherits statement
- Inherits statement, syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 80ca8a685d56ef263d15a7757e7f392b8ea802de
ms.lasthandoff: 03/13/2017

---
# <a name="inherits-statement"></a>Instrução Inherits
Faz com que a classe ou interface atual herde os atributos, variáveis, propriedades, procedimentos e eventos de outra classe ou conjunto de interfaces.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`basetypenames`|Necessário. O nome da classe da qual essa classe deriva.<br /><br /> -ou-<br /><br /> Os nomes das interfaces da qual esta interface deriva. Use vírgulas para separar vários nomes.|  
  
## <a name="remarks"></a>Comentários  
 Se usado, o `Inherits` instrução deve ser a primeira linha não vazia e que não seja de comentários em uma definição de classe ou interface. Você deve seguir imediatamente o `Class` ou `Interface` instrução.  
  
 Você pode usar `Inherits` somente em uma classe ou interface. Isso significa que o contexto da declaração para uma herança não pode ser um arquivo fonte, namespace, estrutura, módulo, procedimento ou bloco.  
  
## <a name="rules"></a>Regras  
  
-   **Herança de classe.** Se uma classe usa a `Inherits` instrução, você pode especificar apenas uma classe base.  
  
     Uma classe não pode herdar de uma classe aninhada nela.  
  
-   **Herança da interface.** Se uma interface usa a `Inherits` instrução, você pode especificar uma ou mais interfaces base. Você pode herdar de duas interfaces mesmo se cada uma define um membro com o mesmo nome. Se você fizer isso, o código de implementação deve usar a qualificação de nome para especificar qual membro que está implementando.  
  
     Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo. Por exemplo, um `Public` interface não pode herdar de um `Friend` interface.  
  
     Uma interface não pode herdar de uma interface aninhada nela.  
  
 Um exemplo de herança de classe no .NET Framework é a <xref:System.ArgumentException>classe que herde a <xref:System.SystemException>classe.</xref:System.SystemException> </xref:System.ArgumentException> Isso fornece ao <xref:System.ArgumentException>todas as propriedades predefinidas e procedimentos exigidos por exceções de sistema, como o <xref:System.Exception.Message%2A>propriedade e o <xref:System.Exception.ToString%2A>método.</xref:System.Exception.ToString%2A> </xref:System.Exception.Message%2A> </xref:System.ArgumentException>  
  
 Um exemplo de herança de interface no .NET Framework é o <xref:System.Collections.ICollection>interface, que herda o <xref:System.Collections.IEnumerable>interface.</xref:System.Collections.IEnumerable> </xref:System.Collections.ICollection> Isso faz com que <xref:System.Collections.ICollection>herde a definição do enumerador necessário para percorrer uma coleção.</xref:System.Collections.ICollection>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Inherits` instrução para mostrar como uma classe chamada `thisClass` pode herdar todos os membros de uma classe base chamada `anotherClass`.  
  
 [!code-vb[VbVbalrStatements&#37;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a herança de várias interfaces.  
  
 [!code-vb[VbVbalrStatements&38;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 A interface denominada `thisInterface` inclui agora todas as definições no <xref:System.IComparable>, <xref:System.IDisposable>, e <xref:System.IFormattable>interfaces membros herdados oferecem respectivamente para comparação de tipo específico de dois objetos, liberando recursos alocados e expressar o valor de um objeto como um `String`.</xref:System.IFormattable> </xref:System.IDisposable> </xref:System.IComparable> Uma classe que implementa `thisInterface` deve implementar todo membro de interface base.  
  
## <a name="see-also"></a>Consulte também  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Noções básicas sobre herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
