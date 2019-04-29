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
ms.openlocfilehash: 7f140807bf4b42e530302190042e729c59248e7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789305"
---
# <a name="fontdialog-component-overview-windows-forms"></a>Visão geral do componente FontDialog (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.FontDialog> componente é uma caixa de diálogo pré-configurada, que é o padrão Windows **fonte** caixa de diálogo usada para expor as fontes que estão atualmente instaladas no sistema. Use-o em seu aplicativo baseado no Windows como uma solução simples para seleção de fonte em vez de configurar sua própria caixa de diálogo.  
  
 Por padrão, a caixa de diálogo mostra caixas de listagem de Fonte, Estilo da fonte e Tamanho. Caixas de seleção para efeitos como Riscado e Sublinhado; uma lista suspensa para Script e um exemplo de como a fonte aparecerá. (Script refere-se a scripts de caracteres diferentes que estão disponíveis para determinada fonte, por exemplo, hebraico ou japonês.) Para exibir a caixa de diálogo de fonte, chame o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.  
  
## <a name="key-properties"></a>Propriedades da chave  
 O componente tem inúmeras propriedades que configuram sua aparência. As propriedades que defina as seleções de caixa de diálogo são <xref:System.Windows.Forms.FontDialog.Font%2A> e <xref:System.Windows.Forms.FontDialog.Color%2A>. O <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade define a fonte, estilo, tamanho, script e efeitos; por exemplo, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FontDialog>
- [Componente FontDialog](fontdialog-component-windows-forms.md)
