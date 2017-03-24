---
title: "&quot;&lt;interfacename&gt;.&lt; nome do membro&gt;&quot;já foi implementado pela classe base&quot;&lt;baseclassname&gt;&quot;. Reimplementação de &lt;tipo&gt; assumido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
dev_langs:
- VB
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 5ab2041826f74fdc5aceab7b1ceb26563d9b3f0a
ms.lasthandoff: 03/13/2017

---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>'&lt;interfacename&gt;.&lt; nome do membro&gt;'já foi implementado pela classe base'&lt;baseclassname&gt;'. Reimplementação de &lt;tipo&gt; assumido
Uma propriedade, procedimento ou evento em uma classe derivada usa um `Implements` cláusula especificando um membro de interface que já é implementado na classe base.  
  
 Uma classe derivada pode reimplementar um membro de interface que é implementado pela classe base. Isso não é o mesmo que substituir a implementação da classe base. Para obter mais informações, consulte [implementa](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42015  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você pretende reimplementar o membro de interface, você não precisa realizar nenhuma ação. Código em sua classe derivada acessa o membro reimplementedo, a menos que você use o `MyBase` palavra-chave para acessar a implementação da classe base.  
  
-   Se você não pretende reimplementar o membro de interface, remova o `Implements` cláusula da declaração de propriedade, procedimento ou evento.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
