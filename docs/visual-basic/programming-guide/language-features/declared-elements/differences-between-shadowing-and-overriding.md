---
title: Diferenças entre sombreamento e sobreposição (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: b935184f0e4d0378bfea69811aa4e6c068a9776f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827920"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Diferenças entre sombreamento e sobreposição (Visual Basic)
Quando você define uma classe que herda de uma classe base, às vezes você deseja redefinir uma ou mais dos elementos de classe base na classe derivada. Sombreamento e sobreposição estão disponíveis para essa finalidade.  
  
## <a name="comparison"></a>Comparação  
 Sombreamento e sobreposição forem usadas quando uma classe derivada herda de uma classe base e os dois redefinem um elemento declarado com outro. Mas há diferenças significativas entre os dois.  
  
 A tabela a seguir compara sombreamento com substituição.  
  
||||  
|---|---|---|  
|Ponto de comparação|Sombreamento|Substituindo|  
|Finalidade|Protege contra uma modificação posterior de classe base que introduz um membro que você já definiu na sua classe derivada|Permite polimorfismo através da definição de uma implementação de um procedimento ou propriedade com a mesma sequência de chamada<sup>1</sup>|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento (`Function`, `Sub`, ou `Operator`) ou propriedade|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento ou propriedade com a sequência de chamada idêntica<sup>1</sup>|  
|Nível de acesso do elemento redefinido|Qualquer nível de acesso|Não é possível alterar o nível de acesso do elemento substituído|  
|A leitura e gravação do elemento redefinido|Qualquer combinação|Não é possível alterar a legibilidade ou a gravação de propriedade substituída|  
|Controle da redefinição|Elemento de classe base não pode forçar ou proibir sombreamento|Elemento de classe base pode especificar `MustOverride`, `NotOverridable`, ou `Overridable`|  
|Uso da palavra-chave|`Shadows` recomendado na classe derivada; `Shadows` pressuposto se nenhum dos dois `Shadows` nem `Overrides` especificado<sup>2</sup>|`Overridable` ou `MustOverride` necessário na classe base; `Overrides` necessário na classe derivada|  
|Herança do elemento redefinido em classes derivadas de sua classe derivada|Sombreamento elemento herdado por futuras classes derivadas; elemento sombreado ainda ocultado<sup>3</sup>|Substituir o elemento herdado por futuras classes derivadas; elemento sobrescrito ainda sobrescrito|  
  
 <sup>1</sup> as *sequência de chamada* consiste em tipo de elemento (`Function`, `Sub`, `Operator`, ou `Property`), nome, a lista de parâmetros e o tipo de retorno. Você não pode substituir um procedimento com uma propriedade ou o oposto. Você não pode substituir um tipo de procedimento (`Function`, `Sub`, ou `Operator`) com outro tipo.  
  
 <sup>2</sup> caso você não especifique `Shadows` ou `Overrides`, o compilador emite uma mensagem de aviso para ajudá-lo a não se esqueça de que tipo de redefinição que você deseja usar. Se você ignorar o aviso, o mecanismo de sombreamento é usado.  
  
 <sup>3</sup> se o elemento sombreador é inacessível em uma classe derivada ainda mais, sombreamento não é herdado. Por exemplo, se você declarar o elemento sombreador como `Private`, uma classe derivada da classe derivada herda o elemento original em vez do elemento de sombreamento.  
  
## <a name="guidelines"></a>Diretrizes  
 Você normalmente usa substituindo nos seguintes casos:  
  
-   Você está definindo classes derivadas polimórficas.  
  
-   Você deseja que a segurança de fazer com que o compilador impor o mesmo tipo de elemento e a sequência de chamada.  
  
 Você normalmente usa sombreamento nos seguintes casos:  
  
-   Você prevê que sua classe base pode ser modificado e define um elemento usando o mesmo nome que o seu.  
  
-   Você quer a liberdade de alterar o tipo de elemento ou sequência de chamada.  
  
## <a name="see-also"></a>Consulte também

- [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Como: Ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Como: Ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Como: Acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)
