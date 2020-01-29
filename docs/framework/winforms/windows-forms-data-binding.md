---
title: Associação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 68871db848ab46b88865e668f27f09972e8debcf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734616"
---
# <a name="windows-forms-data-binding"></a>Associação de dados do Windows Forms
A associação de dados no Windows Forms oferece os meios para exibir e realizar alterações nas informações de uma fonte de dados em controles no formulário. É possível associar a fontes de dados tradicionais e a praticamente qualquer estrutura que contém dados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)  
 Fornece uma visão geral da associação de dados no Windows Forms.  
  
 [Fontes de dados com suporte no Windows Forms](data-sources-supported-by-windows-forms.md)  
 Descreve as fontes de dados que podem ser usadas com o Windows Forms.  
  
 [Interfaces relacionadas à associação de dados](interfaces-related-to-data-binding.md)  
 Descreve várias das interfaces usadas com a associação de dados do Windows Forms.  
  
 [Como navegar por dados nos Windows Forms](how-to-navigate-data-in-windows-forms.md)  
 Mostra como navegar por itens em uma fonte de dados.  
  
 [Notificação de alteração na associação de dados do Windows Forms](change-notification-in-windows-forms-data-binding.md)  
 Descreve os diferentes tipos de notificação de alteração para associação de dados do Windows Forms.  
  
 [Como implementar a interface INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)  
 Mostra como implementar a interface <xref:System.ComponentModel.INotifyPropertyChanged>. A interface se comunica com um controle associado alterado pela propriedade em um objeto de negócios  
  
 [Como aplicar o padrão PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
 Mostra como aplicar o padrão *PropertyName*Changed nas propriedades de um controle de usuário do Windows Forms.  
  
 [Como implementar a interface ITypedList](how-to-implement-the-itypedlist-interface.md)  
 Mostra como habilitar a descoberta do esquema para uma lista vinculável implementando a interface <xref:System.ComponentModel.ITypedList>.  
  
 [Como implementar a interface IListSource](how-to-implement-the-ilistsource-interface.md)  
 Mostra como implementar a interface <xref:System.ComponentModel.IListSource> para criar uma classe vinculável não implementa <xref:System.Collections.IList>, mas fornece uma lista de outro local.  
  
 [Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados](multiple-controls-bound-to-data-source-synchronized.md)  
 Mostra como lidar com o evento <xref:System.Windows.Forms.BindingSource.BindingComplete> para garantir que todos os controles vinculados a uma fonte de dados permaneçam sincronizados.  
  
 [Como assegurar que a linha selecionada em uma tabela filho permaneça na posição correta](ensure-the-selected-row-in-a-child-table-correct.md)  
 Mostra como garantir que a linha selecionada de uma tabela filho não seja alterada quando uma alteração for feita em um campo da tabela pai.  
  
 Consulte também [interfaces relacionadas à vinculação de dados](interfaces-related-to-data-binding.md), [como navegar em dados em Windows Forms](how-to-navigate-data-in-windows-forms.md)e [como criar um controle de ligação simples em um Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Descreve a classe que representa a associação entre um componente vinculável e uma fonte de dados.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Descreve a classe que encapsula uma fonte de dados para associação aos controles.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Componente BindingSource](./controls/bindingsource-component.md)  
 Contém uma lista de tópicos que demonstram como usar o componente <xref:System.Windows.Forms.BindingSource>.  
  
 [Controle DataGridView](./controls/datagridview-control-windows-forms.md)  
 Fornece uma lista de tópicos que demonstram como usar um controle datagrid vinculável.  
  
 Consulte também [acessando dados no Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).
