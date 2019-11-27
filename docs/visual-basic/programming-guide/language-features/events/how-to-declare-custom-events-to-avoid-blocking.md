---
title: Como declarar eventos personalizados para evitar bloqueio
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345141"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Como declarar eventos personalizados para evitar bloqueio (Visual Basic)
Há várias circunstâncias em que é importante que um manipulador de eventos não bloqueie os manipuladores de eventos subsequentes. Eventos personalizados permitem que o evento chame seus manipuladores de eventos de forma assíncrona.  
  
 Por padrão, o campo de armazenamento de backup para uma declaração de evento é um delegado de multicast que combina em série todos os manipuladores de eventos. Isso significa que, se um manipulador levar muito tempo para ser concluído, ele bloqueará os outros manipuladores até que seja concluído. (Manipuladores de eventos bem comparados nunca devem executar operações demoradas ou potencialmente bloqueadas.)  
  
 Em vez de usar a implementação padrão de eventos que Visual Basic fornece, você pode usar um evento personalizado para executar os manipuladores de eventos de forma assíncrona.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o acessador `AddHandler` adiciona o delegado para cada manipulador do evento `Click` a um <xref:System.Collections.ArrayList> armazenado no campo `EventHandlerList`.  
  
 Quando o código gera o evento `Click`, o acessador `RaiseEvent` invoca todos os delegados do manipulador de eventos de forma assíncrona usando o método <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>. Esse método invoca cada manipulador em um thread de trabalho e retorna imediatamente, portanto, os manipuladores não podem bloquear um ao outro.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Como declarar eventos personalizados para conservar memória](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
