---
title: Componente BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683412"
---
# <a name="bindingsource-component"></a>Componente BindingSource
Encapsula uma fonte de dados para associação aos controles.  
  
 O <xref:System.Windows.Forms.BindingSource> componente tem duas finalidades. Primeiro, ele fornece uma camada de indireção ao associar os controles em um formulário de dados. Isso é realizado pela associação a <xref:System.Windows.Forms.BindingSource> componente à sua fonte de dados e, em seguida, associar os controles no formulário para o <xref:System.Windows.Forms.BindingSource> componente. Toda a interação adicional com os dados, incluindo navegar, classificação, filtragem e atualização, é realizada com chamadas para o <xref:System.Windows.Forms.BindingSource> componente.  
  
 Segundo, o <xref:System.Windows.Forms.BindingSource> componente pode agir como uma fonte de dados com rigidez de tipos. Adição de um tipo para o <xref:System.Windows.Forms.BindingSource> componente com o <xref:System.Windows.Forms.BindingSource.Add%2A> método cria uma lista desse tipo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do componente BindingSource](bindingsource-component-overview.md)  
 Apresenta os conceitos gerais do <xref:System.Windows.Forms.BindingSource> componente, que permite que você associe uma fonte de dados a um controle.  
  
 [Como: Associar controles dos Windows Forms a valores de banco de dados DBNull](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Mostra como lidar com um <xref:System.DBNull> o valor da fonte de dados usando o <xref:System.Windows.Forms.BindingSource> componente.  
  
 [Como: Classificar e filtrar dados ADO.NET com o Windows Forms componente BindingSource](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Demonstra como usar o <xref:System.Windows.Forms.BindingSource> componente para aplicar classificações e filtros aos dados exibidos.  
  
 [Como: Associar a um serviço Web usando o BindingSource dos Windows Forms](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Mostra como usar o <xref:System.Windows.Forms.BindingSource> componente para associar a um serviço Web.  
  
 [Como: Tratar erros e exceções que ocorrem na associação de dados](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Demonstra como usar o <xref:System.Windows.Forms.BindingSource> componente lidar normalmente com erros que ocorrem em uma operação de associação de dados.  
  
 [Como: Associar um controle dos Windows Forms a um tipo](how-to-bind-a-windows-forms-control-to-a-type.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente a associar a um tipo.  
  
 [Como: Associar um controle dos Windows Forms a um objeto de fábrica](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para vincular a um objeto de fábrica ou método.  
  
 [Como: Personalizar a adição de Item com o BindingSource dos Windows Forms](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para criar novos itens e adicioná-los a uma fonte de dados.  
  
 [Como: Gerar notificações de alteração usando o método BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para gerar eventos de notificação de alteração de fontes de dados que não dão suporte a notificação de alteração.  
  
 [Como: Gerar notificações de alteração usando um BindingSource e a Interface INotifyPropertyChanged](raise-change-notifications--bindingsource.md)  
 Demonstra como usar um tipo que herda de <xref:System.ComponentModel.INotifyPropertyChanged> com um <xref:System.Windows.Forms.BindingSource> controle.  
  
 [Como: Refletir as atualizações de fonte de dados em um controle de formulários do Windows com o BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Demonstra como responder a alterações na fonte de dados usando o <xref:System.Windows.Forms.BindingSource> componente.  
  
 [Como: Compartilhar dados associados entre formulários usando o componente BindingSource](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Mostra como usar o <xref:System.Windows.Forms.BindingSource> para associar vários formulários para a mesma fonte de dados.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.BindingSource>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.BindingSource> componente.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.BindingNavigator> controle.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Associação de dados do Windows Forms](../windows-forms-data-binding.md)  
 Contém links para tópicos que descrevem a arquitetura de associação de dados do Windows Forms.  
  
 Consulte também [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
