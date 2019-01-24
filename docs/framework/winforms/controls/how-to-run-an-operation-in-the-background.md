---
title: 'Como: Executar uma operação em segundo plano'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 99567897c90244c2768dfbcfe36762d1ec54a070
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510631"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Como: Executar uma operação em segundo plano
Se você tiver uma operação que levará muito tempo para ser concluída, e você não deseja causar atrasos na interface do usuário, você pode usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.  
  
 O exemplo de código a seguir mostra como executar uma operação demorada em segundo plano. O formulário tem **inicie** e **Cancelar** botões. Clique o **iniciar** botão para executar uma operação assíncrona. Clique o **Cancelar** botão para parar uma operação assíncrona em execução. O resultado de cada operação é exibido em um <xref:System.Windows.Forms.MessageBox>.  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  
  
 Consulte também [passo a passo: Executando uma operação em segundo plano](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Como: Implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Componente BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
