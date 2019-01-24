---
title: Visão geral do componente FontDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 854f54454c0c88f965d9ac8240c11f6821f0c64b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594558"
---
# <a name="fontdialog-component-overview-windows-forms"></a>Visão geral do componente FontDialog (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.FontDialog> componente é uma caixa de diálogo pré-configurada, que é o padrão Windows **fonte** caixa de diálogo usada para expor as fontes que estão atualmente instaladas no sistema. Use-o em seu aplicativo baseado no Windows como uma solução simples para seleção de fonte em vez de configurar sua própria caixa de diálogo.  
  
 Por padrão, a caixa de diálogo mostra caixas de listagem de Fonte, Estilo da fonte e Tamanho. Caixas de seleção para efeitos como Riscado e Sublinhado; uma lista suspensa para Script e um exemplo de como a fonte aparecerá. (Script refere-se a scripts de caracteres diferentes que estão disponíveis para determinada fonte, por exemplo, hebraico ou japonês.) Para exibir a caixa de diálogo de fonte, chame o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
## <a name="key-properties"></a>Propriedades da chave  
 O componente tem inúmeras propriedades que configuram sua aparência. As propriedades que defina as seleções de caixa de diálogo são <xref:System.Windows.Forms.FontDialog.Font%2A> e <xref:System.Windows.Forms.FontDialog.Color%2A>. O <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade define a fonte, estilo, tamanho, script e efeitos; por exemplo, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.FontDialog>
- [Componente FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
