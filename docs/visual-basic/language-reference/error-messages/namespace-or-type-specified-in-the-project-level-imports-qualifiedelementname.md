---
title: "Namespace ou tipo especificado no nível de projeto Imports &quot;&lt;qualifiedelementname&gt;&quot; não contém nenhum membro público ou não pode ser encontrado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
dev_langs:
- VB
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
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
ms.openlocfilehash: 5dae6f92f573a57d0974c860500bc7420f55a94f
ms.lasthandoff: 03/13/2017

---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace ou tipo especificado no nível de projeto Imports '&lt;qualifiedelementname&gt;' não contém nenhum membro público ou não foi encontrado
Namespace ou tipo especificado no nível de projeto Imports '\<qualifiedelementname >' não contém nenhum membro público ou não pode ser encontrado. Verifique se o namespace ou o tipo está definido e contém pelo menos um membro público. Verifique se que o nome do alias não contém outros aliases.  
  
 Uma propriedade de importação de um projeto especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.  
  
 A *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração. O elemento contido contém membros, como variáveis, procedimentos ou outros elementos contidos.  
  
 A finalidade da importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los. Seu projeto também precisará adicionar uma referência para o namespace ou tipo. Para obter mais informações, consulte "Importing Containing Elements" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não pode localizar o elemento contido, ele não pode resolver referências que o usam. Se ele acha o elemento mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida. Em ambos os casos, faz sentido para o elemento de importação.  
  
 Você usa o **Project Designer** para especificar elementos a importar. Use o **importado namespaces** seção o **referências** página. Você pode obter o **Project Designer** clicando duas vezes o **meu projeto** ícone na **Solution Explorer**.  
  
 **ID do erro:** BC40057  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Abra o **Project Designer** e alternar para o **referência** página.  
  
2.  No **importado namespaces** seção, verifique se que o elemento contêiner está acessível do seu projeto.  
  
3.  Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.  
  
## <a name="see-also"></a>Consulte também  
 [Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
