---
title: Propriedades em controles dos Windows Forms de suporte a diretrizes de acessibilidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ca18b35b90b028054e68a0a14fecc819a6c20b9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Propriedades em controles dos Windows Forms de suporte a diretrizes de acessibilidade
Os controles na caixa de ferramentas padrão para Windows Forms oferecem suporte a muitas das diretrizes de acessibilidade, incluindo exibição do foco do teclado e dos elementos da tela.  
  
## <a name="planning-ahead-for-accessibility"></a>Planejando acessibilidade  
 As propriedades dos controles podem ser usadas para dar suporte a outras diretrizes de acessibilidade, conforme mostrado na tabela a seguir. Além disso, é preciso usar menus para fornecer acesso aos recursos do programa.  
  
|Propriedades do controle|Considerações sobre acessibilidade|  
|----------------------|--------------------------------------|  
|AccessibleDescription|A descrição é relatada para auxiliares de acessibilidade, tais como leitores de tela. Os auxiliares de acessibilidade são programas e dispositivos especializados que ajudam as pessoas com deficiência a usar computadores de forma mais eficaz.|  
|AccessibleName|O nome a ser relatado aos auxiliares de acessibilidade.|  
|AccessibleRole|Descreve o uso do elemento na interface do usuário.|  
|TabIndex|Cria um caminho de navegação sensível pelo formulário. É importante para os controles sem rótulos intrínsecos, como caixas de texto, ter seu rótulo associado imediatamente antes deles na ordem de tabulação.|  
|Texto|Use o caractere "&" para criar teclas de acesso. O uso de teclas de acesso é parte do fornecimento de acesso documentado do teclado para recursos.|  
|Tamanho da fonte|Se o tamanho da fonte não for ajustável, ele deverá ser definido como 10 pontos ou maior. Uma vez definido o tamanho da fonte do formulário, todos os controles adicionados depois ao formulário terão o mesmo tamanho.|  
|Forecolor|Se essa propriedade for definida como padrão, as preferências de cores do usuário serão usadas no formulário.|  
|Backcolor|Se essa propriedade for definida como padrão, as preferências de cores do usuário serão usadas no formulário.|  
|BackgroundImage|Deixe essa propriedade em branco para tornar o texto mais legível.|  
  
## <a name="see-also"></a>Consulte também  
 [Instruções passo a passo: criando um aplicativo acessível baseado no Windows](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
