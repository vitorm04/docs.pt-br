---
title: Visão geral do componente FontDialog
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745699"
---
# <a name="fontdialog-component-overview-windows-forms"></a>Visão geral do componente FontDialog (Windows Forms)
O Windows Forms <xref:System.Windows.Forms.FontDialog> componente é uma caixa de diálogo pré-configurada, que é a caixa de diálogo de **fontes** padrão do Windows usada para expor as fontes atualmente instaladas no sistema. Use-o em seu aplicativo baseado no Windows como uma solução simples para seleção de fonte em vez de configurar sua própria caixa de diálogo.  
  
 Por padrão, a caixa de diálogo mostra caixas de listagem de Fonte, Estilo da fonte e Tamanho. Caixas de seleção para efeitos como Riscado e Sublinhado; uma lista suspensa para Script e um exemplo de como a fonte aparecerá. (O script refere-se a scripts de caracteres diferentes que estão disponíveis para uma determinada fonte, por exemplo, hebraico ou japonês.) Para exibir a caixa de diálogo fonte, chame o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="key-properties"></a>Propriedades da chave  
 O componente tem inúmeras propriedades que configuram sua aparência. As propriedades que definem as seleções da caixa de diálogo são <xref:System.Windows.Forms.FontDialog.Font%2A> e <xref:System.Windows.Forms.FontDialog.Color%2A>. A propriedade <xref:System.Windows.Forms.FontDialog.Font%2A> define a fonte, o estilo, o tamanho, o script e os efeitos; por exemplo, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.FontDialog>
- [Componente FontDialog](fontdialog-component-windows-forms.md)
