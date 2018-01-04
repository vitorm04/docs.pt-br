---
title: "Como criar um layout dos Windows Forms que responda bem à localização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 072d0694b3e92d9bf4bd8d0cf118b2f4af024af6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Como criar um layout dos Windows Forms que responda bem à localização
Criação de formulários que estão prontos para ser localizados aumenta a velocidade de desenvolvimento para mercados internacionais. Você pode usar o <xref:System.Windows.Forms.TableLayoutPanel> controle para implementar layouts respondem normalmente como redimensionam controles devido a alterações em seus <xref:System.Windows.Forms.Control.Text%2A> valores de propriedade.  
  
## <a name="example"></a>Exemplo  
 Este formulário demonstra como criar um layout que proporcionalmente se ajusta ao converter valores de cadeia de caracteres exibidos em outros idiomas. Esse processo de conversão é chamado *localização*. Para obter mais informações, consulte [localização](../../../../docs/standard/globalization-localization/localization.md).  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  Consulte também [passo a passo: Criando um Layout que ajusta proporção para localização](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [Como alinhar e alongar um controle em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [Como abranger linhas e colunas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
4.  [Como editar colunas e linhas em um controle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
5.  [Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [Como: oferecer suporte à localização no Windows Forms usando AutoSize e o controle TableLayoutPanel](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [Passo a passo: Criando um Windows Form redimensionável para entrada de dados](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Localização](../../../../docs/standard/globalization-localization/localization.md)
