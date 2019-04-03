---
title: Herda de instrução (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 5ab90e44e2809c1e71d7f100970b7be73af4a732
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817091"
---
# <a name="inherits-statement"></a>Instrução Inherits
Faz com que a classe ou interface atual herde atributos, variáveis, propriedades, procedimentos e eventos de outra classe ou conjunto de interfaces.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`basetypenames`|Necessário. O nome da classe da qual essa classe deriva.<br /><br /> - ou -<br /><br /> Os nomes das interfaces da qual deriva dessa interface. Use vírgulas para separar vários nomes.|  
  
## <a name="remarks"></a>Comentários  
 Se usado, o `Inherits` instrução deve ser a primeira linha não está em branco, sem comentário em uma definição de classe ou interface. Você deve seguir imediatamente o `Class` ou `Interface` instrução.  
  
 Você pode usar `Inherits` somente em uma classe ou interface. Isso significa que o contexto da declaração para uma herança não pode ser um arquivo de origem, namespace, estrutura, módulo, procedimento ou bloco.  
  
## <a name="rules"></a>Regras  
  
-   **Herança de classe.** Se uma classe usa o `Inherits` instrução, você pode especificar apenas uma classe base.  
  
     Uma classe não pode herdar de uma classe aninhada dentro dele.  
  
-   **Herança de interface.** Se uma interface usa o `Inherits` instrução, você pode especificar uma ou mais interfaces base. Você pode herdar de duas interfaces, mesmo se cada um deles definir um membro com o mesmo nome. Se você fizer isso, o código de implementação deve usar a qualificação de nome para especificar qual membro que está implementando.  
  
     Uma interface não pode herdar de outra interface com um nível de acesso mais restritivo. Por exemplo, uma `Public` interface não pode herdar de um `Friend` interface.  
  
     Uma interface não pode herdar de uma interface aninhada dentro dele.  
  
 Um exemplo de herança de classe no .NET Framework é o <xref:System.ArgumentException> classe, que herda o <xref:System.SystemException> classe. Isso fornece ao <xref:System.ArgumentException> todas as propriedades pré-definidas e procedimentos exigidos por exceções de sistema, como o <xref:System.Exception.Message%2A> propriedade e o <xref:System.Exception.ToString%2A> método.  
  
 Um exemplo de herança de interface no .NET Framework é o <xref:System.Collections.ICollection> interface, que herda o <xref:System.Collections.IEnumerable> interface. Isso faz com que <xref:System.Collections.ICollection> para herdar a definição do enumerador necessário para percorrer uma coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Inherits` instrução para mostrar como uma classe chamada `thisClass` pode herdar todos os membros de uma classe base chamada `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a herança de várias interfaces.  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 Interface chamada `thisInterface` agora inclui todas as definições na <xref:System.IComparable>, <xref:System.IDisposable>, e <xref:System.IFormattable> interfaces membros herdados fornecem respectivamente para comparação de tipo específico de dois objetos, o liberando alocados a recursos e expressar o valor de um objeto como um `String`. Uma classe que implementa `thisInterface` deve implementar todos os membros de interface base.  
  
## <a name="see-also"></a>Consulte também

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
