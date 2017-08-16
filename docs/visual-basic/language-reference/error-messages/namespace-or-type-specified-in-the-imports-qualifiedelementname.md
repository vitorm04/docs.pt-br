---
title: "Tipo ou Namespace especificado em Imports&quot;&lt;qualifiedelementname&gt;&quot; não contém nenhum membro público ou não pode ser encontrado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40056
- vbc40056
dev_langs:
- VB
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: 8
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
ms.openlocfilehash: 7ad40a538f12f05eae2fe3577d1208b407a4b966
ms.lasthandoff: 03/13/2017

---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Tipo ou Namespace especificado em Imports'&lt;qualifiedelementname&gt;' não contém nenhum membro público ou não foi encontrado
Tipo ou Namespace especificado em Imports'\<qualifiedelementname >' não contém nenhum membro público ou não pode ser encontrado. Verifique se o namespace ou o tipo está definido e contém pelo menos um membro público. Verifique se que o nome do alias não contém outros aliases.  
  
 Um `Imports` instrução Especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.  
  
 A *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração. O elemento contido contém membros, como variáveis, procedimentos ou outros elementos contidos.  
  
 A finalidade da importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los. Seu projeto também precisará adicionar uma referência para o namespace ou tipo. Para obter mais informações, consulte "Importing Containing Elements" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Se o compilador não pode localizar o elemento contido, ele não pode resolver referências que o usam. Se ele acha o elemento mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida. Em ambos os casos, faz sentido para o elemento de importação.  
  
 Tenha em mente que se você importar um elemento de recipiente e atribuir um alias de importação para ele, em seguida, é possível usar esse alias de importação para importar de outro elemento. O código a seguir gera um erro do compilador.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **ID do erro:** BC40056  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se o elemento contêiner está acessível do seu projeto.  
  
2.  Verifique se a especificação do elemento contido não incluem qualquer alias de importação da importação de outro.  
  
3.  Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
