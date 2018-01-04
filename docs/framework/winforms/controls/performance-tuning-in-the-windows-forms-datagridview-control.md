---
title: Ajuste de desempenho no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0171bf4fa056de2dd06c2f7e431ea55a8dab1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Ajuste de desempenho no controle DataGridView dos Windows Forms
Ao trabalhar com grandes quantidades de dados, o controle `DataGridView` pode consumir uma grande quantidade de memória em sobrecarga, a menos que você o utilize com cuidado. Em clientes com memória limitada, é possível evitar um pouco dessa sobrecarga, evitando recursos que têm um custo de memória alto. Você também pode gerenciar alguns ou todas as tarefas de manutenção e recuperação de dados usando o modo virtual para personalizar o uso de memória para seu cenário.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Descreve como usar o controle `DataGridView` de uma maneira que evite penalidades no desempenho e no uso de memória desnecessário ao trabalhar com grandes quantidades de dados.  
  
 [Modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Descreve como usar o modo virtual para suplementar ou substituir o mecanismo de associação de dados padrão.  
  
 [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Descreve como implementar manipuladores para vários eventos no modo virtual. Também demonstra como implementar a reversão de nível de linha e confirmar as edições do usuário.  
  
 [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Descreve como carregar dados sob demanda, que é útil quando você tem mais dados para exibir do que a memória de cliente disponível pode armazenar.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.DataGridView>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Modos de exibição dos dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
