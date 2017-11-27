---
title: "&#39; &lt;eventname&gt;&#39; é um evento e não pode ser chamado diretamente"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords: BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a>&#39; &lt;eventname&gt;&#39; é um evento e não pode ser chamado diretamente
' <`eventname`>' é um evento e portanto não pode ser chamado diretamente. Use um `RaiseEvent` instrução para gerar um evento.  
  
 Uma chamada de procedimento especifica um evento para o nome do procedimento. Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo sinalizador, que deve ser gerado e manipulado.  
  
 **ID do erro:** BC32022  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Use um `RaiseEvent` instrução para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
