---
title: "Como: Declarar enumerações (Visual Basic) | Documentos do Microsoft"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
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
ms.openlocfilehash: 8ff8bf2df39bed0597740bcda968283ec854f447
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a>Como declarar enumerações (Visual Basic)
Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou módulo. Você não pode declarar uma enumeração dentro de um método. Para especificar o nível apropriado de acesso, use `Private`, `Protected`, `Friend`, ou `Public`.  
  
 Um `Enum` tipo tem um nome, um tipo subjacente e um conjunto de campos, cada um representando uma constante. O nome deve ser válido [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualificador. O tipo subjacente deve ser um dos tipos inteiros —`Byte`, `Short`, `Long` ou `Integer`. `Integer` é o padrão. Enumerações são sempre fortemente tipadas e não são intercambiáveis com tipos de número inteiro.  
  
 Enumerações não podem ter valores de ponto flutuante. Se uma enumeração é atribuída um valor de ponto flutuante com `Option Strict On`, um erro de compilação acontece. Se `Option Strict` é `Off`, o valor é convertido automaticamente para o `Enum` tipo.  
  
 Para obter informações sobre nomes e como usar o `Imports` instrução para tornar a qualificação de nome desnecessário, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Para declarar uma enumeração  
  
1.  Escrever uma declaração que inclua um nível de acesso de código, o `Enum` palavra-chave e um nome válido, como os exemplos a seguir, cada uma das quais declara um outro `Enum`.  
  
     [!code-vb[VbEnumsTask n º&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Defina as constantes na enumeração. Por padrão, a primeira constante em uma enumeração é inicializada para `0`, e constantes subsequentes são inicializados com um valor de um mais do que a constante anterior. Por exemplo, a enumeração seguir `Days`, contém uma constante chamada `Sunday` com o valor `0`, uma constante chamada `Monday` com o valor `1`, uma constante chamada `Tuesday` com o valor de `2`, e assim por diante.  
  
     [!code-vb[VbEnumsTask n º&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Você pode explicitamente atribuir valores às constantes em uma enumeração usando uma instrução de atribuição. Você pode atribuir qualquer valor inteiro, incluindo os números negativos. Por exemplo, convém constantes com valores menores que zero para representar condições de erro. Na enumeração seguir, a constante `Invalid` explicitamente é atribuído o valor `–1`e a constante `Sunday` é atribuído o valor `0`. Porque é a primeira constante na enumeração, `Saturday` também é inicializada com o valor `0`. O valor de `Monday` é `1` (mais do que o valor de `Sunday`); o valor de `Tuesday` é `2`, e assim por diante.  
  
     [!code-vb[VbEnumsTask n º&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Para declarar uma enumeração como um tipo explícito  
  
-   Especifique o tipo de enumeração usando o `As` cláusula, conforme mostrado no exemplo a seguir.  
  
     [!code-vb[VbEnumsTask n º&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Tipos de dados constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
