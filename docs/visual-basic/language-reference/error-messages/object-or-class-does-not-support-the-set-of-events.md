---
title: "O objeto ou a classe não dá suporte ao conjunto de eventos"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>O objeto ou a classe não dá suporte ao conjunto de eventos
Você tentou usar um `WithEvents` variável com um componente que não pode funcionar como uma fonte de evento para o conjunto de eventos especificado. Por exemplo, se desejar coletar eventos de um objeto, então criar outro objeto que `Implements` o primeiro objeto. Embora você possa pensar que você pode coletar os eventos do objeto implementado, isso não é sempre o caso. `Implements`apenas implementa uma interface para métodos e propriedades. `WithEvents`Não há suporte para privada `UserControls`, porque as informações de tipo necessária elevar o `ObjectEvent` não está disponível em tempo de execução.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Você não é possível coletar eventos de um componente que não faz eventos fonte.  
  
## <a name="see-also"></a>Consulte também  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
