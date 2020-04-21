---
title: Windows Forms Melhorias de acessibilidade
description: Saiba como o .NET Core Windows Forms tenta melhorar a acessibilidade em comparação com o .NET Framework Windows Forms.
ms.date: 04/20/2020
helpviewer_keywords:
- Windows Forms accessibility
- accessibility
author: M-Lipin
ms.openlocfilehash: 30eb8b3bd0aaf646ea23f4f036e822f9bba78dc4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739748"
---
# <a name="accessibility-improvements-in-windows-forms-controls-for-net-core-30"></a>Melhorias de acessibilidade nos controles do Windows Forms para .NET Core 3.0

O Windows Forms continua a melhorar a forma como funciona com as tecnologias de acessibilidade para melhor apoiar os clientes do Windows Forms. essas melhorias incluem as seguintes alterações:

- Mudanças em várias áreas de interação com aplicativos clientes de acessibilidade, incluindo o Narrator.
- Alterações na hierarquia acessível (melhora da navegação por meio da árvore de automação de interface do usuário).
- Alterações na navegação do teclado.

> [!IMPORTANT]
> As alterações de acessibilidade feitas no Quadro .NET 4.7.1 até o .NET Framework 4.8 estão incluídas no .NET Core 3.0 ou superior, e são habilitadas por padrão. O .NET Framework suportava switches de compatibilidade que permitiam que os aplicativos optassem por não usar o novo comportamento de acessibilidade. Por outro lado, o .NET Core não suporta essas configurações e não permite que os aplicativos optem pelo comportamento de acessibilidade.
  
A partir do .NET Core 3.0, os aplicativos do Windows Forms se beneficiam de todos os novos recursos de acessibilidade (introduzidos no .NET Framework 4.7.1 - 4.8) sem configuração adicional.

## <a name="listbox-accessibility-support"></a>Suporte à acessibilidade do ListBox

As seguintes alterações se aplicam ao <xref:System.Windows.Forms.ListBox> controle:

- Suporte de automação de `ListBox` iu de ui habilitado para controle.
- Melhor `ListBox` suporte à acessibilidade <xref:System.Windows.Automation.ScrollItemPattern> adicionando os `ListBox` itens e melhorando o evento de acessibilidade de elevação e manuseio e navegação do Narrador através dos itens (a navegação de bloqueio de tampas não é correta e não joga a navegação fora do controle involuntariamente).

## <a name="checkedlistbox-accessibility-support"></a>Suporte à acessibilidade do CheckedListBox

As seguintes alterações se aplicam ao <xref:System.Windows.Forms.CheckedListBox> controle:

- Limites `CheckedListBox` corrigidos fornecidos por propriedades de acessibilidade para entradas.
- Melhora `ListBox` geral `CheckedListBox` e acessibilidade: valores de propriedade corrigidos e modelo de evento.

## <a name="combobox-accessibility-support"></a>Suporte à acessibilidade do ComboBox

As seguintes alterações se aplicam ao <xref:System.Windows.Forms.ComboBox> controle:

- Atualizei o `ComboBox` processo de obtenção de objetos de acessibilidade de itens para permitir a geração de IDs para <xref:System.Object.GetHashCode%2A> itens em vez de obter códigos hash de itens, o que pode ser inseguro no caso de a função ser substituída.

## <a name="datagridview-accessibility-support"></a>Suporte à acessibilidade do DataGridView

As seguintes alterações se aplicam ao <xref:System.Windows.Forms.DataGridView> controle:

- Corrigido `DataGridView.Bounds` fornecido pelas propriedades de acessibilidade para colunas, linhas, células e cabeçalhos correspondentes, melhor desempenho do cálculo retângulo delimitador. Todos os limites de acessibilidade são representados corretamente levando em conta os limites de todo o controle, juntamente com sua porta de visualização.
- Valor `Value.IsReadOnly` de propriedade corrigido fornecendo aplicações acessíveis ao cliente. A propriedade agora `IsReadOnly` mostra o status correto para as células.
- Corrigimos o <xref:System.Windows.Forms.DataGridView.CellParsing> problema com a elevação do evento para a primeira mudança de célula. O valor celular pode ser alterado `DataGridView` sem problemas, incluindo a primeira interação de controle.
- Contraste `DataGridView` de cor de fundo melhorado ao usar temas do Windows High Contrast. Alterou `DataGridView` a cor de volta padrão ao usar os temas HC#1, HC#2 e HC Black.

## <a name="propertygrid-accessibility-support"></a>Suporte à acessibilidade do PropertyGrid

