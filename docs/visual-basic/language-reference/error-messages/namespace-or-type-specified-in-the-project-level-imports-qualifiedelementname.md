---
title: Namespace ou tipo especificado no nível de projeto Imports &#39; &lt;qualifiedelementname&gt;&#39; &#39; t contém nenhum membro público ou não foi encontrado
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d0a164562524af239b3b130f681dbc6eff23814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace ou tipo especificado no nível de projeto Imports &#39; &lt;qualifiedelementname&gt;&#39; &#39; t contém nenhum membro público ou não foi encontrado
Namespace ou tipo especificado no nível de projeto Imports '\<qualifiedelementname >' não contém nenhum membro público ou não pode ser encontrado. Verifique se o namespace ou o tipo está definido e contém pelo menos um membro público. Verifique se que o nome do alias não contém outros aliases.  
  
 Uma propriedade de importação de um projeto especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.  
  
 Um *que contém o elemento* pode ser um namespace, classe, estrutura, interface, módulo ou enumeração. O elemento contido contém membros, como variáveis, procedimentos ou outros elementos contidos.  
  
 A finalidade de importação é permitir que seu código para acessar membros de namespace ou tipo sem precisar qualificá-los. Seu projeto talvez seja necessário também adicionar uma referência para o namespace ou tipo. Para obter mais informações, consulte "Importação que contém elementos" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não pode localizar o elemento contido, ele não pode resolver referências que o usam. Se encontrar o elemento, mas o elemento não expõe nenhum `Public` membros e, em seguida, nenhuma referência pode ser bem-sucedida. Em ambos os casos não faz sentido para o elemento de importação.  
  
 Você usa o **Project Designer** para especificar os elementos para importar. Use o **importado namespaces** seção o **referências** página. Você pode obter o **Project Designer** clicando duas vezes o **meu projeto** ícone no **Gerenciador de soluções**.  
  
 **ID do erro:** BC40057  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Abra o **Project Designer** e alterne para o **referência** página.  
  
2.  No **importado namespaces** seção, verifique se o elemento contêiner está acessível do seu projeto.  
  
3.  Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.  
  
## <a name="see-also"></a>Consulte também  
 [Página Referências, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)  
 [Público](../../../visual-basic/language-reference/modifiers/public.md)  
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
