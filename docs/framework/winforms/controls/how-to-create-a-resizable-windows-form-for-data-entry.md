---
title: Como criar um Windows Form redimensionável para entrada de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396021"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Como criar um Windows Form redimensionável para entrada de dados
Um bom layout responde bem a alterações nas dimensões de seu formulário pai. Você pode usar o controle <xref:System.Windows.Forms.TableLayoutPanel> para organizar o layout do formulário para redimensionar e posicionar os controles de forma consistente à medida que as dimensões do formulário são alteradas. O controle <xref:System.Windows.Forms.TableLayoutPanel> também é útil quando as alterações no conteúdo dos controles causam alterações no layout. O processo abordado neste procedimento pode ser realizado no ambiente do Visual Studio.  Consulte também [Instruções passo a passo: criando um Windows Form redimensionável para entrada de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar um controle <xref:System.Windows.Forms.TableLayoutPanel> para criar um layout que responde bem quando o usuário redimensiona o formulário. Ele também demonstra um layout que responde bem à localização.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Como criar um layout dos Windows Forms que responda bem à localização](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
