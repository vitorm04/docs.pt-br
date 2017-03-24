---
title: Sobrecargas (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Overloads
- Overloads
dev_langs:
- VB
helpviewer_keywords:
- Overloads keyword
- hiding by signature
- Shadows keyword
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
caps.latest.revision: 15
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
ms.openlocfilehash: 8f17c1f014065a5bebb47935e37ed71d498cc407
ms.lasthandoff: 03/13/2017

---
# <a name="overloads-visual-basic"></a>Sobrecargas (Visual Basic)
Especifica que uma propriedade ou procedimento declara novamente uma ou mais propriedades ou procedimentos existentes com o mesmo nome.  
  
## <a name="remarks"></a>Comentários  
 *Sobrecarga* é a prática de fornecer mais de uma definição para um determinado nome de propriedade ou procedimento no mesmo escopo. Declarar novamente um propriedade ou procedimento com uma assinatura diferente às vezes é chamado *ocultação por assinatura*.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Overloads` somente na declaração de uma propriedade ou um procedimento.  
  
-   **Modificadores combinados.** Não é possível especificar `Overloads` junto com [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) na mesma declaração de procedimento.  
  
-   **Diferenças requeridas.** O *assinatura* nessa declaração deve ser diferente da assinatura de toda propriedade ou procedimento que ela sobrecarrega. A assinatura inclui o nome de propriedade ou procedimento junto com o seguinte:  
  
    -   o número de parâmetros  
  
    -   a ordem dos parâmetros  
  
    -   os tipos de dados dos parâmetros  
  
    -   o número de parâmetros de tipo (para um procedimento genérico)  
  
    -   o tipo de retorno (somente para um procedimento de operador de conversão)  
  
     Todas as sobrecargas devem ter o mesmo nome, mas cada uma deve diferir de todas as outras em uma ou mais dentre as condições citadas. Isso permite que o compilador distinguir qual versão usar quando o código chama o procedimento ou propriedade.  
  
-   **Diferenças não permitidas.** Alterar um ou mais dos procedimentos a seguir não é válido para sobrecarga de propriedade ou procedimento, porque eles não fazem parte da assinatura:  
  
    -   Se ele retorna um valor (para um procedimento)  
  
    -   o tipo de dados do valor de retorno (exceto para um operador de conversão)  
  
    -   os nomes dos parâmetros ou parâmetros de tipo  
  
    -   as restrições nos parâmetros do tipo (para um procedimento genérico)  
  
    -   palavras-chave de modificador de parâmetro (como `ByRef` ou `Optional`)  
  
    -   palavras-chave modificadores de propriedade ou um procedimento (como `Public` ou `Shared`)  
  
-   **Modificador opcional.** Você não precisa usar o `Overloads` modificador quando você está definindo várias propriedades ou procedimentos sobrecarregados na mesma classe. No entanto, se você usar `Overloads` em uma das declarações, você deve usá-lo em todas elas.  
  
-   **Sombreamento e sobrecarga.** `Overloads`também pode ser usado para sombrear um membro existente, ou conjunto de membros sobrecarregados, em uma classe base. Quando você usa `Overloads` dessa forma, você declara a propriedade ou método com o mesmo nome e a mesma lista de parâmetros como membro da classe base, e você não fornecer o `Shadows` palavra-chave.  
  
 Se você usar `Overrides`, o compilador adiciona implicitamente `Overloads` para que sua biblioteca de APIs trabalhar mais facilmente com o c#.  
  
 O `Overloads` modificador pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
