---
title: "Objeto ou classe não dá suporte para o conjunto de eventos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID459
dev_langs:
- VB
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
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
ms.openlocfilehash: 5e9a29aed8a2ed2d064cd2968aeb46bd21a0aec6
ms.lasthandoff: 03/13/2017

---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>O objeto ou a classe não dá suporte ao conjunto de eventos
Você tentou usar um `WithEvents` variável com um componente que não pode trabalhar como uma fonte de evento para o conjunto de eventos especificado. Por exemplo, se desejar coletar eventos de um objeto, então criar outro objeto que `Implements` o primeiro objeto. Embora você possa pensar que você pode coletar os eventos do objeto implementado, isso nem sempre é o caso. `Implements`apenas implementa uma interface para métodos e propriedades. `WithEvents`Não há suporte para particular`UserControls`, pois a informação de tipo necessária para elevar o `ObjectEvent` não está disponível em tempo de execução.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Você não pode coletar eventos de um componente que não faz eventos fonte.  
  
## <a name="see-also"></a>Consulte também  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
