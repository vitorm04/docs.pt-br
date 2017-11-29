---
title: "Visão geral do componente FontDialog (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1e00fc074148ddd53885bafbb490a3e3868fc0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="fontdialog-component-overview-windows-forms"></a>Visão geral do componente FontDialog (Windows Forms)
Windows Forms <xref:System.Windows.Forms.FontDialog> componente é uma caixa de diálogo pré-configurado, que é o padrão do Windows **fonte** caixa de diálogo usada para expor as fontes que estão atualmente instaladas no sistema. Use-o em seu aplicativo baseado no Windows como uma solução simples para seleção de fonte em vez de configurar sua própria caixa de diálogo.  
  
 Por padrão, a caixa de diálogo mostra caixas de listagem de Fonte, Estilo da fonte e Tamanho. Caixas de seleção para efeitos como Riscado e Sublinhado; uma lista suspensa para Script e um exemplo de como a fonte aparecerá. (Script refere-se a scripts de caracteres diferentes que estão disponíveis para determinada fonte, por exemplo, hebraico ou japonês.) Para exibir a caixa de diálogo de fonte, chame o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
## <a name="key-properties"></a>Propriedades da chave  
 O componente tem inúmeras propriedades que configuram sua aparência. As propriedades que definir as seleções de caixa de diálogo são <xref:System.Windows.Forms.FontDialog.Font%2A> e <xref:System.Windows.Forms.FontDialog.Color%2A>. O <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade define a fonte, estilo, tamanho, script e efeitos; por exemplo, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FontDialog>  
 [Componente FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
