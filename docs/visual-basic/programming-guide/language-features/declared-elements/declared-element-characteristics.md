---
title: Características do elemento declarado (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 98f6a7738a462e9f36abdc0380cb1fe8d488fb9d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821290"
---
# <a name="declared-element-characteristics-visual-basic"></a>Características do elemento declarado (Visual Basic)
Um *característica* de um elemento declarado é um aspecto do elemento que afeta como o código pode interagir com ele. Cada elemento declarado tem um ou mais das seguintes características associadas a ele:  
  
-   *Tipo de dados* — os valores de elemento pode conter e como ela armazena esses valores. Para obter mais informações, veja [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md).  
  
-   *Tempo de vida* — o período de tempo de execução durante o qual o elemento está disponível para uso. Para obter mais informações, consulte [tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Escopo* — o conjunto de todo o código que pode se referir ao elemento sem qualificar seu nome. Para obter mais informações, confira [Como: Controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Nível de acesso* — a permissão para o código fazer uso do elemento. Para obter mais informações, confira [Como: Controlar a disponibilidade de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Características dos elementos  
 A tabela a seguir mostra os elementos declarados e as características que se aplicam a cada um deles.  
  
|Elemento|Tipo de dados|Tempo de vida|Escopo <sup>1</sup>|Nível de acesso|  
|-------------|---------------|--------------|------------------------|------------------|  
|Variável|Sim|Sim|Sim|Sim|  
|Constante|Sim|Não|Sim|Sim|  
|Enumeração|Sim|Não|Sim|Sim|  
|Estrutura|Não|Não|Sim|Sim|  
|Propriedade|Sim|Sim|Sim|Sim|  
|Método|Não|Sim|Sim|Sim|  
|Procedimento (`Sub` ou `Function`)|Não|Sim|Sim|Sim|  
|Parâmetro de procedimento|Sim|Sim|Sim|Não|  
|Retorno de função|Sim|Sim|Sim|Não|  
|Operador|Sim|Não|Sim|Sim|  
|Interface|Não|Não|Sim|Sim|  
|Classe|Não|Não|Sim|Sim|  
|evento|Não|Não|Sim|Sim|  
|delegado|Não|Não|Sim|Sim|  
  
 <sup>1</sup> escopo às vezes é conhecido como *visibilidade*.  
  
## <a name="see-also"></a>Consulte também

- [Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
