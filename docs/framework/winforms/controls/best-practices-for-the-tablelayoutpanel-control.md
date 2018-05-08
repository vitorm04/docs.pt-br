---
title: Práticas recomendadas para o controle TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 40322dc6c5facd4167a4c9ac5c12fdf2a8831b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>Práticas recomendadas para o controle TableLayoutPanel
O <xref:System.Windows.Forms.TableLayoutPanel> controle fornece recursos avançados de layout que você deve considerar cuidadosamente antes de usar em seus formulários do Windows.  
  
## <a name="recommendations"></a>Recomendações  
 As recomendações a seguir o ajudarão a usar o <xref:System.Windows.Forms.TableLayoutPanel> controle aproveitando melhor.  
  
### <a name="targeted-use"></a>Uso direcionado  
 Use o <xref:System.Windows.Forms.TableLayoutPanel> controlar com moderação. Você não deve usá-lo em todas as situações que exigem um layout redimensionável. A lista a seguir descreve os layouts que se beneficiar mais com o uso do <xref:System.Windows.Forms.TableLayoutPanel> controle:  
  
-   Layouts em que há várias partes do formulário redimensionadas proporcionalmente umas para outras.  
  
-   Layouts que serão modificados ou gerados dinamicamente no tempo de execução, como formulários de entrada de dados que têm campos personalizáveis pelo usuário adicionados ou subtraídos com base nas preferências.  
  
-   Layouts que devem permanecer em um tamanho fixo geral. Por exemplo, você pode ter uma caixa de diálogo que deve permanecer menor do que 800 x 600, mas você precisa dar suporte a cadeias de caracteres localizadas.  
  
 A lista a seguir descreve os layouts que não se beneficiam muito do uso de <xref:System.Windows.Forms.TableLayoutPanel> controle:  
  
-   Formulários de entrada de dados simples com uma única coluna de rótulos e uma única coluna de áreas de entrada de texto.  
  
-   Formulários com uma única área de exibição grande que deve preencher o espaço disponível quando ocorre um redimensionamento. Um exemplo disso é um formulário que exibe uma única <xref:System.Windows.Forms.PropertyGrid> controle. Nesse caso, use ancoragem, pois nada mais deve expandir quando o formulário é redimensionado.  
  
 Escolha cuidadosamente quais controles precisam estar em um <xref:System.Windows.Forms.TableLayoutPanel> controle. Se você tem espaço para crescer em 30% usando ancoragem seu texto, considere usar o <xref:System.Windows.Forms.Control.Anchor%2A> apenas com a propriedade. Se você pode estimar o espaço necessário para o layout, o uso de <xref:System.Windows.Forms.Control.Dock%2A> e <xref:System.Windows.Forms.Control.Anchor%2A> é mais fácil do que os detalhes de espaço restante e <xref:System.Windows.Forms.Control.AutoSize%2A> comportamento.  
  
 Em geral, ao projetar o layout com o <xref:System.Windows.Forms.TableLayoutPanel> controlar, mantenha o design mais simples possível.  
  
### <a name="use-the-document-outline-window"></a>Usar a janela Estrutura de Tópicos de Documento  
 A janela Estrutura de Tópicos de Documento fornece um modo de exibição de árvore do layout, que pode ser usada para manipular as relações pai-filho e de ordem z dos controles. No **menu Exibir**, selecione **Outras Janelas** e escolha **Estrutura de Tópicos de Documento**.  
  
### <a name="avoid-nesting"></a>Evitar aninhamento  
 Evite aninhamento outros <xref:System.Windows.Forms.TableLayoutPanel> controla dentro de um <xref:System.Windows.Forms.TableLayoutPanel> controle. Pode ser difícil depurar layouts aninhados.  
  
### <a name="avoid-visual-inheritance"></a>Evitar herança visual  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle não oferece suporte a herança visual no Designer de formulários do Windows. Um <xref:System.Windows.Forms.TableLayoutPanel> controle em uma classe derivada é exibido como "bloqueada" em tempo de design.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
