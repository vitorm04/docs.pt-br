---
title: "Como classificar uma coluna GridView quando um cabeçalho é clicado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], GridView
- controls [WPF], ListView
- ListView controls [WPF], sorting GridView columns
- GridView controls [WPF], ListView control
ms.assetid: 4865d720-d147-40ed-83a7-af7587f8aad8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f24be0ce97071905ce53610e5b44db8f92f24e0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sort-a-gridview-column-when-a-header-is-clicked"></a>Como classificar uma coluna GridView quando um cabeçalho é clicado
Este exemplo mostra como criar um <xref:System.Windows.Controls.ListView> controle que implementa um <xref:System.Windows.Controls.GridView> exibir modo e classifica os dados de conteúdo quando um usuário clica em um cabeçalho de coluna.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma <xref:System.Windows.Controls.GridView> com três colunas que se vinculam ao <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, e <xref:System.DateTime.Day%2A>, propriedades do <xref:System.DateTime> estrutura.  
  
```xaml  
<GridView>  
  <GridViewColumn DisplayMemberBinding="{Binding Path=Year}"   
                  Header="Year"  
                  Width="100"/>  
  <GridViewColumn DisplayMemberBinding="{Binding Path=Month}"   
                  Header="Month"  
                  Width="100"/>  
  <GridViewColumn DisplayMemberBinding="{Binding Path=Day}"   
                  Header="Day"  
                  Width="100"/>  
</GridView>  
```  
  
 O exemplo a seguir mostra os itens de dados que são definidos como um <xref:System.Collections.ArrayList> de <xref:System.DateTime> objetos. O <xref:System.Collections.ArrayList> é definido como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> para o <xref:System.Windows.Controls.ListView> controle.  
  
```xaml  
<ListView.ItemsSource>  
  <s:ArrayList>  
    <p:DateTime>1993/1/1 12:22:02</p:DateTime>  
    <p:DateTime>1993/1/2 13:2:01</p:DateTime>  
    <p:DateTime>1997/1/3 2:1:6</p:DateTime>  
    <p:DateTime>1997/1/4 13:6:55</p:DateTime>  
    <p:DateTime>1999/2/1 12:22:02</p:DateTime>  
    <p:DateTime>1998/2/2 13:2:01</p:DateTime>  
    <p:DateTime>2000/2/3 2:1:6</p:DateTime>  
    <p:DateTime>2002/2/4 13:6:55</p:DateTime>  
    <p:DateTime>2001/3/1 12:22:02</p:DateTime>  
    <p:DateTime>2006/3/2 13:2:01</p:DateTime>  
    <p:DateTime>2004/3/3 2:1:6</p:DateTime>  
    <p:DateTime>2004/3/4 13:6:55</p:DateTime>  
  </s:ArrayList>  
</ListView.ItemsSource>  
```  
  
 Os identificadores `s` e `p` nas marcas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se referem a mapeamentos de namespace definidos nos metadados da página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. O exemplo a seguir mostra a definição dos metadados.  
  
```xaml  
<Window        
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Class="ListViewSort.Window1"      
    xmlns:s="clr-namespace:System.Collections;assembly=mscorlib"  
    xmlns:p="clr-namespace:System;assembly=mscorlib">  
```  
  
 Para classificar os dados de acordo com o conteúdo de uma coluna, o exemplo define um manipulador de eventos para lidar com o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento que ocorre quando você pressiona o botão de cabeçalho de coluna. O exemplo a seguir mostra como especificar um manipulador de eventos para o <xref:System.Windows.Controls.GridViewColumnHeader> controle.  
  
```xaml  
<ListView x:Name='lv' Height="150" HorizontalAlignment="Center"   
  VerticalAlignment="Center"   
  GridViewColumnHeader.Click="GridViewColumnHeaderClickedHandler"  
 >  
```  
  
 O exemplo define o manipulador de eventos para que a direção de classificação mude entre ordem ascendente e decrescente sempre que você pressionar o botão de cabeçalho de coluna. O exemplo a seguir mostra o manipulador de eventos.  
  
