---
title: O namespace ou o tipo especificado no nível de projeto Imports '<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado.
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 12d20a88179a3d0c93c18f0aed65ca46b001059a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283303"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Namespace ou tipo especificado no nível de projeto Imports '\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado
Namespace ou tipo especificado no nível de projeto Imports '\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado. Verifique se o namespace ou o tipo é definido e contém pelo menos um membro público. Verifique se que o nome do alias não contém outros aliases.  
  
 Uma propriedade de importação de um projeto especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.  
  
 Um *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração. O elemento contido contém membros, como variáveis, procedimentos ou outros elementos que contém.  
  
 A finalidade de importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los. Seu projeto talvez seja necessário também adicionar uma referência para o namespace ou tipo. Para obter mais informações, consulte "Importação de elementos que contém" na [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não pode localizar o elemento contido, ele não é possível resolver as referências que usá-lo. Se ele localiza o elemento, mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida. Em ambos os casos não faz sentido para o elemento de importação.  
  
 Você usa o **Designer de projeto** para especificar elementos a importar. Use o **namespaces importados** seção o **referências** página. Você pode obter o **Designer de projeto** clicando duas vezes o **My Project** ícone na **Gerenciador de soluções**.  
  
 **ID do erro:** BC40057  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Abra o **Designer de projeto** e alterne para o **referência** página.  
  
2.  No **namespaces importados** seção, verifique se o elemento que o contém é acessível a partir de seu projeto.  
  
3.  Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.  
  
## <a name="see-also"></a>Consulte também
- [Página Referências, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
- [Público](../../../visual-basic/language-reference/modifiers/public.md)
- [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
