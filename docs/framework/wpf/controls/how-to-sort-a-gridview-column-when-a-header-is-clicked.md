---
title: 'Como: Classificar uma coluna GridView quando um cabeçalho é clicado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], GridView
- controls [WPF], ListView
- ListView controls [WPF], sorting GridView columns
- GridView controls [WPF], ListView control
ms.assetid: 4865d720-d147-40ed-83a7-af7587f8aad8
ms.openlocfilehash: b636842b1d41e17b09f02b7b9a6f7aa47eb4cdd1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365406"
---
# <a name="how-to-sort-a-gridview-column-when-a-header-is-clicked"></a>Como: Classificar uma coluna GridView quando um cabeçalho é clicado
Este exemplo mostra como criar uma <xref:System.Windows.Controls.ListView> controle que implementa um <xref:System.Windows.Controls.GridView> exibir modo e classifica os dados de conteúdo quando um usuário clica em um cabeçalho de coluna.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma <xref:System.Windows.Controls.GridView> com três colunas que se associam ao <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, e <xref:System.DateTime.Day%2A>, as propriedades do <xref:System.DateTime> estrutura.  
  
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
  
 Para classificar os dados de acordo com o conteúdo de uma coluna, o exemplo define um manipulador de eventos para manipular o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento que ocorre quando você pressiona o botão de cabeçalho de coluna. O exemplo a seguir mostra como especificar um manipulador de eventos para o <xref:System.Windows.Controls.GridViewColumnHeader> controle.  
  
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
        var headerClicked = e.OriginalSource as GridViewColumnHeader;  
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
  
                var columnBinding = headerClicked.Column.DisplayMemberBinding as Binding;
                var sortBy = columnBinding?.Path.Path ?? headerClicked.Column.Header as string;

                Sort(sortBy, direction);
  
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
        Dim headerClicked = TryCast(e.OriginalSource, GridViewColumnHeader)  
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

                Dim columnBinding = TryCast(headerClicked.Column.DisplayMemberBinding, Binding)
                Dim sortBy = If(columnBinding?.Path.Path, TryCast(headerClicked.Column.Header, String))

                Sort(sortBy, direction)  

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
End Class
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
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Visão geral de ListView](listview-overview.md)
- [Visão geral de GridView](gridview-overview.md)
- [Tópicos de instruções](listview-how-to-topics.md)