```csharp  
public partial class Window1 : Window  
{  
    public Window1()  
    {  
        InitializeComponent();  
    }  
  
    GridViewColumnHeader _lastHeaderClicked = null;  
    ListSortDirection _lastDirection = ListSortDirection.Ascending;  
  
    void GridViewColumnHeaderClickedHandler(object sender,  
                                            RoutedEventArgs e)  
    {  
        GridViewColumnHeader headerClicked =  
              e.OriginalSource as GridViewColumnHeader;  
        ListSortDirection direction;  
  
        if (headerClicked != null)  
        {  
            if (headerClicked.Role != GridViewColumnHeaderRole.Padding)  
            {  
                if (headerClicked != _lastHeaderClicked)  
                {  
                    direction = ListSortDirection.Ascending;  
                }  
                else  
                {  
                    if (_lastDirection == ListSortDirection.Ascending)  
                    {  
                        direction = ListSortDirection.Descending;  
                    }  
                    else  
                    {  
                        direction = ListSortDirection.Ascending;  
                    }  
                }  
  
                string header = headerClicked.Column.Header as string;  
                Sort(header, direction);  
  
                if (direction == ListSortDirection.Ascending)  
                {  
                    headerClicked.Column.HeaderTemplate =  
                      Resources["HeaderTemplateArrowUp"] as DataTemplate;  
                }  
                else  
                {  
                    headerClicked.Column.HeaderTemplate =  
                      Resources["HeaderTemplateArrowDown"] as DataTemplate;  
                }  
  
                // Remove arrow from previously sorted header  
                if (_lastHeaderClicked != null && _lastHeaderClicked != headerClicked)  
                {  
                    _lastHeaderClicked.Column.HeaderTemplate = null;  
                }  
  
                _lastHeaderClicked = headerClicked;  
                _lastDirection = direction;  
            }  
        }  
    }  
```  
  
```vb  
Partial Public Class Window1  
        Inherits Window  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        Private _lastHeaderClicked As GridViewColumnHeader = Nothing  
        Private _lastDirection As ListSortDirection = ListSortDirection.Ascending  
  
        Private Sub GridViewColumnHeaderClickedHandler(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim headerClicked As GridViewColumnHeader = TryCast(e.OriginalSource, GridViewColumnHeader)  
            Dim direction As ListSortDirection  
  
            If headerClicked IsNot Nothing Then  
                If headerClicked.Role <> GridViewColumnHeaderRole.Padding Then  
                    If headerClicked IsNot _lastHeaderClicked Then  
                        direction = ListSortDirection.Ascending  
                    Else  
                        If _lastDirection = ListSortDirection.Ascending Then  
                            direction = ListSortDirection.Descending  
                        Else  
                            direction = ListSortDirection.Ascending  
                        End If  
                    End If  
  
                    Dim header As String = TryCast(headerClicked.Column.Header, String)  
                    Sort(header, direction)  
  
                    If direction = ListSortDirection.Ascending Then  
                        headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowUp"), DataTemplate)  
                    Else  
                        headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowDown"), DataTemplate)  
                    End If  
  
                    ' Remove arrow from previously sorted header  
                    If _lastHeaderClicked IsNot Nothing AndAlso _lastHeaderClicked IsNot headerClicked Then  
                        _lastHeaderClicked.Column.HeaderTemplate = Nothing  
                    End If  
  
                    _lastHeaderClicked = headerClicked  
                    _lastDirection = direction  
                End If  
            End If  
        End Sub  
```  
  
 O exemplo a seguir mostra o algoritmo de classificação chamado pelo manipulador de eventos para classificar os dados. A classificação é executada, criando um novo <xref:System.ComponentModel.SortDescription> estrutura.  
  
```csharp  
private void Sort(string sortBy, ListSortDirection direction)  
{  
    ICollectionView dataView =  
      CollectionViewSource.GetDefaultView(lv.ItemsSource);  
  
    dataView.SortDescriptions.Clear();  
    SortDescription sd = new SortDescription(sortBy, direction);  
    dataView.SortDescriptions.Add(sd);  
    dataView.Refresh();  
}  
```  
  
```vb  
Private Sub Sort(ByVal sortBy As String, ByVal direction As ListSortDirection)  
            Dim dataView As ICollectionView = CollectionViewSource.GetDefaultView(lv.ItemsSource)  
  
            dataView.SortDescriptions.Clear()  
            Dim sd As New SortDescription(sortBy, direction)  
            dataView.SortDescriptions.Add(sd)  
            dataView.Refresh()  
        End Sub  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
