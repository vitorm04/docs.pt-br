---
title: Como a entrada do mouse funciona no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 7817b6a414f313cd2891fe0e124e230643b06e07
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725315"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Como a entrada do mouse funciona no Windows Forms
Receber e manipular entradas de mouse é uma parte importante qualquer aplicativo do Windows. Você pode manipular eventos de mouse para executar uma ação em seu aplicativo ou usar informações sobre a localização do mouse para executar testes de clique ou outras ações. Além disso, é possível alterar a maneira como os controles em seu aplicativo manipulam as entradas de mouse. Este tópico descreve esses eventos de mouse de forma detalhada, bem como obter e alterar configurações do sistema para o mouse. Para obter mais informações sobre os dados fornecidos com os eventos de mouse e a ordem em que os eventos de clique do mouse são gerados, consulte [Eventos de mouse nos Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Localização do mouse e teste de clique  
 Quando o usuário move o mouse, o sistema operacional move o ponteiro do mouse. O ponteiro do mouse contém um único pixel, chamado de ponto de acesso, que o sistema operacional rastreia e reconhece como a posição do ponteiro. Quando o usuário move o mouse ou pressiona um botão do mouse, o <xref:System.Windows.Forms.Control> que contém o <xref:System.Windows.Forms.Cursor.HotSpot%2A> gera o evento de mouse apropriado. Você pode obter a posição atual do mouse com o <xref:System.Windows.Forms.MouseEventArgs.Location%2A> propriedade do <xref:System.Windows.Forms.MouseEventArgs> ao manipular um evento de mouse ou usando o <xref:System.Windows.Forms.Cursor.Position%2A> propriedade do <xref:System.Windows.Forms.Cursor> classe. Posteriormente, você pode usar informações sobre a localização do mouse para executar o teste de clique e, em seguida, executar uma ação com base na localização do mouse. Capacidade de teste de clique é interna a vários controles nos Windows Forms, como o <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> e <xref:System.Windows.Forms.DataGridView> controles. Usado com o evento de mouse apropriado, <xref:System.Windows.Forms.Control.MouseHover> , por exemplo, o teste de clique é muito útil para determinar quando o aplicativo deve executar uma ação específica.  
  
## <a name="mouse-events"></a>Eventos de mouse  
 A principal maneira de responder a entradas de mouse é manipular eventos de mouse. A tabela a seguir mostra os eventos de mouse e descreve quando eles são gerados.  
  
|Evento de mouse|Descrição|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Esse evento ocorre quando o botão do mouse é liberado, normalmente antes o <xref:System.Windows.Forms.Control.MouseUp> eventos. O manipulador deste evento recebe um argumento do tipo <xref:System.EventArgs>. Manipule este evento quando você só precisar determinar quando um clique ocorrer.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Este evento ocorre quando o usuário clica no controle com o mouse. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.MouseEventArgs>. Manipule este evento quando você precisar obter informações sobre o mouse quando um clique ocorrer.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Este evento ocorre quando um usuário clica duas vezes no controle. O manipulador deste evento recebe um argumento do tipo <xref:System.EventArgs>. Manipule este evento quando você só precisar determinar quando um clique duplo ocorrer.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Este evento ocorre quando o usuário clica duas vezes no controle com o mouse. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.MouseEventArgs>. Manipule este evento quando você precisar obter informações sobre o mouse quando um clique duplo ocorrer.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Este evento ocorre quando o ponteiro do mouse está sobre o controle e um botão do mouse é pressionado. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Este evento ocorre quando o ponteiro do mouse entra na borda ou na área de cliente do controle, dependendo do tipo de controle. O manipulador deste evento recebe um argumento do tipo <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Este evento ocorre quando o ponteiro do mouse para e permanece sobre o controle. O manipulador deste evento recebe um argumento do tipo <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Este evento ocorre quando o ponteiro do mouse deixa a borda ou a área de cliente do controle, dependendo do tipo de controle. O manipulador deste evento recebe um argumento do tipo <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Este evento ocorre quando o ponteiro do mouse se move enquanto está sobre um controle. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Este evento ocorre quando o ponteiro do mouse está sobre o controle e o usuário libera um botão do mouse. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Este evento ocorre quando o usuário gira o botão de rolagem do mouse enquanto o controle está em foco. O manipulador deste evento recebe um argumento do tipo <xref:System.Windows.Forms.MouseEventArgs>. Você pode usar o <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> propriedade de <xref:System.Windows.Forms.MouseEventArgs> para determinar quanto o mouse foi rolado.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Alterando a entrada do mouse e detectando as configurações do sistema  
 Você pode detectar e alterar a maneira como um controle manipula a entrada de mouse derivando do controle e usando o <xref:System.Windows.Forms.Control.GetStyle%2A> e <xref:System.Windows.Forms.Control.SetStyle%2A> métodos. O <xref:System.Windows.Forms.Control.SetStyle%2A> método usa uma combinação bit a bit de <xref:System.Windows.Forms.ControlStyles> valores para determinar se o controle terá padrão clique ou clique duas vezes no comportamento ou se o controle manipulará seu próprio processamento de mouse. Além disso, o <xref:System.Windows.Forms.SystemInformation> classe inclui propriedades que descrevem os recursos do mouse e especificam como o mouse interage com o sistema operacional. A tabela a seguir resume essas propriedades.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Obtém as dimensões, em pixels, da área em que o usuário deve clicar duas vezes para que o sistema operacional considere os dois cliques um clique duplo.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Obtém o número máximo de milissegundos que pode decorrer entre um primeiro clique e um segundo clique para que o sistema operacional considere a ação do mouse um clique duplo.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Obtém o número de botões do mouse.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Obtém um valor que indica se as funções dos botões esquerdo e direito do mouse foram trocadas.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Obtém as dimensões, em pixels, do retângulo no qual o ponteiro do mouse deve permanecer pelo tempo de foco do mouse antes que uma mensagem de foco do mouse seja gerada.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Obtém o tempo, em milissegundos, que o ponteiro do mouse deve permanecer no retângulo de foco antes que uma mensagem de foco do mouse seja gerada.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Obtém um valor que indica se um mouse está instalado.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Obtém um valor que indica a velocidade atual do mouse, de 1 a 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Obtém um valor que indica se um mouse com botão de rolagem está instalado.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Obtém o valor delta do incremento de uma única rotação da roda do mouse.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Obtém o número de linhas a rolar quando o botão de rolagem do mouse é girado.|  
  
## <a name="see-also"></a>Consulte também
- [Entrada do mouse em um Aplicativo do Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Captura do mouse nos Windows Forms](mouse-capture-in-windows-forms.md)
- [Ponteiros do mouse nos Windows Forms](mouse-pointers-in-windows-forms.md)
