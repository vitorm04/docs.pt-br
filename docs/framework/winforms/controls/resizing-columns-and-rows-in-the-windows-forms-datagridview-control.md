---
title: Redimensionando colunas e linhas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: e1fa2d57cfb2cd374d691fe03a0e0bdbd3ad7141
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903182"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>Redimensionando colunas e linhas no controle DataGridView dos Windows Forms
O controle `DataGridView` fornece diversas opções para personalizar o comportamento de dimensionamento de suas colunas e linhas. Normalmente, células `DataGridView` não são redimensionados com base em seu conteúdo. Em vez disso, elas cortam qualquer valor de exibição maior do que a célula. Se o conteúdo puder ser exibido como uma cadeia de caracteres, a célula o exibirá em uma dica de ferramenta.  
  
 Por padrão, os usuários poderão arrastar os divisores de linha, coluna e cabeçalho com o mouse para mostrar mais informações. Os usuários também podem clicar duas vezes em um divisor para redimensionar automaticamente a faixa da linha, coluna ou cabeçalho associado ao conteúdo.  
  
 O controle `DataGridView` fornece propriedades, métodos e eventos que permitem personalizar ou desabilitar todos esses comportamentos causados voltados para o usuário. Além disso, é possível redimensionar linhas, colunas e cabeçalhos com programação para ajustar o conteúdo ou configurá-los para redimensionarem a si próprios automaticamente sempre que seu conteúdo mudar. Você também pode configurar colunas para dividir automaticamente a largura disponível do controle em proporções especificadas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)  
 Descreve as opções para dimensionar linhas, colunas e cabeçalhos. Também fornece detalhes sobre os métodos e propriedades relacionados ao dimensionamento e descreve os cenários comuns de uso.  
  
 [Modo de preenchimento de coluna no controle DataGridView dos Windows Forms](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 Descreve o modo de preenchimento de coluna em detalhes e fornece código de demonstração que pode ser usado para experimentar o modo de preenchimento de coluna e outros modos.  
  
 [Como: Definir os modos de dimensionamento do controle DataGridView dos Windows Forms](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 Descreve como configurar os modos de dimensionamento para fins comuns.  
  
 [Como: Redimensionar de forma programática as células para ajustar o conteúdo no controle DataGridView dos Windows Forms](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 Fornece código de demonstração que pode ser usado para experimentar o redimensionamento com programação.  
  
 [Como: Redimensionar automaticamente células quando o conteúdo é alterado no controle DataGridView dos Windows Forms](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 Fornece código de demonstração que pode ser usado para experimentar os modos de dimensionamento automáticos.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.DataGridView>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.  
  
## <a name="see-also"></a>Consulte também

- [Controle DataGridView](datagridview-control-windows-forms.md)
