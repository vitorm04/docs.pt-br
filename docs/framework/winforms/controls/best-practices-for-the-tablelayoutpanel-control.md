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
ms.openlocfilehash: 6be6d0904d5b52e5188f0a5a16aaefa08265379c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674187"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>Práticas recomendadas para o controle TableLayoutPanel
O <xref:System.Windows.Forms.TableLayoutPanel> controle fornece recursos poderosos de layout que você deve considerar cuidadosamente antes de usar em seus formulários do Windows.  
  
## <a name="recommendations"></a>Recomendações  
 As recomendações a seguir ajudará você a usar o <xref:System.Windows.Forms.TableLayoutPanel> controle aproveitando melhor.  
  
### <a name="targeted-use"></a>Uso direcionado  
 Use o <xref:System.Windows.Forms.TableLayoutPanel> controlar com moderação. Você não deve usá-lo em todas as situações que exigem um layout redimensionável. A lista a seguir descreve os layouts que mais o uso de beneficiam o <xref:System.Windows.Forms.TableLayoutPanel> controle:  
  
-   Layouts em que há várias partes do formulário redimensionadas proporcionalmente umas para outras.  
  
-   Layouts que serão modificados ou gerados dinamicamente no tempo de execução, como formulários de entrada de dados que têm campos personalizáveis pelo usuário adicionados ou subtraídos com base nas preferências.  
  
-   Layouts que devem permanecer em um tamanho fixo geral. Por exemplo, você pode ter uma caixa de diálogo que deve permanecer menor do que 800 x 600, mas você precisa dar suporte a cadeias de caracteres localizadas.  
  
 A lista a seguir descreve os layouts que não se beneficiam muito do usando o <xref:System.Windows.Forms.TableLayoutPanel> controle:  
  
-   Formulários de entrada de dados simples com uma única coluna de rótulos e uma única coluna de áreas de entrada de texto.  
  
-   Formulários com uma única área de exibição grande que deve preencher o espaço disponível quando ocorre um redimensionamento. Um exemplo disso é um formulário que exibe uma única <xref:System.Windows.Forms.PropertyGrid> controle. Nesse caso, use ancoragem, pois nada mais deve expandir quando o formulário é redimensionado.  
  
 Escolha cuidadosamente quais controles precisam estar em um <xref:System.Windows.Forms.TableLayoutPanel> controle. Se você tiver espaço para o texto crescer até 30% usando ancoragem, considere usar o <xref:System.Windows.Forms.Control.Anchor%2A> apenas com a propriedade. Se você pode estimar o espaço necessário para o layout, use <xref:System.Windows.Forms.Control.Dock%2A> e <xref:System.Windows.Forms.Control.Anchor%2A> é mais fácil do que os detalhes de espaço restante e <xref:System.Windows.Forms.Control.AutoSize%2A> comportamento.  
  
 Em geral, ao projetar seu layout com o <xref:System.Windows.Forms.TableLayoutPanel> controlar, mantenha o design mais simples possível.  
  
### <a name="use-the-document-outline-window"></a>Usar a janela Estrutura de Tópicos de Documento  
 A janela Estrutura de Tópicos de Documento fornece um modo de exibição de árvore do layout, que pode ser usada para manipular as relações pai-filho e de ordem z dos controles. No **menu Exibir**, selecione **Outras Janelas** e escolha **Estrutura de Tópicos de Documento**.  
  
### <a name="avoid-nesting"></a>Evitar aninhamento  
 Evitar aninhamento outro <xref:System.Windows.Forms.TableLayoutPanel> controles dentro de um <xref:System.Windows.Forms.TableLayoutPanel> controle. Pode ser difícil depurar layouts aninhados.  
  
### <a name="avoid-visual-inheritance"></a>Evitar herança visual  
 O <xref:System.Windows.Forms.TableLayoutPanel> controle não dá suporte a herança visual no Designer de formulários do Windows. Um <xref:System.Windows.Forms.TableLayoutPanel> controle em uma classe derivada é exibido como "bloqueada" em tempo de design.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
