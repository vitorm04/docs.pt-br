---
title: Tipo ou Namespace especificado em Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t contém nenhum membro público ou não foi encontrado
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8be0df5cbe4b8d4a640c9b6c2e126b3828254fd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Tipo ou Namespace especificado em Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t contém nenhum membro público ou não foi encontrado
Tipo ou Namespace especificado em Imports'\<qualifiedelementname >' não contém nenhum membro público ou não pode ser encontrado. Verifique se o namespace ou o tipo está definido e contém pelo menos um membro público. Verifique se que o nome do alias não contém outros aliases.  
  
 Um `Imports` instrução Especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.  
  
 Um *que contém o elemento* pode ser um namespace, classe, estrutura, interface, módulo ou enumeração. O elemento contido contém membros, como variáveis, procedimentos ou outros elementos contidos.  
  
 A finalidade de importação é permitir que seu código para acessar membros de namespace ou tipo sem precisar qualificá-los. Seu projeto talvez seja necessário também adicionar uma referência para o namespace ou tipo. Para obter mais informações, consulte "Importação que contém elementos" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não pode localizar o elemento contido, ele não pode resolver referências que o usam. Se encontrar o elemento, mas o elemento não expõe nenhum `Public` membros e, em seguida, nenhuma referência pode ser bem-sucedida. Em ambos os casos não faz sentido para o elemento de importação.  
  
 Tenha em mente que se você importa um elemento de contêiner e atribuir um alias de importação para ele, em seguida, você não pode usar esse alias de importação para importar de outro elemento. O código a seguir gera um erro do compilador.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **ID do erro:** BC40056  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o elemento contêiner está acessível do seu projeto.  
  
2.  Verifique se que a especificação de um elemento que o contém não inclui qualquer alias de importação de importação de outra.  
  
3.  Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Público](../../../visual-basic/language-reference/modifiers/public.md)  
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
