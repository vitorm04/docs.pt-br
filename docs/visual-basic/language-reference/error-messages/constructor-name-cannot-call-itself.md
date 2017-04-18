---
title: "Construtor &quot;&lt;nome&gt;&quot; não pode chamar a mesmo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
dev_langs:
- VB
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
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
ms.openlocfilehash: ff25354e49bb276bf5e48e7d6ee3b7f5a834ea8d
ms.lasthandoff: 03/13/2017

---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Construtor '&lt;nome&gt;' não pode chamar a mesmo
Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.  
  
 A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ela é primeiro criado. Uma classe ou estrutura pode ter vários construtores, desde que todos eles têm diferentes listas de parâmetros. Um construtor pode chamar outro construtor para executar sua funcionalidade além de seu próprio. Mas não faz sentido um construtor chamar a próprio e, de fato resultaria em recursão infinita se permitido.  
  
 **ID do erro:** BC30298  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a lista de parâmetro do construtor sendo chamado. Ele deve ser diferente do construtor fazendo a chamada.  
  
2.  Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.  
  
## <a name="see-also"></a>Consulte também  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
