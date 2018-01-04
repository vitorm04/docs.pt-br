---
title: "Cenários do controle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38e5337f775d98f8729c62b3481c3e839bff2252
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Cenários do controle DataGridView (Windows Forms)
Com o <xref:System.Windows.Forms.DataGridView> controle, você pode exibir dados de uma variedade de fontes de dados de tabela. Para usos simples, você pode preencher manualmente um <xref:System.Windows.Forms.DataGridView> e manipular os dados diretamente por meio do controle. Normalmente, no entanto, você armazena seus dados em uma fonte de dados externa e associar o controle a ele por meio de um <xref:System.Windows.Forms.BindingSource> componente.  
  
 Este tópico descreve alguns dos cenários comuns que envolvem o <xref:System.Windows.Forms.DataGridView> controle.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Cenário 1: Exibição de pequenas quantidades de dados  
 Você não precisa armazenar os dados em uma fonte de dados externa para exibi-lo no <xref:System.Windows.Forms.DataGridView> controle. Se estiver trabalhando com uma pequena quantidade de dados, você poderá preencher o controle por conta própria e manipular os dados por meio do controle. Isso é chamado de *modo não associado*. Para obter mais informações, consulte [Como criar um controle DataGridView não associado dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Principais aspectos do cenário  
  
-   No modo não associado, você preenche o controle manualmente.  
  
-   O modo não associado é especialmente adequado para pequenas quantidades de dados somente leitura.  
  
-   O modo não associado também é adequado para tabelas preenchidas escassamente ou semelhantes a planilhas.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Cenário 2: Exibindo e atualizando dados armazenados em uma fonte de dados externa  
 Você pode usar o <xref:System.Windows.Forms.DataGridView> controlar como uma interface de usuário (UI) por meio do qual os usuários podem acessar os dados mantidos em uma fonte de dados como uma tabela de banco de dados ou uma coleção de objetos de negócios. Para obter mais informações, consulte [Como associar dados ao controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Principais aspectos do cenário  
  
-   O modo associado lhe permite se conectar a uma fonte de dados, gerar colunas automaticamente de acordo com as propriedades da fonte de dados ou colunas de banco de dados e preencher automaticamente o controle.  
  
-   O modo associado é adequado para quando há um alto nível de interação do usuário com os dados. Os dados podem ser formatados para exibição e dados especificados pelo usuário podem ser analisados para o formato esperado pela fonte de dados. Erros de formatação de entrada de dados e erros de restrição de banco de dados podem ser detectados para que os usuários possam ser avisados e células com erros possam ser corrigidas.  
  
-   Funcionalidades adicionais, como a classificação, o congelamento e a reorganização de colunas permitem que os usuários exibam os dados da maneira que for mais conveniente para seu fluxo de trabalho.  
  
-   O suporte para a área de transferência permite que os usuários copiem dados de seu aplicativo para outros aplicativos.  
  
## <a name="scenario-3-advanced-data"></a>Cenário 3: Dados avançados  
 Se tiver necessidades especiais que o modelo de vinculação de dados padrão não atende, você pode gerenciar a interação entre o controle e seus dados com a implementação do *modo virtual*. Implementar o modo virtual significa implementar um ou mais manipuladores de eventos que permitem que o controle solicite informações sobre as células conforme essas informações forem necessárias.  
  
 Por exemplo, caso trabalhe com grandes quantidades de dados, você talvez queira implementar o modo virtual para garantir a eficiência máxima. O modo virtual também é útil para manter os valores das colunas não associadas que você exibe em conjunto com colunas recuperadas de outra fonte de dados.  
  
 Para obter mais informações sobre o modo virtual, consulte [Instruções passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Principais aspectos do cenário  
  
-   O modo virtual é adequado para exibir grandes quantidades de dados quando você precisar ajustar o desempenho.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Cenário 4: Redimensionar automaticamente linhas e colunas  
 Quando exibe dados que são atualizados regularmente, você pode redimensionar automaticamente as linhas e colunas para garantir que todo o conteúdo esteja visível. O <xref:System.Windows.Forms.DataGridView> controle oferece várias opções que permitem habilitar ou desabilitar manual redimensionamento, redimensionar programaticamente em horários específicos ou redimensionar automaticamente sempre que alterações de conteúdo. Para obter mais informações, consulte [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms).  
  
### <a name="scenario-key-points"></a>Principais aspectos do cenário  
  
-   O redimensionamento manual permite que os usuários ajustem as larguras e as alturas das células.  
  
-   O redimensionamento automático permite que você mantenha os tamanhos das células, de modo que o conteúdo da célula nunca seja recortado.  
  
-   O redimensionando programático permite redimensionar células em momentos específicos para evitar a degradação do desempenho decorrente do redimensionamento automático contínuo.  
  
## <a name="scenario-5-simple-customization"></a>Cenário 5: Personalização simples  
 O <xref:System.Windows.Forms.DataGridView> controle fornece várias maneiras de alterar sua aparência básica e seu comportamento. Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Principais aspectos do cenário  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle>objetos permitem que você forneça a cor, fonte, formatação e posicionamento informações em vários níveis e para elementos individuais do controle.  
  
-   Os estilos das células podem ser dispostos em camadas e compartilhados por vários elementos, permitindo que você reutilize o código.  
  
## <a name="scenario-6-advanced-customization"></a>Cenário 6: Personalização avançada  
 O <xref:System.Windows.Forms.DataGridView> controle fornece várias maneiras para personalizar sua aparência e comportamento.  
  
### <a name="scenario-key-points"></a>Principais aspectos do cenário  
  
-   Você pode fornecer seu próprio código de pintura da célula. Para obter mais informações, consulte [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Você pode fornecer sua própria pintura de linhas. Isso é útil, por exemplo, para criar linhas com conteúdo que se estende por várias colunas. Para obter mais informações, consulte [Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Você pode implementar suas próprias classes de célula e de coluna para personalizar a aparência da célula. Para obter mais informações, consulte [Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Você pode implementar suas próprias classes de célula e de coluna para hospedar controles diferentes daqueles fornecidos pelos tipos de coluna internos. Para obter mais informações, consulte [Como hospedar controles em células DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Visão geral do controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