As seguintes alterações se aplicam ao <xref:System.Windows.Forms.PropertyGrid> controle:

- Corrigido `PropertyGrid.Bounds` fornecido por propriedades de acessibilidade para entradas de grade, melhor desempenho do cálculo retângulo delimitador. Por enquanto, todos os limites de acessibilidade são representados corretamente levando em conta os limites de todo o controle, juntamente com sua porta de visão.
- Corrigido nomes acessíveis e descrições de subcontroles para não incluir nomes de tipo de controle e para evitar anúncio duplo para nomes de tipo de controle.

## <a name="toolstrip-accessibility-support"></a>Suporte à acessibilidade ToolStrip

As seguintes alterações se aplicam ao <xref:System.Windows.Forms.ToolStrip> controle:

- Navegação melhorada `ToolStrip`através `MenuStrip`, `StatusStrip` e itens. Navegação `ToolStrip` corrigida e `MenuStrip` de guia de turno, retroceder os itens do menu quando a seta para cima da guia de turno é pressionada, que navega até o elemento do menu inferior.
- Navegação `MenuStrip` acessível melhorada, menu corrigido tipos de controle acessíveis para submenus para fazer submenus do tipo 'Menu' em vez de 'MenuItem'.

## <a name="printpreviewcontrol-and-printpreviewdialog-accessibility-support"></a>PrintPreviewControl e PrintPreviewSuporteSuporte acessibilidade de diálogo

As seguintes alterações se aplicam aos controles de impressão:

- Navegação acessível melhorada (incluindo navegação narradora) através de itens de menu.
- Melhorados temas de Alto Contraste suportam e tornaram o elemento de controle mais contrastado.

## <a name="stringcollectioneditor-accessibility-support"></a>Suporte à acessibilidade StringCollectionEditor

O designer do Windows Forms agora usa o editor de coleção de strings com suporte de acessibilidade aprimorado.

## <a name="monthcalendar-accessibility-support-available-in-net-core-31"></a>Suporte de acessibilidade monthcalendar (disponível em .NET Core 3.1)

As seguintes alterações se aplicam ao <xref:System.Windows.Forms.MonthCalendar> controle:

- Adicionou provedores de `MonthCalendar` servidores de automação de ui para controlar, adicionou o padrão de grade de automação de ui e provedores de padrão de tabela.
- Alterou o tipo de controle acessível à _tabela_ para o tipo de `MonthCalendar` controle acessível ao _calendário,_ `MonthCalendar` exceto no caso em que o controle possui um controle de rótulo anterior que define o nome acessível ao controle, neste caso específico, o tipo de controle acessível torna-se _tabela_.
- Anúncio aprimorado da data `MonthCalendar` selecionada para controle.
- Suporte `MonthCalendar` de controle aprimorado para leitores de tela e outras ferramentas de acessibilidade. Neste momento, os usuários podem navegar pelos elementos de controle e interagir com esses elementos usando a entrada somente para teclado. Com o Narrador, use caps + teclas de seta para navegação através dos elementos de controle e CAPS + Enter para invocar a ação padrão do elemento.
- Navegação melhorada da `MonthCalendar` tecla de seta através de elementos infantis com um retângulo focal: retângulo de foco azul para Narrador.
- Acessibilidade aprimorada para ação de `MonthCalendar` teste de `MonthCalendar` impacto para elementos de controle para permitir obter elementos acessíveis à criança por coordenadas fornecidas.

## <a name="tooltips-accessibility-available-in-net-core-31"></a>Acessibilidade ToolTips (disponível no .NET Core 3.1)

- Adicionada capacidade de anunciar um texto de dica de ferramenta por aplicativos de leitor de tela, como NVDA e Narrator. O aplicativo do leitor de tela agora pode anunciar o texto da dica de ferramenta do teclado ou mouse de qualquer controle do Windows Forms configurado para mostrar dicas de ferramentas.

## <a name="ui-automation-support-for-datagridview-propertygrid-listbox-combobox-toolstrip-and-other-controls"></a>Suporte à automação de IU para DataGridView, PropertyGrid, ListBox, ComboBox, ToolStrip e outros controles

O suporte à automação de ia é habilitado para controles em tempo de execução, mas não é usado durante o tempo de projeto. Para obter uma visão geral de automação da interface do usuário, confira a [Visão geral de automação da interface do usuário](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

## <a name="see-also"></a>Confira também

- [Práticas recomendadas de acessibilidade](../ui-automation/accessibility-best-practices.md).
