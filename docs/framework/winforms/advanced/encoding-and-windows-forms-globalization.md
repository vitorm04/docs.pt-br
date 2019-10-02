---
title: Codificação e globalização de formulários do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736881"
---
# <a name="encoding-and-windows-forms-globalization"></a>Codificação e globalização de formulários do Windows Forms

Aplicativos dos Windows Forms são totalmente habilitados para Unicode, o que significa que cada caractere é representado por um número exclusivo, independente da plataforma, programa ou linguagem. Para obter mais informações sobre Unicode, consulte o [site da Unicode Consortium](https://www.unicode.org).

## <a name="benefits-of-unicode"></a>Benefícios do Unicode

Os benefícios de formulários habilitados para Unicode incluem a capacidade de trabalhar com scripts voltados apenas para Unicode, como Hindi. Além disso, é possível usar vários idiomas em um único formulário. Em Unicode, todos os caracteres têm dois bytes, portanto nenhum esforço especial é necessário para representar caracteres de byte duplo. Também é possível escrever um único conjunto de códigos que funcionará em todas as plataformas. Essa é uma alteração das versões anteriores do Visual Basic, na qual era necessário escrever código diferente para diferentes plataformas, como o Windows NT e o Windows 98.

No entanto, determinados controles não oferecem suporte a Unicode no Windows 98 e no Windows Millennium Edition. Esses controles, todos herdados do controle comum, processarão dados com as páginas de código do Windows, como ANSI. Esses controles são: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> e <xref:System.Windows.Forms.StatusBar>. Como resultado, não é possível exibir dados Unicode nesses controles nas plataformas listadas. Por exemplo, você não pode exibir caracteres japoneses em um sistema operacional Windows 98 em inglês.

Para alternativas que reconhecem Unicode para os controles <xref:System.Windows.Forms.ToolBar> e <xref:System.Windows.Forms.StatusBar>, use os controles <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip>, que substituem esses controles mais antigos. Para manter uma aparência semelhante entre os elementos visuais em seu aplicativo, use o controle <xref:System.Windows.Forms.MenuStrip> para renderizar menus em vez de <xref:System.Windows.Forms.MainMenu>. Assim como <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> também podem processar e exibir caracteres Unicode.

## <a name="see-also"></a>Consulte também

- [Globalizando aplicativos Windows Forms](globalizing-windows-forms.md)
