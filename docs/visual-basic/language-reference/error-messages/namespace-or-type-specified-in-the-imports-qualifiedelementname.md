---
title: O namespace ou o tipo especificado em Imports '<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: d19a769b33b3b63b7f431b73841f49632e41f9e6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288269"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Tipo ou Namespace especificado em Imports'\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado
Tipo ou Namespace especificado em Imports'\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado. Verifique se o namespace ou o tipo é definido e contém pelo menos um membro público. Verifique se que o nome do alias não contém outros aliases.  
  
 Uma `Imports` declaração especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.  
  
 Um *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração. O elemento contido contém membros, como variáveis, procedimentos ou outros elementos que contém.  
  
 A finalidade de importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los. Seu projeto talvez seja necessário também adicionar uma referência para o namespace ou tipo. Para obter mais informações, consulte "Importação de elementos que contém" na [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não pode localizar o elemento contido, ele não é possível resolver as referências que usá-lo. Se ele localiza o elemento, mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida. Em ambos os casos não faz sentido para o elemento de importação.  
  
 Tenha em mente que se você importar um elemento de recipiente e atribuir um alias de importação para ele, em seguida, é possível usar esse alias de importação para importar de outro elemento. O código a seguir gera um erro do compilador.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **ID do erro:** BC40056  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o elemento que o contém é acessível a partir de seu projeto.  
  
2.  Verifique se que a especificação do elemento contido não inclui qualquer alias de importação da importação de outro.  
  
3.  Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Público](../../../visual-basic/language-reference/modifiers/public.md)
- [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
