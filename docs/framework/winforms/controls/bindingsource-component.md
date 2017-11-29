---
title: Componente BindingSource
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 006cafafdf8e3c3f4da77394d6155fa52e113b58
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="bindingsource-component"></a>Componente BindingSource
Encapsula uma fonte de dados para associação aos controles.  
  
 O <xref:System.Windows.Forms.BindingSource> componente tem duas finalidades. Primeiro, ele fornece uma camada de indireção ao associar os controles em um formulário de dados. Isso é feito pela associação a <xref:System.Windows.Forms.BindingSource> componente para sua fonte de dados e, em seguida, associar os controles no formulário para o <xref:System.Windows.Forms.BindingSource> componente. Toda a interação adicional com os dados, incluindo navegar, classificação, filtragem e atualização, é feita com chamadas para o <xref:System.Windows.Forms.BindingSource> componente.  
  
 Segundo, o <xref:System.Windows.Forms.BindingSource> componente pode agir como uma fonte de dados fortemente tipados. Adicionar um tipo para o <xref:System.Windows.Forms.BindingSource> componente com o <xref:System.Windows.Forms.BindingSource.Add%2A> método cria uma lista desse tipo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 Apresenta os conceitos gerais do <xref:System.Windows.Forms.BindingSource> componente, que permite que você associe uma fonte de dados a um controle.  
  
 [Como associar controles dos Windows Forms a valores de banco de dados DBNull](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Mostra como tratar uma <xref:System.DBNull> valor da fonte de dados usando o <xref:System.Windows.Forms.BindingSource> componente.  
  
 [Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Demonstra como usar o <xref:System.Windows.Forms.BindingSource> componente para aplicar classificações e filtros para dados exibidos.  
  
 [Como associar a um serviço Web usando o BindingSource dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Mostra como usar o <xref:System.Windows.Forms.BindingSource> componente para vincular a um serviço Web.  
  
 [Como identificar erros e exceções que ocorram na associação de dados](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Demonstra como usar o <xref:System.Windows.Forms.BindingSource> componente para manipular normalmente erros que ocorrem em uma operação de associação de dados.  
  
 [Como associar um controle dos Windows Forms a um tipo](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para vincular a um tipo.  
  
 [Como associar um controle dos Windows Forms a um objeto de fábrica](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para vincular a um objeto de fábrica ou método.  
  
 [Como personalizar a adição de item com o BindingSource dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para criar novos itens e adicioná-los a uma fonte de dados.  
  
 [Como acionar notificações de alteração usando o método BindingSource ResetItem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para gerar eventos de notificação de alteração para fontes de dados que não oferecem suporte a notificação de alteração.  
  
 [Como gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 Demonstra como usar um tipo que herda o <xref:System.ComponentModel.INotifyPropertyChanged> com um <xref:System.Windows.Forms.BindingSource> controle.  
  
 [Como refletir atualizações feitas na fonte de dados em um controle dos Windows Forms com o BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Demonstra como responder a alterações na fonte de dados usando o <xref:System.Windows.Forms.BindingSource> componente.  
  
 [Como compartilhar dados associados entre formulários usando o componente BindingSource](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Mostra como usar o <xref:System.Windows.Forms.BindingSource> para associar várias formas à mesma fonte de dados.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.BindingSource>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.BindingSource> componente.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.BindingNavigator> controle.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Associação de dados do Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 Contém links para tópicos que descrevem a arquitetura de associação de dados do Windows Forms.  
  
 Consulte também [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
