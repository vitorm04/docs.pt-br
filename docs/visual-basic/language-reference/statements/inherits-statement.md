---
title: Instrução Inherits
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 6e6e9cc9210232059210862f2bda691c57b372d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353233"
---
# <a name="inherits-statement"></a>Instrução Inherits
Faz com que a classe ou a interface atual herde os atributos, variáveis, propriedades, procedimentos e eventos de outra classe ou conjunto de interfaces.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`basetypenames`|Necessária. O nome da classe da qual essa classe deriva.<br /><br /> - ou -<br /><br /> Os nomes das interfaces das quais essa interface deriva. Use vírgulas para separar vários nomes.|  
  
## <a name="remarks"></a>Comentários  
 Se usado, a instrução `Inherits` deve ser a primeira linha não em branco, que não seja de comentário em uma definição de classe ou de interface. Ele deve seguir imediatamente a instrução `Class` ou `Interface`.  
  
 Você pode usar `Inherits` apenas em uma classe ou interface. Isso significa que o contexto de declaração para uma herança não pode ser um arquivo de origem, namespace, estrutura, módulo, procedimento ou bloco.  
  
## <a name="rules"></a>Regras  
  
- **Herança de classe.** Se uma classe usar a instrução `Inherits`, você poderá especificar apenas uma classe base.  
  
     Uma classe não pode herdar de uma classe aninhada dentro dela.  
  
- **Herança de interface.** Se uma interface usar a instrução `Inherits`, você poderá especificar uma ou mais interfaces base. Você pode herdar de duas interfaces, mesmo se cada uma delas definir um membro com o mesmo nome. Se você fizer isso, o código de implementação deverá usar a qualificação de nome para especificar qual membro está sendo implementado.  
  
     Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo. Por exemplo, uma interface `Public` não pode herdar de uma interface `Friend`.  
  
     Uma interface não pode herdar de uma interface aninhada dentro dela.  
  
 Um exemplo de herança de classe no .NET Framework é a classe <xref:System.ArgumentException>, que é herdada da classe <xref:System.SystemException>. Isso fornece a <xref:System.ArgumentException> todas as propriedades predefinidas e os procedimentos exigidos pelas exceções do sistema, como a propriedade <xref:System.Exception.Message%2A> e o método <xref:System.Exception.ToString%2A>.  
  
 Um exemplo de herança de interface no .NET Framework é a interface <xref:System.Collections.ICollection>, que é herdada da interface <xref:System.Collections.IEnumerable>. Isso faz com que <xref:System.Collections.ICollection> herdem a definição do enumerador necessário para atravessar uma coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Inherits` para mostrar como uma classe denominada `thisClass` pode herdar todos os membros de uma classe base denominada `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a herança de várias interfaces.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 A interface chamada `thisInterface` agora inclui todas as definições nas interfaces <xref:System.IComparable>, <xref:System.IDisposable>e <xref:System.IFormattable>. os membros herdados fornecem, respectivamente, a comparação específica de tipo de dois objetos, liberando recursos alocados e expressando o valor de um objeto como um `String`. Uma classe que implementa `thisInterface` deve implementar todos os membros de cada interface base.  
  
## <a name="see-also"></a>Consulte também

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
