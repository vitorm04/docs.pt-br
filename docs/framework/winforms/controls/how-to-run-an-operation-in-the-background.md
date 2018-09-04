---
title: Como executar uma operação na tela de fundo
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
ms.openlocfilehash: 94abd36affdccec1d01c030fcff4c6de93ca6c72
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565920"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Como executar uma operação na tela de fundo
Se você tiver uma operação que levará muito tempo para ser concluída, e você não deseja causar atrasos na interface do usuário, você pode usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.  
  
 O exemplo de código a seguir mostra como executar uma operação demorada em segundo plano. O formulário tem **inicie** e **Cancelar** botões. Clique o **iniciar** botão para executar uma operação assíncrona. Clique o **Cancelar** botão para parar uma operação assíncrona em execução. O resultado de cada operação é exibido em um <xref:System.Windows.Forms.MessageBox>.  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  
  
 Consulte também [instruções passo a passo: executando uma operação em segundo plano](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Como implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Componente BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
