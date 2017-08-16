---
title: "Declarado características do elemento (Visual Basic) | Documentos do Microsoft"
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
- declared elements, lifetime
- access levels, declared elements
- declared elements, scope
- visibility, declared elements
- elements, programming
- scope, declared elements
- lifetime, declared elements
- declared elements, access level
- data types [Visual Basic], declared elements
- declared elements, visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
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
ms.openlocfilehash: cb03ab496fa141ea76e4faa19bc7dc0595def024
ms.lasthandoff: 03/13/2017

---
# <a name="declared-element-characteristics-visual-basic"></a>Características do elemento declarado (Visual Basic)
A *característica* de um elemento declarado é um aspecto do elemento que afeta como o código pode interagir com ele. Cada elemento declarado tem um ou mais das seguintes características associadas a ele:  
  
-   *Tipo de dados* — os valores de elemento pode conter, e como ela armazena esses valores. Para obter mais informações, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
-   *Tempo de vida* — o período de tempo de execução durante o qual o elemento está disponível para uso. Para obter mais informações, consulte [tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Escopo* — o conjunto de todos os códigos que podem se referir ao elemento sem qualificar seu nome. Para obter mais informações, consulte [como: controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Nível de acesso* — a permissão para o código fazer uso do elemento. Para obter mais informações, consulte [como: controlar a disponibilidade de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
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
|Evento|Não|Não|Sim|Sim|  
|Representante|Não|Não|Sim|Sim|  
  
 <sup>1</sup> escopo é às vezes referido como *visibilidade*.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Nomes de elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
