---
title: Classificando dados no controle DataGridView do Windows Forms
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012135"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>Classificando dados no controle DataGridView do Windows Forms

Por padrão, os usuários podem classificar os dados em um <xref:System.Windows.Forms.DataGridView> controle clicando no cabeçalho de uma coluna de caixa de texto (ou pressionando F3 quando uma célula de caixa de texto está focalizada no .NET Framework 4.7.2 e versões posteriores). Você pode modificar a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode> de colunas específicas para permitir aos usuários classificar por outros tipos de coluna quando fizer sentido. Você também pode classificar os dados de forma programática por qualquer coluna ou por várias colunas.

## <a name="in-this-section"></a>Nesta seção

[Modos de classificação da coluna no controle DataGridView dos Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
Descreve as opções para classificar os dados no controle.

[Como: Definir os modos de classificação para colunas no controle DataGridView dos Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
Descreve como habilitar usuários para classificar por colunas que não são classificáveis por padrão.

[Como: Personalizar a classificação no controle DataGridView dos Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
Descreve como classificar dados por meio de programação e como personalizar a classificação usando o <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> evento ou implementando o <xref:System.Collections.IComparer> interface.

## <a name="reference"></a>Referência

<xref:System.Windows.Forms.DataGridView>  
Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.Sort%2A> método.

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> propriedade.

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeração.

## <a name="see-also"></a>Consulte também

- [Controle DataGridView](datagridview-control-windows-forms.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
