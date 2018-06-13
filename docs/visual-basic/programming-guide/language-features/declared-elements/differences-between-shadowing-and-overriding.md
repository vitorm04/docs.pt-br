---
title: Diferenças entre sombreamento e sobreposição (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 94ce3e7fe25b7942730e6e89a53654b03d91c42b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649627"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Diferenças entre sombreamento e sobreposição (Visual Basic)
Quando você define uma classe que herda de uma classe base, às vezes você deseja redefinir um ou mais dos elementos de classe base na classe derivada. Sombreamento e sobreposição estão disponíveis para essa finalidade.  
  
## <a name="comparison"></a>Comparação  
 Sombreamento e sobreposição forem usadas quando uma classe derivada herda de uma classe base e os dois redefinem um elemento declarado com outro. Mas há diferenças significativas entre os dois.  
  
 A tabela a seguir compara sombreamento com substituição.  
  
||||  
|---|---|---|  
|Ponto de comparação|Sombreamento|Substituindo|  
|Finalidade|Protege contra uma modificação subsequente de classe base que introduz um membro que você já tenha definido em sua classe derivada|Permite polimorfismo através da definição de uma implementação de um procedimento ou propriedade com a mesma sequência de chamada<sup>1</sup>|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento (`Function`, `Sub`, ou `Operator`) ou propriedade|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento ou propriedade com a sequência de chamada idêntica<sup>1</sup>|  
|Nível de acesso do elemento redefinido|Qualquer nível de acesso|Não é possível alterar o nível de acesso do elemento substituído|  
|Legibilidade de gravabilidade do elemento redefinido|Qualquer combinação|Não é possível alterar a legibilidade ou gravabilidade de propriedade substituída|  
|Controle da redefinição|Elemento de classe base não pode forçar ou proibir sombreamento|Elemento de classe base pode especificar `MustOverride`, `NotOverridable`, ou `Overridable`|  
|Uso da palavra-chave|`Shadows` recomendado na classe derivada; `Shadows` pressuposto se nenhum `Shadows` nem `Overrides` especificado<sup>2</sup>|`Overridable` ou `MustOverride` necessário na classe base. `Overrides` necessário na classe derivada|  
|Herança do elemento redefinido em classes derivadas da classe derivada|Sombreamento de elemento herdado por futuras classes derivadas; elemento sombreado ainda ocultado<sup>3</sup>|Substituir o elemento herdado por futuras classes derivadas; elemento sobrescrito ainda sobrescrito|  
  
 <sup>1</sup> o *sequência de chamada* consiste em tipo de elemento (`Function`, `Sub`, `Operator`, ou `Property`), nome, listas de parâmetros e tipo de retorno. Você não pode substituir um procedimento com uma propriedade ou o oposto. Você não pode substituir um tipo de procedimento (`Function`, `Sub`, ou `Operator`) com outro tipo.  
  
 <sup>2</sup> se você não especificar um `Shadows` ou `Overrides`, o compilador emite uma mensagem de aviso para ajudá-lo a não se esqueça de que tipo de redefinição que você deseja usar. Se você ignorar o aviso, o mecanismo de sombreamento é usado.  
  
 <sup>3</sup> se o elemento sombreador é inacessível em uma classe derivada adicional, sombreamento não é herdado. Por exemplo, se você declarar o elemento sombreador como `Private`, uma classe derivando de sua classe derivada herda o elemento original em vez do elemento de sombreamento.  
  
## <a name="guidelines"></a>Diretrizes  
 Você normalmente usa sobrescrição nos seguintes casos:  
  
-   Você está definindo classes derivadas polimórficas.  
  
-   Você deseja que a segurança de fazer o compilador forçar o mesmo tipo de elemento e a sequência de chamada.  
  
 Você normalmente usa sombreamento nos seguintes casos:  
  
-   Você prevê que sua classe base pode ser modificada e define um elemento usando o mesmo nome que o seu.  
  
-   Você deseja ter a liberdade de alterar o tipo de elemento ou sequência de chamada.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Como ocultar uma variável com o mesmo nome que a variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Como ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Como acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)
